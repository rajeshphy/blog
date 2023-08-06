---
layout: post
comments: true
title:  "ChatGPT in terminal"
subtitle: "Empower Your Terminal with AI Magic!"
credits: "Photo by Rajesh Kumar"
categories: [tech]
date:   2023-08-06 19:00:00 +0530
background: '/img/nainital-2019-03/nainital-2019-03-x2.jpg'
---
<img src="{{"/img/posts/terminal.jpg" | relative_url }}" alt="GitHub Token Generator" style="max-width:100%;">

As developers, we're always on the lookout for tools that can enhance our productivity and make our lives easier. Well, say hello to Shell-GPT, a game-changing command-line productivity tool that harnesses the power of OpenAI's ChatGPT (GPT-3.5) to supercharge your development process. With Shell-GPT, you can now generate shell commands, code snippets, comments, and documentation, all within the familiar confines of your terminal. No more need for cheat sheets or endless Google searches – this innovative tool brings accurate answers right to your fingertips.

## Installation and Setup

Getting started with Shell-GPT is a breeze. Simply run the following command to install it:

```bash
pip install shell-gpt
```

To start using Shell-GPT, you'll need an OpenAI API key. You can generate one from the OpenAI website. Once you have your API key, Shell-GPT will automatically use the `$OPENAI_API_KEY` environment variable if it's set, or it will prompt you to enter the key and store it in `~/.config/shell_gpt/.sgptrc` for future use.

## Diverse Usage Scenarios

Shell-GPT is a versatile tool with a wide range of use cases, making it an invaluable asset for developers. Let's explore some of the scenarios where Shell-GPT can come to your rescue.

### Simple Queries

With Shell-GPT, you can use your terminal as a powerful search engine. Ask any question, and get accurate answers instantly:

```bash
sgpt "What is the capital of France?"
# -> The capital of France is Paris.

sgpt "How do I check my public IP address?"
# -> You can check your public IP address by running: `curl ifconfig.me`

sgpt "How many bytes are there in a kilobyte?"
# -> 1 kilobyte is equal to 1024 bytes.
```

### Shell Commands

Finding and executing shell commands has never been easier. Just use the `--shell` option:

```bash
sgpt --shell "Create a new directory named 'project'"
# -> mkdir project

sgpt --shell "List all files in the current directory"
# -> ls

sgpt --shell "Remove a file named 'data.txt'"
# -> rm data.txt
```

And if you want to directly execute the received command, simply add the `--execute` (or `-se`) parameter:

```bash
sgpt --shell --execute "Install required Python packages"
# -> pip install numpy matplotlib pandas
# -> Execute shell command? [y/N]: y
# ...
```

### Code Generation

Need to generate code snippets quickly? Shell-GPT has got you covered. Use the `--code` parameter along with your query:

```bash
sgpt --code "Generate a random number between 1 and 10 in Python"
# -> import random
# -> random_number = random.randint(1, 10)
# -> print(random_number)
```

And since the output is valid Python code, you can easily redirect it to a file:

```bash
sgpt --code "Create a simple web server using Flask"
# -> from flask import Flask
# ->
# -> app = Flask(__name__)
# ->
# -> @app.route('/')
# -> def hello_world():
# ->     return 'Hello, World!'
# ->
# -> if __name__ == '__main__':
# ->     app.run()
# ->
# -> Save this code in a file named 'app.py' and run it using 'python app.py'
```

### Chat Sessions

Want to have interactive sessions with ChatGPT to improve its suggestions iteratively? Shell-GPT makes it a breeze:

```bash
sgpt --chat language "Translate 'hello' to French"
# -> 'hello' in French is 'bonjour'.

sgpt --chat calculation "What is the square root of 144?"
# -> The square root of 144 is 12.
```

## Conclusion

In conclusion, Shell-GPT brings the power of AI right into your development workflow. By delivering quick, accurate, and context-aware answers directly within your terminal, Shell-GPT revolutionizes the way you interact with the command line, boosting your efficiency and effectiveness.

Stay tuned for more exciting AI and No-Code content like this, and feel free to drop any questions you have in the comments below.

Thanks for reading! Happy coding with Shell-GPT!

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
