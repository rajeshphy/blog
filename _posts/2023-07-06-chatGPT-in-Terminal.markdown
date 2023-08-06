---
layout: post
comments: true
title:  "Test Blog"
subtitle: "Test Blog Format"
credits: "Photo by Rajesh Kumar"
categories: [tech]
date:   2023-07-06 19:00:00 +0530
background: '/img/nainital-2019-03/nainital-2019-03-x2.jpg'
---

# Introducing GPT-CLI: Empower Your Terminal with AI Magic!
<img src="{{"/img/posts/terminal.jpg" | relative_url }}" alt="GitHub Token Generator" style="max-width:100%;">

Are you tired of switching between your code editor and the browser to find that elusive piece of code or command? Say hello to GPT-CLI, the ultimate command-line productivity tool that brings the power of OpenAI’s ChatGPT (GPT-3.5) right to your terminal! GPT-CLI streamlines your development process by generating shell commands, code snippets, and more, helping you boost productivity and code like a wizard.

## Installation and Setup

To get started with GPT-CLI, follow these simple steps:

Step 1: Install GPT-CLI using pip

```shell
pip install gpt-cli
```

Step 2: Obtain an API Key

To use GPT-CLI, you'll need an OpenAI API key. Head over to [OpenAI's website](https://openai.com) to generate your API key.

Step 3: Configure GPT-CLI

Once you have your API key, set it up as an environment variable, or let GPT-CLI prompt you for it during the first run. Your API key will be securely stored in `~/.config/gpt_cli/config.yaml` for future use.

## Diverse Usage Scenarios

GPT-CLI offers a plethora of use cases that cater to your coding and development needs. From simple queries to executing shell commands and generating code, GPT-CLI is your go-to companion for all things development.

### Simple Queries

Need quick answers without browsing the web? Use GPT-CLI like your personal search engine:

```shell
gpt-cli "current date and time in India"
# -> The current date and time in India is 2023-08-06 15:30:00.

gpt-cli "convert Celsius to Fahrenheit formula"
# -> The formula to convert Celsius to Fahrenheit is: (Celsius * 9/5) + 32.

gpt-cli "definition of recursion"
# -> Recursion is a programming technique where a function calls itself to solve a problem.
```

### Shell Commands

Finding and running shell commands has never been easier with GPT-CLI's `--shell` option:

```shell
gpt-cli --shell "list all files in current directory"
# -> ls
```

Execute the command directly using the `--execute` (or `-e`) parameter:

```shell
gpt-cli --shell --execute "list all files in current directory"
# -> ls
# -> Execute shell command? [y/N]: y
# ...
```

### Code Generation

Generating code snippets is a breeze with GPT-CLI's `--code` parameter:

```shell
gpt-cli --code "generate random numbers in Python"

# -> Response
import random

random_numbers = [random.randint(1, 100) for _ in range(10)]
print(random_numbers)
```

Redirect the output to a file and execute it:

```shell
gpt-cli --code "generate random numbers in Python" > random_numbers.py
python random_numbers.py
# [86, 23, 57, 71, 4, 92, 10, 33, 29, 58]
```

### Chat Sessions

Engage in interactive chat sessions with GPT-CLI for iterative improvements or dynamic queries:

```shell
gpt-cli --chat favorite_color "my favorite color is blue"
# -> Got it! Your favorite color is blue.

gpt-cli --chat favorite_color "what color complements blue?"
# -> Blue's complement is orange.
```

## Conclusion

With GPT-CLI, you can harness the power of AI directly in your terminal. Embrace the efficiency and convenience it brings to your development workflow, reducing the time spent searching for answers and enhancing your coding experience. Stay tuned for more exciting AI-driven tools and content to level up your coding game!

Happy coding with GPT-CLI!

*ChatGPT*


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

        s.src = 'https://consultt-github-io.disqus.com/embed.js';  // IMPORTANT: Replace EXAMPLE with your forum shortname!

        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
{% endif %}
