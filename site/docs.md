<div class="ui container">
  <div class="ui divided stackable grid">
    <div class="column three wide spacing">
      <div class="ui sticky spacing">
        <div class="ui link list">
          <a href="#overview" class="item">Overview</a>
          <a href="/support" class="item">Support</a>
          <a href="/enterprise" class="item">Enterprise</a>
        </div>
        <h3>Learn</h3>
        <div class="ui link list">
          <a href="#languages" class="item">Languages</a>
          <a href="#multilingual" class="item">Multilingual</a>
          <a href="#collaboration" class="item">Collaboration</a>
          <a href="#configuration" class="item">Configuration</a>
          <a href="#yaml_default_branch" class="item">Default Branch</a>
          <a href="#yaml_default_commit_status" class="item">Default Commit Statuses</a>
          <a href="#flags" class="item">Coverage Flags</a>
          <a href="#fixing_paths" class="item">Fixing Paths</a>
          <a href="#api" class="item">API</a>
        </div>
        <h3>Caveats</h3>
        <div class="ui link list">
          <a href="#github-scope-policy" class="item">GitHub Scope Policy</a>
          <a href="#bitbucket-compare" class="item">Bitbucket Compare</a>
        </div>
        <h3>Meta</h3>
        <div class="ui link list">
          <a href="https://github.com/codecov" class="item">Contribute</a>
          <!-- <a href="/branding" class="item">Branding and Logos</a> -->
          <a href="/pricing" class="item">Pricing</a>
          <a href="http://shop.codecov.io" class="item">Shop</a>
          <a href="http://shop.codecov.io/blog" class="item">Blog</a>
        </div>
        <h3>Site</h3>
        <div class="ui link list">
          <a href="/site/changelog" class="item">Changes</a>
          <a href="/site/privacy" class="item">Privacy Policy</a>
          <a href="/site/terms" class="item">Terms of Use</a>
          <a href="/site/security" class="item">Security</a>
        </div>
        <p class="text-center">
          <a href="https://github.com/codecov/support/site/docs.md" class="ui mini label">Edit in Github</a>
        </p>
      </div>
    </div>
    <div class="column eleven wide spacing">
      <div>
        <h1 id="overview"><a href="#overview" class="anchor">&infin;</a> Overview</h1>
        <p>
          Thank you for choosing Codecov.
          We work hard to provide a powerful solution to help your team analyze coverage reports.
        </p>
        <p>
          Codecov gathers the coverage reports, from all languages, and aggregate the results in a single cohesive report.
          Then we dig deeping into the reports by comparing history to discover issues and changes
          reporting this information back the developer to ensure code quality.
        </p>
        <p>
          We do this all with high integration into your workflow.
          The Codecov Browser Extention brings the coverage reports directly into GitHub for a
          seamless workflow enhancement. Coupled with our amazing pull request comment and
          three powerful commit statuses your product will be well covered.
        </p>
      </div>
      <div class="ui more spacing divider"></div>
      <div>
        <h1 id="languages"><a href="#languages" class="anchor">&infin;</a> Languages</h1>
        <p>
          Codecov supports all major languages and continues to add new languages with community support. Thank you!
          We also support <b>multiple languages in a single repository</b> <a href="#multilingual">learn more here</a>.
        </p>
        <p>Click on your language to view a full repository example and documentation specifics.</p>
        <div class="ui horizontal bulleted list">
          <!-- [languages] -->
          <a class="item" href="https://github.com/codecov/example-bash">Bash</a>
          <a class="item" href="https://github.com/codecov/example-c">C</a>
          <a class="item" href="https://github.com/codecov/example-clojure">Clojure</a>
          <a class="item" href="https://github.com/codecov/example-d">D</a>
          <a class="item" href="https://github.com/codecov/example-dart">Dart</a>
          <a class="item" href="https://github.com/codecov/example-fortran">Fortran</a>
          <a class="item" href="https://github.com/codecov/example-go">Go</a>
          <a class="item" href="https://github.com/codecov/example-groovy">Groovy</a>
          <a class="item" href="https://github.com/codecov/example-java">Java</a>
          <a class="item" href="https://github.com/codecov/example-android">Android (Java)</a>
          <a class="item" href="https://github.com/codecov/example-javascript">ES6</a>
          <a class="item" href="https://github.com/codecov/example-javascript">Javascript</a>
          <a class="item" href="https://github.com/codecov/example-kotlin">Kotlin</a>
          <a class="item" href="https://github.com/codecov/example-node">NodeJS</a>
          <a class="item" href="https://github.com/codecov/example-objc">Objective-C</a>
          <a class="item" href="https://github.com/codecov/example-perl">Perl</a>
          <a class="item" href="https://github.com/codecov/example-php">PHP</a>
          <a class="item" href="https://github.com/codecov/example-python">Python</a>
          <a class="item" href="https://github.com/codecov/example-r">R</a>
          <a class="item" href="https://github.com/codecov/example-ruby">Ruby</a>
          <a class="item" href="https://github.com/codecov/example-scala">Scala</a>
          <a class="item" href="https://github.com/codecov/example-swift">Swift</a>
          <a class="item" href="https://github.com/codecov/example-xtend">XTend</a>
        </div>
        <div class="ui message">Don't see your language? We can add it with your help. <a href="/support">Please contact us.</a></div>
      </div>
      <div class="ui more spacing divider"></div>
      <div>
        <h1 id="multilingual"><a href="#multilingual" class="anchor">&infin;</a> Multilingual</h1>
        <p>
          Codecov supports multiple langauges in the same repository.
          You may upload reports for one or more languages and Codecov will merge the reports automatically
          while maintaining the original upload context.
        </p>
        <p>
          <i>How?</i> Codecov does not "override" report data for multiple uploads. We always merge the data.
          Simply upload all three reports at once <b>or</b> seperately.
        </p>
        <h5>Single upload example</h5>
        <pre class="data src"><span class="o">$</span> coverage run tests/
