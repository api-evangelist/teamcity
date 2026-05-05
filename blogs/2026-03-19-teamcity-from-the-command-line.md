---
title: "$ teamcity From the Command Line"
url: "https://blog.jetbrains.com/teamcity/2026/03/teamcity-cli/"
date: "Thu, 19 Mar 2026 09:42:53 +0000"
author: "Viktor Tiulpin"
feed_url: "https://blog.jetbrains.com/teamcity/feed/"
---
<p><em>Start builds, tail logs, and manage agents and queues – without switching windows.</em></p>



<p>Whether you are debugging a failed build, managing build agents, or scripting your deployment pipeline (or your AI coding agent is doing so) – there are times when opening a browser is one step too many.</p>



<p>TeamCity CLI is a lightweight, open-source tool that puts TeamCity at your fingertips.&nbsp;</p>



<p>A CLI for TeamCity has been a long-standing request from the community. Here’s how it works and what you can use it for.</p>



<p>TeamCity CLI includes over 60 commands, and for anything it doesn&#8217;t wrap yet, <code>teamcity api</code> gives you direct access to the full TeamCity REST API.</p>



<p><strong>Source code (Apache 2.0):</strong> <a href="https://github.com/JetBrains/teamcity-cli" rel="noopener" target="_blank">https://github.com/JetBrains/teamcity-cli</a></p>



<h2 class="wp-block-heading">Getting started</h2>



<p>Install and authenticate in seconds:</p>



<pre class="EnlighterJSRAW"># macOS / Linux
brew install jetbrains/utils/teamcity

# via a bash script
curl -fsSL https://jb.gg/tc/install | bash

# Windows
winget install JetBrains.TeamCityCLI

# via a powershell script
irm https://jb.gg/tc/install.ps1 | iex

# Connect to your server
teamcity auth login https://example.teamcity.com/</pre>



<p>That&#8217;s all! Now let’s see it in action.</p>



<h2 class="wp-block-heading">Investigating a failed build</h2>



<p>Let’s say something breaks. Here’s how to go from wondering what happened to having it fixed without switching windows.</p>



<h3 class="wp-block-heading">See what&#8217;s happening</h3>



<pre class="EnlighterJSRAW">teamcity run list --all</pre>



<figure class="wp-block-image size-full"><img alt="" class="wp-image-689574" src="https://blog.jetbrains.com/wp-content/uploads/2026/03/image3.gif" style="width: 100% !important; height: auto !important;" /></figure>



<p>Build 1389 failed. Here’s how we can drill down:</p>



<pre class="EnlighterJSRAW">teamcity run view 1389</pre>



<p>Need to jump to the TeamCity UI instead? Add <code>--web</code>.</p>



<h3 class="wp-block-heading">Find the root cause</h3>



<p>You don&#8217;t need to scroll through the entire log. Show only the failed step, then the failed tests:</p>



<pre class="EnlighterJSRAW">teamcity run log 1389 --failed</pre>



<figure class="wp-block-image size-full"><img alt="" class="wp-image-689585" src="https://blog.jetbrains.com/wp-content/uploads/2026/03/gif-1_see-whats-happening-1.gif" style="width: 100% !important; height: auto !important;" /></figure>



<p>Only one test failed, so you know exactly what to fix.</p>



<h3 class="wp-block-heading">Fix and re-trigger</h3>



<p>After you push the fix, restart and watch it in real time:</p>



<pre class="EnlighterJSRAW">teamcity run restart 1389
teamcity run watch 1408 --logs</pre>



<figure class="wp-block-image size-full"><img alt="" class="wp-image-689618" src="https://blog.jetbrains.com/wp-content/uploads/2026/03/image1.gif" style="width: 100% !important; height: auto !important;" /></figure>



<p>You see all the updates happening live in your terminal – build state changes, step progress, and streaming log output.</p>



<h3 class="wp-block-heading">Test before you push</h3>



<p>Want to validate your changes with CI before committing to a push? Run <a href="https://www.jetbrains.com/help/teamcity/personal-build.html" rel="noopener" target="_blank">a personal build</a> with your local changes:</p>



