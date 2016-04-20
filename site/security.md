# Codecov Security

> v1.0.0 - Edit on [GitHub](https://github.com/codecov/support/blob/master/site/security.md)


#### Contents
1. [How does Codecov authenticate access to repository?](#how-does-codecov-authenticate-access-to-a-repository)
1. [How does Codecov store passwords?](#how-does-codecov-store-passwords)
1. [How does Codecov store Tokens?](#how-does-codecov-store-tokens)
1. [Does Codecov store source code?](#does-codecov-store-source-code)
1. [Is my team data isolated from other teams?](#is-my-team-data-isolated-from-other-teams)
1. [How do I add collaborators/members to my private repository?](#how-do-i-add-collaboratorsmembers-to-my-private-repository)
1. [When does Codecov read source code from my repository?](#when-does-codecov-read-source-code-from-my-repository)
1. [Does Codecov ever clone the repository?](#does-codecov-ever-clone-the-repository)
1. [When does Codecov write to my repository?](#when-does-codecov-write-to-my-repository)
1. [How long are uploaded reports archived for?](#how-long-are-uploaded-reports-archived-for)
1. [Are logs kept on who access what data on Codecov?](#are-logs-kept-on-who-access-what-data-on-codecov)
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
- **User** a single person whom has logged-in to Codecov via Service therefore having an active user session
- **Guest** a http request from performed without an active user sessions
- **Bot** the User whom was choosen to consume Service endpoints during Worker jobs
- **Worker** Codecov async backend which handles uploading, report processing and other tasks
- **Web** Codecov front-end service that handles page builds and all HTTP requests (GET, POST, etc.)
- **Extension** the Codecov Browser Extension
- **Token** a Users oAuth token/secret granted by Service upon logging-in to Codecov
- **Scope** what level of permission a Users has on a Repository in Service, provided by Services
- **CI** continuous integration provider. Including (not limited to) Travis-CI, Circle CI, Jenkins, etc
- **API** HTTP requests to Service
- **3rd Party** a SaaS tool that Codecov uses. *Example* [Sentry](https://getsentry.com) and [Logentries](https://logentries.com)

-----

## How does Codecov authenticate access to a repository?
- **Public** Repos are visible to all Users and Guests
- **Private** Repos are visible to Users whom have at least `read` according to Service
- Codecov checks the Users Scope by making an API request using the User's Token
- If the User **does not** have at least `read` access to the Repo: Codecov will return a 404 HTTP Error
- Codecov **always** uses the acting User's Token to make API requests to Service *when navigating Codecov*
- Codecov **always** uses the Bot's Token in when preforming Worker tasks

## How does Codecov store passwords?
- Codecov **does not** use passwords in the product.
- Codecov does not, **ever**, ask for any "passwords".
- Codecov stores Tokens for Users upon logging-in.

## How does Codecov store Tokens?
- Codecov received Tokens when a User logs into Codecov.
- Tokens are **encrypted** by [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard).
  The key used to encrypt Tokens is broken into three chunks stored in different locations
  in the Stack to reduce a single point of failure. In order to comprise Tokens an attacker
  must breach multiple levels of the Codecov Stack (database, source code, server environment, and more)
- Only Codecov Staff has access to User Tokens
- Tokens are aggressively removed from any logs and tracebacks, never sent to 3rd Party solutions

## Does Codecov store source code?

> TLDR; We do not store source code.
> Some archived raw uploads may contain source code, which you can elect to disable.

There is only one opportunity where source code could be stored: during report uploading.
Some languages, C++ for example, produce reports that include source code in the report data.
Codecov scrubs some source code out (and we plan to support this effort more) but may not find it all.
These uploads, by default, are archived for 1 month. You may elect to disable this feature
which will prevent all uploads from archiving.

##### How to disable archiving
In you `codecov.yml` set the following value to `false`:

```
codecov:
  archive:
    uploads: false
```

## How does Codecov archive reports?
Codecov archives both the pre-processed reports (preventing vendor-lockin and to verify report accuracy)
and the post-processed reports (which never contain source code) in AWS S3.
Archives are **accessible publicly** to Users whom have access to the encrypted location of the content.
The location is kept secret in a way that is nearly impossible to find by an unauthorized users.
Below is an example path of such an archive, note how there are several unique variables
needing to be known in order to discover the location of the archive.

```
in)  /v4/raw/<yyyy-mm-dd>/<unique-repo-hash>/<commitid>/<uuid>.txt
out) /v4/raw/2016-01-01/4434BC2A2EC4FCA57F77B473D83F928C/9ac8f27fb300b8ab415b31ec19d2d29eb153bfce/869a4b41-882f-474b-8763-e673444cab25.txt
```

## Is my team data isolated from other teams?
No, Teams/Repos/Users data is stored in one or more databases, all properly of Codecov, but not
isolated from other Teams/Repos/Users utilizing Codecov services.

## How do I add collaborators/members to my private repository?
- A User's access is always verified with Service.
- If using GitHub: once a User logs in they must grant Codecov Private Repository Access
  in order to interact with Private repositories hosted on GitHub that they have
  appropriate access to.

This allows us to have 100% transparency on whom can access source code and view reports on Codecov.

## What Scope is used when signing-up using GitHub?
Codecov first asks for `user:email, read:org, repo:status, write:repo_hook` Scope, **note**
this is for **Public Repos only**. Once a User is logged-in they may elect to grant
Codecov extended privileged which enable the User to interact with **Private Repos**.

> Read more on [GitHub Scopes here](https://developer.github.com/v3/oauth/#scopes)

## Can I restrict which Teams Codecov has access to?
No. This is currently a limitation to GitHub (and all other Services).
This feature would have to be implemented by the Service and not in Codecov.

## Does Codecov ever clone the repository?
No, never. Codecov uses API requests to retrieve information necessary to perform it job and never stores source code in the result of an API request.

## When does Codecov read source code from my repository?
- When a User requests to view source code by a Web request.
- During several Worker tasks in order to perform analysis of the uploaded reports.

> Source code is never stored in the processes mentioned above.

## When does Codecov write to my repository?
The only times Codecov will "write" to your repository is in the following processes:
1. Create/Update a Webhook
2. Create/Update/Delete a Pull Request Comment
3. Create/Update the Commit Status

> Codecov never adjusts source code, delete branches, close pull requests or perform any other write action.

## How long are uploaded reports archived for?
- By default pre-processed reports are archived in AWS-S3 for **1 month**. This feature may be disabled.
- Codecov archives post-processed report in AWS-S3 indefinitely.


## Are logs kept on who access what data on Codecov?
Yes. Each and every Web request is logged up-to or more then one year.
Logs are accessible by Codecov Staff and are used to analyze User behavior and help debug the product.


## Who can adjust the Team configuration?
The User can adjust team configuration if:

a. a Codecov Team Admin, **OR**
b. adjust their own account, **OR**
c. the first User to create a billing account for the Team, **OR**
d. have `admin` status according to Service

- The **first User** to setup billing for a Team will be added as the first Codecov Team Admin
- **Note** if you want "transfer administration" to another User please (1) add the new User, (b) remove the old user in your Team account page.


## Who can adjust billing/plans information?
The User can adjust billing and plans details if:

a. a Codecov Team Admin, **OR**
b. adjust their own account, **OR**
c. the first User to create a billing account for the Team, **OR**
d. have `admin` status according to Service


- Please contact Codecov Staff if there are any discrepancies or issues will billing.
- **Note** if you want "transfer administration" to another User please (1) add the new User, (b) remove the old user in your Team account page.


## How do I change the configuration on the repository?
Most Repo configuration is recorded in a file called `codecov.yml` within the Repo.
The location of this configuration file may be anywhere within the Repo and must be named `codecov.yml` or `.codecov.yml` in order to be detected.
Having configuration stored in the `codecov.yml` allows for complete transparency and version controlled configuration.
For more details please visit http://localhost:8888/docs#configuration
