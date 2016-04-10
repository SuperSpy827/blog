---
layout: post
title: How to use Cloudflare for free SSL with Github Pages
summary: An easy-to-follow tutorial on how to use Cloudflare for free SSL
---
## Setting up Cloudflare for your Domain

As I said in my previous [post](https://blog.koga.tech/2016/03/29/up-and-running), I use Github Pages to host my blog. One downside is that there is no SSL on custom domains. I mentioned this to a friend of mine and he recommended Cloudflare as the free plan has free SSL. The following steps tell you how you can use it too.

![img-1](/images/posts/using-cloudflare/img-1.png)

<h1></h1>

First off, create an account at (cloudflare.com)[https://www.cloudflare.com]. It is a farily self-explanatory process and google shows you a guide [here](https://www.google.com/search?q=create+account+cloudflare). You will then be presented with a page that asks you to enter your domain names you wish to administer with Cloudfare. Be sure you input the __base domain__ only. For example I would put '_koga.tech_' instead of '_www.koga.tech_'. 

![img-3](/images/posts/using-cloudflare/img-3.png)

<h1></h1>

After that click _Continue Setup_ and it will begin playing a video while it scans your DNS records, the process should take about a minute. When it is finished press _Continue_.

![img-4](/images/posts/using-cloudflare/img-4.png)

<h1></h1>

Now Cloudflare will be ask you to verify your DNS records. You can modify them if you wish before scrolling down and clicking _Continue_ once again. Note that in most cases, you won't need to 

![img-5](/images/posts/using-cloudflare/img-5.png)

<h1></h1>

You will be asked which plan you wish to use. For this tutorial, I will use the free plan since that is what I used. Simple select it and click that familiar button to proceed.

![img-6](/images/posts/using-cloudflare/img-6.png)

<h1></h1>

Now you are at the final step in this section, Cloudflare is asking you to change your nameservers to the two it assigns to you. The instructions for changing nameservers vary from registar to registar and I recommend you consult your registar's knowledgebase for details. In this picture, you will note that the original nameservers are already Cloudflare ones. This is because I have already setup koga.tech with another Cloudflare account.

![img-7](/images/posts/using-cloudflare/img-7.png)

<h1></h1>


## Enabling SSL support

While SSL should be enabled by default, it never hurts to check. Click on the cloud in the middle of the navigation bar to enter the overview. If the Settings Summary says SSL is flexible, full or full (strict) then you can stop right here as SSL is enabled already. If you want to go further, you can skip to the <a href="#going-further">Going Further</a> section. Otherwise, click on the _Crypto_ button to edit your SSL preferences.

![img-8](/images/posts/using-cloudflare/img-8.png)

<h1></h1>

Simply click on the multiple-choice button and select Flexible if you don't have a custom SSL certificate, Full if you have a custom SSL certificate stored on the server or Full (Strict). I chose Flexible as while Github Pages doesn't support SSL certs being stored on it, it does allow a secure connection between Cloudfare (who is actually serving up the content) and us. The connection between Cloudfare and Github however is not encrypted.

![img-9](/images/posts/using-cloudflare/img-9.png)

<h1></h1>

## Going Further: Autoredirecting to HTTPS <a name="going-further"></a>

Now we have SSL setup by default, there's just one catch: you can't autoredirect to the HTTPS version of your website... _yet_. This can be solved by using a nifty tool provided by Cloudflare called _Page Tools_. Simple scroll to the top of the page and click on it's button. 

![img-10](/images/posts/using-cloudflare/img-10.png)

<h1></h1>

Here you will see a form to add a new rule. In the textbox that says '_URL Pattern_', type in 'http://' followed by the same base url you used earlier. For me it would be '_http://koga.tech_'. This tells Cloudflare that we want our rule to affect the following URL pattern. Then tick the '_Always use HTTPS_', this will make all the other options - except the URL Pattern box obviously - disappear. 

![img-11](/images/posts/using-cloudflare/img-11.png)

<h1></h1>

In conclusion, getting and using SSL for a Github Pages is trivial with the right tools. Used correctly Cloudflare can be a powerful tool providing a huge amount of features in just its free plan. While I find the free plan enough for my own needs, upgrading is viable for those who need it. As always send me an email if you need anything, my email address can be found on my about page.