<pre class="EnlighterJSRAW">teamcity run start Sandbox_Test --local-changes</pre>



<p>TeamCity runs the build with your uncommitted work applied as a patch – no branch, no force-push, no noise in the repo.</p>



<h2 class="wp-block-heading">Remote agent access</h2>



<p>You can open an interactive shell session on any build agent – or execute commands remotely:</p>



<pre class="EnlighterJSRAW">teamcity agent list
teamcity agent term 813</pre>



<figure class="wp-block-image size-full"><img alt="" class="wp-image-689596" src="https://blog.jetbrains.com/wp-content/uploads/2026/03/image2.gif" style="width: 100% !important; height: auto !important;" /></figure>



<p>No SSH keys to manage, no VPN to connect – if your TeamCity server can reach the agent, so can you. </p>



<p>Need to just run a quick command? Here’s how:</p>



<pre class="EnlighterJSRAW">teamcity agent exec 813 &quot;docker ps -a&quot;</pre>



<h2 class="wp-block-heading">Built for scripting</h2>



<p>teamcity covers queues, agents, artifacts, and project configuration – the commands look exactly as you’d expect:</p>



<pre class="EnlighterJSRAW">teamcity queue list                                          # what&#039;s queued
teamcity queue top 461                                       # move a build to the front
teamcity queue approve 462                                   # approve a waiting build

teamcity agent list                                          # all agents with status
teamcity agent disable &quot;Linux Agent 03&quot; --comment &quot;Maint&quot;    # take one offline

teamcity run artifacts 453                                   # browse artifacts
teamcity run download 453 &quot;reports/**/*.html&quot; --output ./out # grab what you need

# Restart all failed builds on main
teamcity run list --failed --branch main --plain=id | xargs -I{} tc run restart {}

# Structured data for dashboards or scripts
teamcity run list --failed --json=id,status,buildType.name

# Hit any REST API endpoint directly
teamcity api /app/rest/server</pre>



<p>Every list command supports <code>--json</code> with field selection and <code>--plain</code> for tab-delimited text – making <code>teamcity</code> a building block for automation.</p>



<p><code>teamcity api</code> is the escape hatch – anything the CLI doesn&#8217;t wrap yet, you can call directly.</p>



<h2 class="wp-block-heading">Compatible with AI coding agents</h2>



<p>TeamCity CLI ships with an <a href="https://agentskills.io" rel="noopener" target="_blank">Agent Skill</a> that teaches AI coding assistants how to use the tool. Your AI agent can then check the build status, investigate failures, download artifacts, and manage your pipeline on your behalf.</p>



<p><strong>Users should limit the token rights granted to the agent, be aware of security implications, and always check the actions the agent intends to execute.</strong></p>



<figure class="wp-block-image size-full"><img alt="" class="wp-image-689607" src="https://blog.jetbrains.com/wp-content/uploads/2026/03/image5.gif" style="width: 100% !important; height: auto !important;" /></figure>



<h2 class="wp-block-heading">What&#8217;s next</h2>



<p>TeamCity CLI is open-source under Apache 2.0. There&#8217;s more we want to build – for example, pipeline visualization, richer TUI interfaces, and deeper integration with version control workflows. Your feedback will shape what comes next.</p>



<h2 class="wp-block-heading">Try it</h2>



<pre class="EnlighterJSRAW">brew install jetbrains/utils/teamcity       # macOS
winget install JetBrains.TeamCityCLI        # Windows
curl -fsSL https://jb.gg/tc/install | bash  # Linux/macOS setup script
irm https://jb.gg/tc/install.ps1 | iex      # Windows setup script</pre>



<p><strong>Source code and docs:</strong> <a href="https://github.com/JetBrains/teamcity-cli" rel="noopener" target="_blank">github.com/JetBrains/teamcity-cli</a></p>



<p><strong>Report issues or request features:</strong><a href="https://github.com/JetBrains/teamcity-cli/issues" rel="noopener" target="_blank"> GitHub Issues</a></p>
