---
layout: post
comments: true
title:  "Installing Krita in Ubuntu 20.04 using the AppImage and creating a desktop entry"
credits: Backdrop Taken from <a href="https://krita-artists.org/t/mosquito-lagoon/38138"> Krita's Website </a>
categories: [tech]
date:   2022-03-12 00:00:00 +0530
background: '/img/posts/2022-03-12-installing-krita-from-appimage-ubuntu-20-04.jpeg'
---

<script src="{{ "/assets/js/prism.js" | prepend: site.baseurl | prepend: site.url }}"></script>

<p>
Krita is a sketching and painting program. It is also be used for 2D animations and is considered
an free and open source alternative to Adobe Animate. Their recommended way to use Krita is to
download the App Image and run it as an executable. But this way you would have run the file from
the terminal every time you want to use it. Wouldn't it be better if we could run the app as any
other normal application! This tutorial explains how you can install Krita's AppImage (and for that
matter any AppImage) and run it like you would run any other application.
</p>

<ol>
  <li> Download Krita's AppImage from their website's download page <a href="https://krita.org/en/download/krita-desktop/" rel="nofollow">here.</a></li>

  <li> Open the terminal and go to the directory where the AppImage has been downloaded </li>

  <li> Run <code> chmod +x krita.appimage </code> </li>

  <li> Copy the AppImage to <code> /usr/local/bin/</code> or <code>~/.local/bin/</code> using the <code>cp</code> command. Use <code>sudo</code> if you get the <code>Permission Denied</code> error. </li>

  <li> Change directory to the directory where the AppImage was downloaded </li>

  <li> Run <code> ./krita.appimage --appimage-extract </code></li>

  <li> This should extract the contents of the AppImage into the directory <code> squashfs-root </code> in the same directory </li>

  <li> <code> cd </code> into the <code> squashfs-root </code> directory and open the file <code> org.kde.krita.desktop </code> in a text editor for editing. </li>

  <li> Search for the line saying <code> Exec=krita %F </code> and replace <code>krita</code> with the location where you copied the AppImage. Eg. If you copied the AppImage to <code>/usr/local/bin/</code>, then the location of the AppImage is <code>/usr/local/bin/krita.appimage</code>. Save changes and exit. </li>

  <li> Copy the modified <code> org.kde.krita.desktop </code> file to <code> /.local/share/applications/ </code> directory. </li>

  <li> This will create a desktop entry for <code> Krita </code> but we still need to put the desktop icon in the proper directory. </li>

  <li> Now copy icon file, <code>krita.png</code> to <code>/usr/share/pixmaps/</code> using <code>sudo</code> </li>

  <li> Restart the GNOME shell by pressing <code>Alt+F2</code> and Run <code>restart</code>. You may even try restarting the computer. </li>

  <li> After this the AppImage should be properly installed along with the desktop entry.</li>

  <li> This approach can be followed for other AppImages as well </li>
</ol>



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

