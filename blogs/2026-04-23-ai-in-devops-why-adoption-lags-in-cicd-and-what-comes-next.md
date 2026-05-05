---
title: "AI in DevOps: Why Adoption Lags in CI/CD (and What Comes Next)"
url: "https://blog.jetbrains.com/teamcity/2026/04/ai-in-devops/"
date: "Thu, 23 Apr 2026 12:29:24 +0000"
author: "Olga Bedrina"
feed_url: "https://blog.jetbrains.com/teamcity/feed/"
---
<h2 class="wp-block-heading">AI is everywhere except in CI/CD</h2>



<p>Developers now use AI for nearly everything, except the part that actually ships code.</p>



<p>Recent surveys conducted by JetBrains indicate that AI is now widely used in software development, with workplace usage exceeding 90% and a large majority of developers already incorporating it into daily workflows. Developers rely on these tools for writing code, debugging, and navigating unfamiliar systems.</p>



<figure class="wp-block-image size-full"><img alt="" class="wp-image-702662" src="https://blog.jetbrains.com/wp-content/uploads/2026/04/which-of-these-ai-tools-do-you-use.png" style="width: 100% !important; height: auto !important;" /><figcaption class="wp-element-caption"><em>Source: JetBrains AI Pulse, January 2026</em></figcaption></figure>



<p>However, when you look at CI/CD pipelines, adoption is much more limited. This difference reflects how teams evaluate risk across the delivery lifecycle.</p>



<p><a href="https://www.jetbrains.com/teamcity/ci-cd-guide/ci-cd-pipeline/" rel="noopener" target="_blank">CI/CD pipelines</a> are the stage where changes are validated and prepared for release. At this point, teams rely on consistent, reproducible signals. Introducing non-deterministic systems into this environment raises concerns around reliability, compliance, and production impact.</p>



<p><em>Note on data:</em> The findings referenced in this article are based on internal JetBrains research conducted in January 2026 (<em>AI Pulse</em>) and October 2025 (<a href="https://devecosystem-2025.jetbrains.com/" rel="noopener" target="_blank"><em>State of Developer Ecosystem</em></a> and <a href="https://blog.jetbrains.com/teamcity/2025/10/the-state-of-cicd/"><em>State of CI/CD Tools</em></a> reports). Given the pace of change in AI, these results should be interpreted as a snapshot of current trends rather than a fixed baseline.</p>



<blockquote class="wp-block-quote">
<p></p>
<cite><strong>Key insight:</strong> AI adoption is highest where the cost of mistakes is low. CI/CD operates under different constraints.</cite></blockquote>



<h2 class="wp-block-heading">How AI is used in software development today</h2>



<p>According to JetBrains’ <em>AI Pulse</em> (January 2026), AI tools are now used by a large majority of developers in their daily work, and AI is already embedded in many parts of the software development lifecycle, but its impact is uneven.&nbsp;</p>



<p>In practice, most of the value today is concentrated upstream from CI/CD pipelines, in areas where developers can iterate quickly and validate results informally.</p>



<p>The table below compares how AI is used in day-to-day development work versus AI in DevOps pipelines. Each row highlights one aspect of the workflow and shows how the conditions differ.</p>



<figure class="wp-block-table"><table><tbody><tr><td><strong>Dimension</strong></td><td><strong>Upstream (IDE/dev workflow)</strong></td><td><strong>CI/CD pipelines</strong></td></tr><tr><td>Feedback loop</td><td>Immediate and local, results are visible right away</td><td>Slower and system-wide, feedback comes from full pipeline runs</td></tr><tr><td>Cost of error</td><td>Low; changes can be reverted easily</td><td>Higher; failures can affect builds or releases</td></tr><tr><td>Validation</td><td>Informal and often manual</td><td>Formal and automated through tests, scans, and checks</td></tr><tr><td>Role of AI</td><td>Assists developers during coding and exploration</td><td>Assists, but outputs must pass strict validation</td></tr><tr><td>Adoption level</td><td>High; widely used in daily workflows</td><td>Limited; used cautiously in specific scenarios</td></tr></tbody></table></figure>



<p>In day-to-day development work, AI is primarily used to accelerate routine tasks. Developers rely on it to generate code, refactor existing logic, and explore unfamiliar APIs. These interactions are fast and low-risk because they are easy to verify locally and can be discarded without consequences.</p>



