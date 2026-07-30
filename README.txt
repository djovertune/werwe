ALLAI WEBSITE — WHAT'S IN HERE AND HOW TO PUT IT LIVE
=====================================================

FILES
-----
index.html          the site. one page, no build step, no dependencies.
404.html            "page not found", styled to match.
favicon.svg         browser tab icon (modern browsers).
favicon-32.png      fallback for older browsers.
favicon-192.png     Android home screen.
apple-touch-icon.png iOS home screen.
og-image.png        the preview picture when you paste your link into
                    LinkedIn, WhatsApp, email etc. Worth having.
robots.txt          tells search engines they're welcome.
sitemap.xml         helps Google find the page.
netlify.toml        caching + security headers. Netlify reads this itself.
brand/              your logo in every variant, for invoices, vans, socials.


BEFORE YOU DEPLOY — ONE THING
-----------------------------
Replace the placeholder phone number. It appears in BOTH index.html and
404.html, in two forms:

    0000 000 0000        (what people read)
    +440000000000        (what the tap-to-call link uses)

Find and replace both, in both files. If you skip this, the site will
invite people to ring a number that doesn't exist.


PUTTING IT LIVE
---------------
1. Log in to Netlify.
2. Open your site, go to the "Deploys" tab.
3. Drag this whole folder onto the drop zone that says
   "Drag and drop your site output folder here".
4. Wait about ten seconds. It's live.

That's it - no build command, no framework, nothing to install.


THE CONTACT FORM
----------------
It uses Netlify Forms, which works automatically once deployed - there's
nothing to set up. Submissions appear under Forms in your Netlify
dashboard.

Worth doing once: in Netlify go to Forms -> Settings -> Form notifications
-> add an email notification to filip.lubas@allsai.net, so a new enquiry
lands in your inbox instead of waiting to be noticed.

There's a hidden honeypot field that catches most spam bots.


POINTING allsai.net AT IT
-------------------------
Do NOT switch your nameservers to Netlify - that would move your DNS away
from Squarespace and break your Google Workspace email.

Instead, in Netlify: Domain management -> Add a domain -> allsai.net.
Then in Squarespace DNS -> Custom Records, add:

    Host: @      Type: A       Data: 75.2.60.5
    Host: www    Type: CNAME   Data: <your-site>.netlify.app

If an A record already exists on @, REPLACE it - don't add a second one.
Leave the MX and TXT records alone, they're your email.

SSL is issued automatically once DNS propagates.


CHANGING THINGS LATER
---------------------
It's one HTML file with the styles at the top. Text lives in plain
readable HTML further down. To change a heading, search for the words you
want to change and type over them.

The colours are all defined once at the top of the <style> block, under
:root - change a hex value there and it updates everywhere.
