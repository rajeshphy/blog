---
layout: post
comments: true
title:  "Pushing to GitHub repo from Travis CI [WIP]"
subtitle: "A guide to pushing changes to a GitHub repo from TravisCI"
categories: [tech]
date:   2019-04-10 01:28:00 +0530
background: '/img/pushing-to-github-from-Travis-CI/02-backdrop.jpg'
---

<script src="{{ "/assets/js/prism.js" | prepend: site.baseurl | prepend: site.url }}"></script>

<p>
Sometimes we may need to make some changes in a repository and push
it to the GitHub repository from TravisCI. An example would be to use TravisCI
to deploy a Jekyll website to github for which we can
build the website in TravisCI and push the <code> &#95;site </code>
data in the GitHub branch.

<br>

The issue comes when we try to push the changes in the git repository,
which requires authorisation, which can't be entered manually in TravisCI.

<br>

We can solve this issue with something called GitHub's
<code>Personal Access Tokens</code>. Generate a <code>Pesonal Access Token</code>
by following
<a target="_blank" rel="noopener noreferrer" href="https://help.github.com/en/articles/creating-a-personal-access-token-for-the-command-line">this article</a>
by GitHub.

<br>

While generating the token, we need to give access to the github repository.
For this, check the options shown in the image below (in black border) on the
Token generator page. This will allow the service with this token to make
changes to a repository in GitHub.

<br>

<img src="{{"/img/pushing-to-github-from-Travis-CI/01-github-token-generator.jpg" | relative_url }}" alt="GitHub Token Generator" style="max-width:100%;">

<br>
<br>


Now we need to tell TravisCI about the token. But this GitHub token
has to be encrypted before we give it to TravisCI. To do this first
install <code>travis</code> in your local linux machine and login to
<code>travis</code> by using these commands:
<pre>
  <code class="language-bash">
      sudo gem install travis
      travis login
  </code>
</pre>

After this, add these lines in the <code>after_script</code> part of your
<code>.travis.yml</code> file.

<pre>
  <code class="language-yaml">
 after_script:
   - git config credential.helper "store --file=.git/credentials"
   - echo "https://${GH_TOKEN}:@github.com" > .git/credentials
   - node ./node_modules/grunt-cli/bin/grunt release
  </code>
</pre>

Now, while staying in the directory where <code>.travis.yml</code> is,
run,

<pre>
  <code class="language-bash">
    travis encrypt 'GITHUB_TOKEN=&lt;REPLACE-WITH-YOUR-GITHUB-PERSONAL-ACCESS-TOKEN&gt;' --add
  </code>
</pre>

This will add the encrypted <code>Personal Access Token</code> in
your <code>.travis.yml</code> file.

<br>

When TravisCI builds on your repo, it stores this token in the global
variable <code class="language-bash">GITHUB_TOKEN</code>, which you can
use to push to a particular github repository via a command which looks
something like this

<pre>
  <code class="language-bash">
    git push -f -q https://${GITHUB_TOKEN}@github.com/&lt;GITHUB-USERNAME&GT;/&lt;GITHUB-REPO-NAME&gt;.git &lt;DEPLOY_BRANCH&gt;
  </code>
</pre>

Note however that the command <code class="language-bash">git push</code>
can only be used after the variable <code class="language-bash">GITHUB_TOKEN</code>
has been initialised, which only happens after the commands shown in
<code>after_script</code> section of the <code>.travis.yml</code> has
been executed. So, any script using <code class="language-bash">git push</code>
should be put after those three commands in <code>after_script</code>.
</p>




{% if page.comments %}
<div id="disqus_thread"></div>
<script>
    /**
     *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
     *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables
     */
    /*
    var disqus_config = function () {
        this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
        this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    */
    (function() {  // REQUIRED CONFIGURATION VARIABLE: EDIT THE SHORTNAME BELOW
        var d = document, s = d.createElement('script');

        s.src = 'https://amanabt.disqus.com/embed.js';  // IMPORTANT: Replace EXAMPLE with your forum shortname!

        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
{% endif %}