<figure class="wp-block-image size-full"><img alt="" class="wp-image-702673" src="https://blog.jetbrains.com/wp-content/uploads/2026/04/what-areas-do-you-use-ai-in.png" style="width: 100% !important; height: auto !important;" /><figcaption class="wp-element-caption"><em>Source: JetBrains State of Developer Ecosystem 2025</em></figcaption></figure>



<p>The same applies to debugging workflows, where AI helps interpret logs and suggest likely causes of failures. Even when suggestions are imperfect, they provide a useful starting point that reduces the time spent on manual investigation.</p>



<p>AI is also widely used for documentation and knowledge discovery. In large codebases, understanding existing systems often takes longer than writing new code. AI reduces this friction by summarizing components, explaining dependencies, and surfacing relevant context.&nbsp;</p>



<p>Similarly, in security workflows, AI is increasingly used to flag potential vulnerabilities and suggest fixes, particularly in earlier stages of development.</p>



<p>What unites these use cases is not the specific task, but the environment in which they operate. They all sit in parts of the workflow where feedback is immediate, mistakes are easy to detect, and decisions can be reversed with minimal cost.</p>



<p>CI/CD pipelines operate under different conditions. Changes are no longer local experiments but candidates for release. At this stage, the cost of error increases, and the system relies on consistent, reproducible validation signals.&nbsp;</p>



<p>This shift in constraints explains why AI adoption is not progressing at the same pace across the entire DevOps lifecycle. Generally speaking, AI is expanding more quickly in development workflows and more cautiously inside CI/CD pipelines.</p>



<h2 class="wp-block-heading">Why AI adoption in CI/CD is still low</h2>



<p>AI in DevOps is still at an early stage compared to development workflows.</p>



<h3 class="wp-block-heading">What the data shows</h3>



<ul>
<li><strong>73%</strong> of organizations don’t use AI in CI/CD pipelines at all</li>



<li><strong>60%</strong> cite unclear use cases or value</li>



<li><strong>36%</strong> cite lack of trust in AI-generated results</li>



<li><strong>33%</strong> cite data privacy concerns</li>
</ul>



<figure class="wp-block-image size-full"><img alt="" class="wp-image-702695" src="https://blog.jetbrains.com/wp-content/uploads/2026/04/how-does-your-organization-use-AI-in-cicd-workflows-if-it-does.png" style="width: 100% !important; height: auto !important;" /><figcaption class="wp-element-caption"><em>Source: JetBrains State of CI/CD Tools survey</em></figcaption></figure>



<p>These results suggest that the main challenge is not technical integration. Teams are evaluating whether AI can reliably and predictably deliver value within a system that is responsible for validation.</p>



<p>In practice, AI adoption inside pipelines is shaped more by trust and measurable outcomes than by model capability.</p>



<figure class="wp-block-image size-full"><img alt="" class="wp-image-702706" src="https://blog.jetbrains.com/wp-content/uploads/2026/04/what-prevents-your-organization-from-adopting-a.png" style="width: 100% !important; height: auto !important;" /><figcaption class="wp-element-caption"><em>Source: JetBrains State of CI/CD Tools survey</em></figcaption></figure>



<h2 class="wp-block-heading">CI/CD is an evidence system, not just automation</h2>



<p>CI/CD is often framed as automation, but that undersells what it actually does. Its real job is to give teams enough confidence to ship changes without fear.</p>



<p>Every step in a pipeline is designed to reduce the likelihood and impact of production failures. Builds confirm code compiles. Tests validate behavior. Deployment processes ensure changes can go out and come back cleanly.</p>



<p>Think of it this way: CI/CD turns code changes into signals teams can act on. Test results, logs, deployment outcomes, all these answer one question: is this safe to release?</p>



<p>AI complicates this. It increases both the volume and variability of changes entering the pipeline, and CI/CD is built around predictability. That results in tension.</p>



<p>But it&#8217;s not a compatibility problem. AI-generated changes can move through a pipeline the same as any other, provided the pipeline can validate them with enough confidence. What changes is the stakes. When code is being written faster and in larger quantities, having a system that can catch bad changes reliably matters more, not less.</p>



<h2 class="wp-block-heading">Where AI actually works in CI/CD today</h2>



<p>Current use of AI in CI/CD pipelines is focused on improving how evidence is generated and interpreted.</p>



<h3 class="wp-block-heading">Failure diagnosis</h3>



<p>AI is most effective in CI/CD when it is used to speed up failure analysis rather than to make decisions. By processing pipeline logs at scale, identifying recurring patterns, and correlating errors across runs, AI tools help engineers identify likely root causes much faster than manual inspection.&nbsp;</p>



