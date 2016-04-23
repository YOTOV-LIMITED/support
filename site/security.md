# Codecov Security

> v1.0.0 - Edit on [GitHub](https://github.com/codecov/support/blob/master/site/security.md)


#### Contents
1. [How does Codecov authenticate access to repository?](#how-does-codecov-authenticate-access-to-a-repository)
1. [How does Codecov store passwords?](#how-does-codecov-store-passwords)
1. [How does Codecov store Tokens?](#how-does-codecov-store-tokens)
1. [Does Codecov store source code?](#does-codecov-store-source-code)
1. [Is my Team data isolated from other Teams?](#is-my-team-data-isolated-from-other-teams)
1. [How do I add collaborators/members to my private repository?](#how-do-i-add-collaboratorsmembers-to-my-private-repository)
1. [When does Codecov read source code from my repository?](#when-does-codecov-read-source-code-from-my-repository)
1. [Does Codecov ever clone the repository?](#does-codecov-ever-clone-the-repository)
1. [When does Codecov write to my repository?](#when-does-codecov-write-to-my-repository)
1. [How long are uploaded reports archived for?](#how-long-are-uploaded-reports-archived-for)
1. [Are logs kept on who accesses what data on Codecov?](#are-logs-kept-on-who-access-what-data-on-codecov)
1. [How do I change the configuration on the repository?](#how-do-i-change-the-configuration-on-the-repository)
1. [How does Codecov archive reports?](#how-does-codecov-archive-reports)
1. [Who can adjust the Team configuration?](#who-can-adjust-the-team-configuration)
1. [Who can adjust billing/plans information?](#who-can-adjust-billingplans-information)
1. [What Scope is used when signing-up using GitHub?](#what-scope-is-used-when-signing-up-using-github)
1. [Can I restrict which Teams Codecov has access to?](#can-i-restrict-which-teams-codecov-has-access-to)

#### Terms
- **Codecov** Codecov and its technology/product/services
- **Service** one of the following companies: GitHub, Bitbucket or GitLab
- **Team** a team or organization in Service
- **Repo** a Service (public or private) repository
- **User** a single person who has logged into Codecov via Service therefore has an active user session
- **Guest** a http request performed without an active user sessions
- **Worker** Codecov's sync back-end which handles uploading, report processing, and other tasks
- **Bot** the User who was chosen to consume Service endpoints during Worker jobs !!!should define Worker before using term here !!!!!
- **Web** Codecov front-end service that handles page builds and all HTTP requests (GET, POST, etc.)
- **Extension** the Codecov Browser Extension
- **Token** a Users auth token/secret granted by Service upon logging-in to Codecov
- **Scope** what level of permission a User has on a Repository in Service, provided by Services
- **CI** continuous integration provider. Including (not limited to) Travis-CI, Circle CI, Jenkins, etc.
- **API** HTTP requests to Service
- **3rd Party** a SaaS tool used by Codecov. *Example* [Sentry](https://getsentry.com) and [Logentries](https://logentries.com)

-----

## How does Codecov authenticate access to a repository?
- **Public** Repos are visible to all Users and Guests
- **Private** Repos are visible to Users who have at least `read` access according to Service
- Codecov checks the User's Scope by making an API request with the User's Token
- If the User **does not** have at least `read` access to the Repo: Codecov will return a 404 HTTP Error
- Codecov **always** uses the acting User's Token to make API requests to Service *when navigating Codecov*
- Codecov **always** uses the Bot's Token in when preforming Worker tasks

## How does Codecov store passwords?
- Codecov **does not** use passwords in the product.
- Codecov does not, **ever**, ask for any "passwords".
- Codecov stores Tokens for Users upon logging-in.

## How does Codecov store Tokens?
- Codecov receives Tokens when a User logs into Codecov.
- Tokens are **encrypted** by [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard).
  The key used to encrypt Tokens is broken into three chunks stored in different locations
  in the Stack to reduce a single point of failure. In order to compromise Tokens an attacker
  must breach multiple levels of the Codecov Stack (database, source code, server environment, and more)
- Only Codecov staff has access to User Tokens
- Tokens are aggressively removed from any logs and tracebacks and are never sent to 3rd Party solutions

## Does Codecov store source code?

> TLDR; We do not store source code.
> Some archived raw uploads may contain source code, which you can elect to disable.

There is only one opportunity for source code to be stored: while uploading reports.
Some languages, C++ for example, produce reports that include source code in the report data.
Codecov scrubs some source code out (and we plan to support this effort more) but may not find it all.
These uploads, by default, are archived for 1 month. You may elect to prevent all uploads from archiving
by disabling this feature.

##### How to disable archiving
In your `codecov.yml` set the following value to `false`:

```
codecov:
  archive:
    uploads: false
```

## How does Codecov archive reports?
Codecov archives both the pre-processed reports (preventing vendor-lockin and to verifying report accuracy)
and the post-processed reports (which never contain source code) in AWS S3.
Archives are **accessible publicly** to Users who have access to the encrypted location of the content.
The location is kept secret in a way that is nearly impossible to find by an unauthorized users.
Below is an example path of such an archive, note how there are several unique variables
that must be known in order to discover the location of the archive.

```
in)  /v4/raw/<yyyy-mm-dd>/<unique-repo-hash>/<commitid>/<uuid>.txt
out) /v4/raw/2016-01-01/4434BC2A2EC4FCA57F77B473D83F928C/9ac8f27fb300b8ab415b31ec19d2d29eb153bfce/869a4b41-882f-474b-8763-e673444cab25.txt
```

## Is my Team's data isolated from other Teams?
No, Teams/Repos/Users data is stored in one or more databases, all properly of Codecov, but not
isolated from other Teams/Repos/Users utilizing Codecov services.

## How do I add collaborators/members to my private repository?
- A User's access is always verified with Service.
- If using GitHub: once a User logs in they must grant Codecov Private Repository Access
  in order to interact with Private repositories hosted on GitHub that User has
  appropriate access to.

This allows us to have 100% transparency on who can access source code and view reports on Codecov.

## What Scope is used when signing-up using GitHub?
Codecov first asks for `user:email, read:org, repo:status, write:repo_hook` Scope, **note**
this is for **Public Repos only**. Once a User is logged-in they may elect to grant
Codecov extended privileges which enable the User to interact with **Private Repos**.

> Read more on [GitHub Scopes here](https://developer.github.com/v3/oauth/#scopes)

## Can I restrict which Teams Codecov has access to?
No. This is currently a limitation to GitHub (and all other Services).
This feature would have to be implemented by the Service; not by Codecov.

## Does Codecov ever clone the repository?
No, never. Codecov uses API requests to retrieve information necessary to perform its job and never stores source code in the result of an API request.

## When does Codecov read source code from my repository?
- When a User requests to view source code by a Web request.
- Or, during several Worker tasks in order to perform analysis of the uploaded reports.

> Source code is never stored in the processes mentioned above.

## When does Codecov write to my repository?
The only times Codecov will "write" to your repository is in the following processes:
1. Create/Update a Webhook
2. Create/Update/Delete a Pull Request Comment
3. Create/Update the Commit Status

> Codecov never adjusts source code, deletes branches, closes pull requests, or performs any other 'write' action.

## How long are uploaded reports archived?
- By default, pre-processed reports are archived in AWS-S3 for **1 month**. This feature may be disabled.
- Codecov archives post-processed reports in AWS-S3 indefinitely.


## Are logs kept on who accesses what data on Codecov?
Yes. Each and every Web request is logged for up to one year. !!!! Saying both "up to" and "or more than" makes no sense. Which is it? Also note, if you use "more than", make sure you say "than" instead of "then" !!!!
Logs are accessible by Codecov staff and are used to analyze User behavior and help debug the product. !!! if you want to capitalize "Staff", include it in the terms" !!!!!


## Who can adjust the Team configuration?
The following can adjust team configuration:

a. the User, if the account is their own, **OR**
b. a Codecov Team Admin, **OR**
c. the first User to create a billing account for the Team, **OR**
d. a User with `admin` status according to Service


- By default, the **first User** to setup billing for a Team will be added as the first Codecov Team Admin
- **Note** if you want to transfer administration to another User please (1) add the new User, (b) remove the old user in your Team account page.


## Who can adjust billing/plans information?
THe following can adjust billing/plans information:

a. the User, if the account is their own, **OR**
b. a Codecov Team Admin, **OR**
c. the first User to create a billing account for the Team, **OR**
d. a User with `admin` status according to Service


- Please contact Codecov staff if there are any discrepancies or issues with billing.
- **Note** if you want to transfer administration to another User please (1) add the new User, (b) remove the old user in your Team account page.


## How do I change the configuration on the repository?
Most Repo configuration is recorded in a file called `codecov.yml` within the Repo.
The location of this configuration file may be anywhere within the Repo and must be named `codecov.yml` or `.codecov.yml` in order to be detected.
Having configuration stored in the `codecov.yml` allows for complete transparency and version controlled configuration.
For more details please visit http://localhost:8888/docs#configuration