<span class="o">$</span> istanbul cover ./node_modules/mocha/bin/_mocha
<span class="o">$</span> bash &lt;(curl -s https://codecov.io/bash)</pre>
        <p><small>Codecov found and uploaded <code>python::coverage.xml</code> and <code>javascript::coverage.json</code></small></p>
        <h5>Multiple upload example</h5>
        <pre class="data src"><span class="c"># container 1</span>
<span class="o">$</span> coverage run tests/
<span class="o">$</span> bash &lt;(curl -s https://codecov.io/bash)</pre>
        <p><small>Codecov found and uploaded <code>python::coverage.xml</code></small></p>
        <pre class="data src"><span class="c"># container 2</span>
<span class="o">$</span> istanbul cover ./node_modules/mocha/bin/_mocha
<span class="o">$</span> bash &lt;(curl -s https://codecov.io/bash)</pre>
        <p><small>Codecov found and uploaded <code>javascript::coverage.json</code></small></p>

        <p>In both examples above your repository will show reports from Javascript and Python, together.</p>

      </div>
      <div class="ui more spacing divider"></div>
      <div>
        <h1 id="collaboration"><a href="#collaboration" class="anchor">&infin;</a> Collaboration</h1>
        <p>
          No setup necessary. Codecov uses GitHub/Bitbucket/GitLab API's to authorize users.
        </p>
        <div class="ui info message">
          When using <strong>GitHub</strong> please make sure your team members give Codecov private
          repository access in order to view and interact with private repositories on Codeocov.
          Please review our <a href="#github-scope-policy">Github Scope Policy here</a>.
        </div>
      <div>
      <div class="ui more spacing divider"></div>
      <div>
        <h1 id="configuration"><a href="#configuration" class="anchor">&infin;</a> Configuration</h1>
        <p>Codecov searches for a <code>codecov.yml</code> within your repo to customize the product's behavior.</p>
        <p>
          The <code>codecov.yml</code> is a file within your repository that
          configures Codecov to operate in a flexible and customized fashion.
        </p>

        <h3 id="yaml-file-location"><a href="#yaml-file-location" class="anchor">&infin;</a> File Location</h3>
        <p>
          The default location for your yaml file is in the root directory of your repository: <code>./codecov.yml</code>.
          You may place the file inside any sub directory within your project and Codecov will discover the file automatically.
          The file must be named <code>codecov.yml</code> or <code>.codecov.yml</code> in order to be discovered.
        </p>

        <h3 id="yaml-inheritance"><a href="#yaml-inheritance" class="anchor">&infin;</a> Inheritance</h3>
        <p>Repository configuration inherits and overrides the content found in the Team's `codecov.yml` and the default configuration provided by Codecov.</p>
        <div class="ui small steps">
          <div class="step">
            <div class="content">
              <div class="title">Defaults</div>
              <div class="description">
                <a href="https://github.com/codecov/support/src/master/codecov.yml">Review here</a>
              </div>
            </div>
          </div>
          <div class="step">
            <div class="content">
              <div class="title">Team Yaml</div>
              <div class="description">Customized configuration for the entire team</div>
            </div>
          </div>
          <div class="step">
            <div class="content">
              <div class="title">Repository Yaml</div>
              <div class="description">Repository's <code>codecov.yml</code></div>
            </div>
          </div>
        </div>

        <h3 id="yaml-validation"><a href="#yaml-validation" class="anchor">&infin;</a> Validation</h3>
        <p>
          The structure of <code>codecov.yml</code> is strict and parsing will raise errors if extra data or invalid values are provided.
          Codecov will warn the commit author of issues in the yaml file.
        </p>
        <div class="ui info message">
          <b>Best practice</b> validate the yaml file by posting the content to Codecov
          <pre class="data">curl -X POST -d @codecov.yml https://codecov.io/validate <a href="#" class="float-right" data-clipboard-text="curl -X POST -d @codecov.yml https://codecov.io/validate">Copy</a></pre>
        </div>

        <h3 id="yaml-structure"><a href="#yaml-structure" class="anchor">&infin;</a>Structure</h3>
        <div class="ui info message">Interactive documentation can be found on your repository setting page.</div>
        <!-- <script src="https://gist.github.com/stevepeak/53bee7b2c326b24a9b4a.js"></script> -->
      </div>
      <div class="ui more spacing divider"></div>
      <div>
        <h1 id="api"><a href="#api" class="anchor">&infin;</a> API</h1>
        <p>
          Codecov implements a simple approach to API's.
        </p>
        <p>
          By simply adding <code>api/</code> to any page on Codecov will expose the <code>json</code> API output.
        </p>
        <pre class="data src">curl https://codecov.io/<b>api/</b>gh/codecov/example-python</pre>

        <h2 id="api-pagination"><a href="#api-endpoints" class="anchor">&infin;</a> Pagination</h2>
        <p>
          Endpoints that query multiple results have pagination implemented.
          You can specify what page and limit in the url query.
        </p>
        <p>Specify a page number <code>?page=:int</code></p>
        <p>Specify number of results in page <code>?limit=:int</code></p>

        <h2 id="api-authorization"><a href="#api-authorization" class="anchor">&infin;</a> Authorization</h2>
        <p>
          Provide a API access token to retrieve content related to your account.
        </p>
        <p>
          You can generate API tokens in your account page.
          Proceed to <code>/account/:service/:owner/access</code> to manage API access tokens.
        </p>
        <p>
          <b>Option A</b> Provide in the http query via <code>?access_token=:token</code>
        </p>
        <p>
          <b>Option B</b> Provide in the http headers via <code>Authorization: token :token</code>
        </p>


        <h2 id="api-rate-limit"><a href="#api-rate-limit" class="anchor">&infin;</a> Rate Limit</h2>
        <p>We currently do not rate-limit API requests, but may implement a system in the future.</p>
        <!--
        <p>
          If your account is rate-limited, Codecov will return a <code>HTTP 403 Rate Limited</code> status.
          The following HTTP headers will be included on all API requests.
        </p>
        <pre class="data">X-RateLimit-Remaining: 823
X-RateLimit-Limit: 1000
X-RateLimit-Reset: 1460321144</pre>
        -->

        <h2 id="api-endpoints"><a href="#api-endpoints" class="anchor">&infin;</a> Endpoints</h2>
        <div class="ui link list">
          <a class="item" href="#api-teams">Teams</a>
          <a class="item" href="#api-team">Team</a>
          <a class="item" href="#api-repository">Repository</a>
          <a class="item" href="#api-commits">Commits</a>
          <a class="item" href="#api-commit">Commit</a>
          <a class="item" href="#api-branches">Branches</a>
          <a class="item" href="#api-branch">Branch</a>
          <a class="item" href="#api-pulls">Pulls</a>
          <a class="item" href="#api-pull">Pull</a>
          <a class="item" href="#api-compare">Compare</a>
        </div>

        <h3 id="api-teams"><a href="#api-teams" class="anchor">&infin;</a> Teams</h3>
        <p>List all the teams of which you are a member.</p>
        <pre class="data">GET /api/:service</pre>

        <h3 id="api-team"><a href="#api-team" class="anchor">&infin;</a> Repositories</h3>
        <p>List repositories and team statistics.</p>
        <pre class="data">GET /api/:service/:owner</pre>

        <h3 id="api-repository"><a href="#api-repository" class="anchor">&infin;</a> Repository</h3>
        <p>Get repository details and latest commit on default branch.</p>
        <pre class="data">GET /api/:service/:owner/:repo</pre>

        <h3 id="api-commits"><a href="#api-commits" class="anchor">&infin;</a> Commits</h3>
        <p>List commits on all branches and pulls.</p>
        <pre class="data">GET /api/:service/:owner/:repo/commits</pre>

        <h3 id="api-commit"><a href="#api-commit" class="anchor">&infin;</a> Commit</h3>
        <p>Get a single commit and all coverage details.</p>
        <pre class="data">GET /api/:service/:owner/:repo/commit/:sha</pre>

        <h3 id="api-branches"><a href="#api-branches" class="anchor">&infin;</a> Branches</h3>
        <p>List branches on a repository.</p>
        <pre class="data">GET /api/:service/:owner/:repo/branches</pre>

        <h3 id="api-branch"><a href="#api-branch" class="anchor">&infin;</a> Branch</h3>
        <p>Get the head commit on a branch.</p>
        <pre class="data">GET /api/:service/:owner/:repo/branch/:name</pre>

        <h3 id="api-pulls"><a href="#api-pulls" class="anchor">&infin;</a> Pulls</h3>
        <p>Get commits on a pull request.</p>
        <pre class="data">GET /api/:service/:owner/:repo/pulls</pre>

        <h3 id="api-pull"><a href="#api-pull" class="anchor">&infin;</a> Pull</h3>
        <p>Get a single pull request.</p>
        <pre class="data">GET /api/:service/:owner/:repo/pulls/:pullid</pre>

        <h3 id="api-compare"><a href="#api-compare" class="anchor">&infin;</a> Compare</h3>
        <p>List commits and coverage details between two references.</p>
        <pre class="data">GET /api/:service/:owner/:repo/compare/:base...:head</pre>

      </div>
      <div class="ui more spacing divider"></div>
      <div>
        <h1 id="yaml_default_branch"><a href="#yaml_default_branch" class="anchor">&infin;</a> Default Branch</h1>
        <p>You can specify a custom default branch that is only used in the UI for navigation.</p>
        <p>Change your default branch in your <code>codecov.yml</code></p>
        <pre class="data"><span class="kc">codecov:</span>
  <span class="kc">branch:</span> <strong>develop</strong></pre>

      </div>
      <div class="ui more spacing divider"></div>
      <div>
        <h1 id="yaml_default_commit_status"><a href="#yaml_default_commit_status" class="anchor">&infin;</a> Default Commit Status</h1>
        <p>
          Codecov will enable three unique commit statuses by default (as seen below).
          You can disable, change, or create statuses at your own discretion.
        </p>
        <pre><span class="kc">coverage:</span>
  <span class="kc">status:</span>
    <span class="kc">project:</span>
      <span class="kc">default:</span>  <span class="o"># status context</span>
        <span class="kc">target:</span> <span class="s">auto</span>
        <span class="kc">threshold:</span> <span class="o">null</span>
    <span class="kc">patch:</span>
      <span class="kc">default:</span>
        <span class="kc">target:</span> <span class="s">auto</span>
        <span class="kc">threshold:</span> <span class="o">null</span>
    <span class="kc">changes:</span>
      <span class="kc">default:</span>
        <span class="kc">target:</span> <span class="s">auto</span></pre>
        <p>
          This setup will produce the following statuses
          <ul>
            <li><code>codecov/project</code>,</li>
            <li><code>codecov/patch</code>,</li>
            <li><code>codecov/changes</code></li>
          </ul>
        </p>
        <p>
          You can adjust the <code>default</code> statuses or create your own.
          You'll apply a custom context label when you create your own.
        </p>
        <pre><span class="kc">coverage:</span>
  <span class="kc">status:</span>
    <span class="kc">project:</span>
      <span class="kc">default:</span> <span class="o">false</span>
      <span class="kc">unit:</span>
        <span class="kc">threshold:</span> <span class="s">"1.25%"</span>
        <span class="kc">flags:</span>
          <span class="s">- unittests</span>
      <span class="kc">handlers:</span>
        <span class="kc">paths:</span>
          <span class="s">- "app/handlers"</span></pre>
        <p>
          Codecov will then post the following statuses:
          <ul>
            <li><code>codecov/project/unit</code> concerning only unittests metrics,</li>
            <li><code>codecov/project/handlers</code> concerning only coverage data found in the directory <code>app/handlers</code></li>
          </ul>
        </p>
      </div>
      <div class="ui more spacing divider"></div>
      <div>
        <h1 id="flags"><a href="#flags" class="anchor">&infin;</a> Flags</h1>
        <p>
          Flags are used to group coverage data for advanced tracking. Below are some common
          practices implementing flags.
        </p>

        <h3 id="flags-scope"><a href="#flags-scope" class="anchor">&infin;</a> Test Scopes</h3>
        <p><code>unittests</code>, <code>integration</code>, <code>regression</code>, <code>api</code> etc.</p>
        <p>Customers who group tests in categories above should append the desired flag during uploading.<p>
        <pre class="data src"><span class="o">$</span> coverage run tests/unittests
<span class="o">$</span> bash &lt;(curl -s https://codecov.io/bash) <b>-F unittests</b>
<span class="o">$</span> coverage run tests/integration
<span class="o">$</span> bash &lt;(curl -s https://codecov.io/bash) <b>-F integration</b></pre>
        <p>
          In Codecov you can now view coverage data specific to <code>unittests</code> or <code>integration</code> flags.
          This is a step closer to understanding which test group hit which lines.
        </p>
        <p>
          In your <code>codecov.yml</code> you can now create custom notifications or statuses based entirely on one or more flags.
          <pre class="data src"><span class="kc">coverage:</span>
  <span class="kc">status:</span>
    <span class="kc">project:</span>
      <span class="kc">a_custom_title:</span>
        <span class="kc">target:</span> <span class="s">95%</span>
        <span class="kc">threshold:</span> <span class="s">1.25%</span>
        <span class="kc">flag:</span> <span class="s">unittests</span></pre>
        </p>
        <p>Codecov will post a status specifically for <code>unittests</code> with the context <code>codecov/project/a_custom_title</code>.</p>

        <h3 id="flags-group"><a href="#flags-group" class="anchor">&infin;</a> Grouping Projects</h3>
        <p></p>
        <p>
          In your <code>codecov.yml</code> you can now create custom notifications or statuses based entirely on one or more flags.
          <pre class="data src"><span class="kc">coverage:</span>
  <span class="kc">notify:</span>
    <span class="kc">slack:</span>
      <span class="kc">uix:</span>  <span class="c"># custom title</span>
        <span class="kc">url:</span> <span class="s">https://...</span>
        <span class="kc">flags:</span>
          <span class="s">- frontend</span>
          <span class="s">- unittests</span>  <span class="c"># as seen in example above</span>
  <span class="kc">flags:</span>
    <span class="kc">frontend:</span>  <span class="c"># custom title</span>
      <span class="kc">paths:</span>
        <span class="s">- src/js</span>
    <span class="kc">backend:</span>
      <span class="kc">paths:</span>
        <span class="s">- web/</span></pre>
        </p>
        <p>Codecov will submit a notification to your Slack channel with metrics concerning <code>frontend</code> <code>unittests</code> only.</p>

      </div>
      <div class="ui more spacing divider"></div>
      <div>
        <h1 id="fixing_paths"><a href="#fixing_paths" class="anchor">&infin;</a> Fixing Paths</h1>
        <p>
          Coverage reports often do not have accurate relative paths to your repository files.
          Codecov will attempt to fix these paths, and is typically successful at doing so.
          However, some projects have complex path names and Codecov is unable to fix the path properly.
        </p>
        <p>
          To fix these paths you'll need to provide Codecov with a map of where to affix the paths.
        </p>
        <pre class="data src"><span class="kc">coverage:</span>
  <span class="kc">fixes:</span>
    <span class="s">- ::add/this/</span>  <span class="c"># before=file.js after=add/this/file.js</span>
    <span class="s">- remove/this/::</span>  <span class="c"># before=remove/this/file.js after=file.js</span>
    <span class="s">- move/this/::to/that</span>  <span class="c"># before=move/this/file.js after=to/that/file.js</span></pre>
      </div>
      <div class="ui more spacing divider"></div>
      <div>
        <h1 id="github-scope-policy"><a href="#github-scope-policy" class="anchor">&infin;</a> GitHub Scope Policy</h1>
        <p>
          Codecov will first ask for <code>user:email, read:org, repo:status, write:repo_hook</code> scope
          which is only grants access to public data and repositories.
        </p>
        <p>You may elect to give Codecov extender permissions (considered "private" scope).
          This increased scope is required in order to view and interact with private repositories on Codecov.
          We request the following scopes from GitHub:
        </p>
        <p><code>user:email, read:org, repo:status, write:repo_hook, <b>repo</b></code></p>
        <p>Learn more about <a href="https://developer.github.com/v3/oauth/#scopes">GitHub Scopes here</a>.</p>
      </div>
      <div class="ui more spacing divider"></div>
      <div>
        <h1 id="bitbucket-compare"><a href="#bitbucket-compare" class="anchor">&infin;</a> Bitbucket Compare</h1>
        <p>
          Bitbucket currently <strong>does not support</strong> retrieving a diff between two commit references.
          This lack of support is <strong>crucial</strong> to many of Codecov's internal operations.
        </p>
        <p>
          We are waiting for support which can be tracked in this
          <a href="https://bitbucket.org/site/master/issues/4779/ability-to-diff-between-any-two-commits">thread in Bitbucket Suppport</a>.
        </p>
        <p>Only affects Bitbucket. Bitbucket Server and Stash have full support available.</p>
      </div>
    </div>
  </div>
</div>