<p>This reduces initial triage time and allows teams to focus on resolving issues, while keeping decisions firmly under human control.</p>



<figure class="wp-block-image size-full"><img alt="" class="wp-image-702717" src="https://blog.jetbrains.com/wp-content/uploads/2026/04/teamcity-cli-agents.gif" style="width: 100% !important; height: auto !important;" /><figcaption class="wp-element-caption"><em>TeamCity CLI and Claude Code analyzing what builds are failing</em></figcaption></figure>



<p>In practice, this reduces the time spent on initial triage and allows teams to focus on resolving issues, while keeping the decision-making process firmly under human control.</p>



<h3 class="wp-block-heading">Security fixes</h3>



<p>In security workflows, AI is increasingly used to assist with identifying and remediating vulnerabilities discovered during pipeline execution. Rather than replacing existing scanning tools, AI builds on top of them by interpreting findings, suggesting fixes, and in some cases generating patches.&nbsp;</p>



<p>These suggestions still pass through standard CI/CD validation steps, including testing and review, which ensures that security improvements do not introduce regressions or unintended side effects.</p>



<h3 class="wp-block-heading">Test optimization</h3>



<p>Testing remains one of the most resource-intensive parts of CI/CD, and this is where AI is beginning to show measurable impact. By analyzing historical test runs and code changes, AI can prioritize which tests are most relevant for a given change, identify patterns of flaky behavior, and reduce redundant execution.&nbsp;</p>



<p>This leads to faster pipelines and more relevant feedback without sacrificing coverage entirely. Faster feedback is valuable, but it only matters if teams can still trust the results.</p>



<p>In practice, this means treating AI-driven test selection as an optimization layer rather than a replacement for validation. Teams often keep periodic full test runs in place and monitor for defects that might slip through reduced test sets. This approach allows them to increase speed without weakening the pipeline&#8217;s reliability.</p>



<p>The common thread across these use cases: AI is making validation more efficient, not replacing it.</p>



<h2 class="wp-block-heading">From copilots to agents: What’s changing</h2>



<p>The role of AI in DevOps is evolving from assistance to participation in workflows. Early tools focused on suggesting code or helping developers understand unfamiliar parts of the codebase by explaining logic, tracing dependencies, and summarizing large components.&nbsp;</p>



<p>Newer systems are beginning to generate changes, propose pull requests, and iterate based on feedback.</p>



<p>This shift introduces a different interaction model. Instead of developers being the only source of change, AI systems become contributors that operate within repository and pipeline workflows. They can suggest modifications, open pull requests, and respond to feedback loops created by CI/CD pipelines.</p>



<p>At first glance, this can create the impression that AI and CI/CD are in conflict. AI introduces more change, more variability, and less predictability, while CI/CD exists to enforce stability and control.</p>



<p>In practice, the opposite is true. The more AI participates in generating changes, the more teams rely on CI/CD to evaluate and constrain those changes. Pipelines become the mechanism that determines which AI-generated outputs are acceptable and which are not.</p>



<p>💡 Read also: &nbsp;<a href="https://blog.jetbrains.com/teamcity/2026/03/how-we-taught-ai-agents-to-see-the-bigger-picture/">How We Taught AI Agents to See the Bigger Picture</a></p>



<p>The implication for CI/CD is significant. Pipelines are no longer validating only human-written code. They are increasingly responsible for evaluating changes produced by automated systems. CI/CD becomes the environment where AI-generated changes are tested, constrained, and approved before they reach production.</p>



<p>In practical terms, this means AI in DevOps moves from being a productivity layer in the IDE to becoming part of the delivery system itself. The quality of that system determines whether agent-driven workflows can be adopted safely.</p>



<h2 class="wp-block-heading">The maturity model of AI in CI/CD</h2>



<p>AI doesn&#8217;t enter CI/CD all at once. Teams move through it gradually, expanding what they trust AI to do as the system proves itself.</p>



<p>Most teams are still at the starting point: AI isn&#8217;t in the pipeline at all. Developers might use it heavily in their editors, but the pipeline itself treats every change the same, regardless of how it was written.</p>



<p>The first real integration is usually about failure analysis. When a pipeline breaks, AI can read the logs, identify the error, and suggest what likely caused it. Engineers still make the call on what to fix and how. AI just cuts down the time spent staring at output trying to figure out where things went wrong.</p>



<p>From there, teams start letting AI generate outputs: suggested fixes, pull requests, configuration changes, test improvements. These still go through normal review and validation. AI is part of the workflow, but a human is still deciding what ships.</p>



<blockquote class="wp-block-quote">
<p></p>
<cite>AI is part of the workflow, but a human is still deciding what ships</cite></blockquote>



<p>The furthest stage is agent-like behavior, where AI can trigger actions on its own: opening pull requests, rerunning pipelines, proposing changes without being asked.&nbsp;</p>



<p>This doesn&#8217;t mean AI acts without limits. It can only trigger actions that have been explicitly permitted, every action is logged, and anything significant still requires a human to approve it before it goes through.</p>



<p>What determines how far a team can go with AI in CI/CD is whether the surrounding system, the validation, the policies, the pipeline signals, is reliable enough to support it.&nbsp;</p>



<p>Most teams are still in the first two stages, and survey data backs that up: direct AI integration inside CI/CD workflows remains uncommon. According to the JetBrains AI Pulse, 78.2% of respondents don’t use AI in CI/CD workflows at all.</p>



<figure class="wp-block-image size-full"><img alt="" class="wp-image-702728" src="https://blog.jetbrains.com/wp-content/uploads/2026/04/78-percent-of-respondents-dont-delegate-tasks-to-AI.png" style="width: 100% !important; height: auto !important;" /></figure>



<p>What matters across these stages is not the sophistication of the models, but the level of trust in the surrounding system. Each step forward requires stronger validation, clearer policies, and more reliable signals from the pipeline.</p>



<p>Most teams today remain in the first two stages, where AI is used to support understanding rather than to execute changes. This aligns with broader survey data showing limited adoption of AI directly inside CI/CD workflows.</p>



<p>To summarize this progression, the stages can be viewed side by side:</p>



<figure class="wp-block-table"><table><tbody><tr><td><strong>Stage</strong></td><td><strong>What changes in practice</strong></td><td><strong>Level of control</strong></td></tr><tr><td>No AI</td><td>Pipelines treat all changes equally</td><td>Fully human-driven</td></tr><tr><td>AI-assisted understanding</td><td>AI explains failures and logs</td><td>Human decisions</td></tr><tr><td>AI-assisted proposals</td><td>AI suggests fixes, PRs, and test changes</td><td>Human review required</td></tr><tr><td>Agentic workflows</td><td>AI can trigger actions within pipelines</td><td>Governed and constrained</td></tr></tbody></table></figure>



<p>This framing highlights that adoption is not about adding AI features, but about increasing the level of trust a team is willing to place in automated decisions.</p>



<h2 class="wp-block-heading">What this means for CI/CD systems</h2>



<p>As AI becomes more embedded in development workflows, the role of CI/CD systems shifts from automation to control and validation.</p>



<p>Three areas become critical:</p>



<p>First, <strong>the reliability and clarity of pipeline results start to limit how effectively teams can use AI.</strong> AI increases the volume of changes entering the system, which puts pressure on testing, build stability, and signal reliability. <a href="https://blog.jetbrains.com/teamcity/2025/12/how-to-tame-flaky-tests/">Flaky tests</a>, inconsistent builds, and unclear feedback loops become more visible and more costly.</p>



<p>Second, <strong>pipelines need clear controls over how changes progress</strong>. As AI systems begin to propose or trigger changes, teams rely on approvals, policy checks, access controls, and audit trails to govern them. These controls already exist in CI/CD, but they become more central as automation increases.</p>



<p>Third, <strong>integration with external systems becomes more important</strong>. CI/CD platforms are increasingly expected to expose pipelines, logs, and workflows in a way that other tools, including AI systems, can interact with. This shifts CI/CD from a closed automation system to a component in a broader toolchain.</p>



<h2 class="wp-block-heading">Conclusion: AI in DevOps needs a trust layer</h2>



<p>AI is accelerating software development workflows. CI/CD systems continue to focus on validation and release readiness. These two facts are not in conflict, but they do create pressure.</p>



<p>As AI-generated changes become more common, the role of CI/CD becomes more critical in ensuring those changes meet the standards required for production. Teams will increasingly evaluate their delivery systems based on their ability to handle higher change volume while maintaining reliability.</p>



<p>But the questions the industry has not fully answered yet are the following: As AI agents become more capable and more autonomous, how do you build governance mechanisms that scale with them? What does meaningful human oversight look like when a pipeline is processing hundreds of AI-generated changes per day? And at what point does the evidence that CI/CD produces need to be audited by AI itself?</p>



<p>These are not hypothetical. They are the questions that will define how CI/CD evolves over the next few years.</p>
