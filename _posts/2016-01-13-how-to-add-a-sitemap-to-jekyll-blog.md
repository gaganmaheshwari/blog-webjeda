---
title: Adding Sitemap to Jekyll Blog
desc: Submitting sitemap to major search engines is important to get indexed and rank better. Jekyll blogs will not have sitemap by default but we can create one using this method. A sitemap facilitates search engines as an easy main-door to crawl through all the post and pages you have in your blog.
keywords: sitemap in Jekyll blog, Jekyll sitemap, sitemap for Jekyll
author: sharathdt
tags: Jekyll SEO
image: add-sitemap-to-Jekyll-github-pages.png
layout: post
permalink: /jekyll-sitemap/
---

<img width="600px" max-height="375px" alt="{{page.title}}" title="{{page.title}}" itemprop="thumbnailUrl" class="left half noborder" src="/thumbs/{{page.image}}">

<i class="fa fa-quote-left fa-3x fa-pull-left fa-border"></i>{{page.desc}}
{: .intro}

In one of my previous posts, I wrote on [How to create a Jekyll Blog](/create-jekyll-blog/){:target="_blank"}. If you have created a blog or if you already have a Jekyll blog then go through this tutorial to know how to create a sitemap automatically and manually in easy steps.
{: .clear}

* Do not remove this line (it will not be displayed) 
{:toc}


![Sitemap of a website]({{ site.url }}/images/how-to-add-sitemap-to-jekyll.jpg)
{: .right .half}
A sitemap is a list of links to all your web pages. It will be in ```.xml``` format. It helps search engine bots to crawl your website. It will also have metadata such as dates of posts, pages, last modified date and how often it was updated etc., It looks something like your **feed.xml** file but with different tags. 

Here is [my blog's Sitemap](/sitemap.xml){:rel='dofollow'}{:target="_blank"}


## Why is a Sitemap used?
{: .clear}
If your website doesn't have any posts or pages, you may not need a sitemap. But for a blog with several posts, a sitemap is necessary (if you want to rank better in search engines). You can submit your sitemap to major search engines like Google, Bing, Yahoo etc., so that their respective bots crawl your site and index them. Only after indexing, your website link appears in the search results.

Leaving a link to your sitemap inside your website is also a good idea. Let's say someone refers to a post of yours in their well-ranked blog. There are chances that a bot will crawl that link and land on your post. You shouldn't miss a chance of giving the link to your sitemap when the bot is crawling your post! 

[Submit your sitemap to Google](https://www.google.com/webmasters/tools/home?hl=en){:rel='nofollow'}{:target="_blank"} if you already have one. I usually submit my sitemap to Webmaster tools of Google, Bing, and Yahoo. 

I use [SEO-checkup](https://toolbox.seositecheckup.com/apps/seo-checkup){:rel='nofollow'}{:target="_blank"} to check whether my websites comply with common SEO parameters. I found out that I did not have a sitemap by using this app. I will write a detailed post on some useful on-line tools to optimize your website to make perform well and search engine friendly.

## How to create a sitemap for Jekyll blog?

In WordPress, creating a sitemap using a plugin is very easy! What if I tell you that creating a sitemap in Jekyll is much easier! 

Jekyll blogs will not have sitemap by default. You can always generate them using a small snippet of code. Add the below code to your **_config.yml** file. This will create a sitemap for you with the link ```/sitemap.xml```.

{% highlight css %}
gems:
  - jekyll-sitemap
{% endhighlight %}


Here is my [_config.yml](https://raw.githubusercontent.com/sharu725/emerald/gh-pages/_config.yml){:rel='nofollow'} file for reference. You will not be able to see the XML file created for sitemap inside your directory.

{% include adsense-inside-post.html %}

Now, commit the changes and hit the URL ``yourwebsite.com/sitemap.xml``. You should see all your links listed there.

<iframe width="100%" height="360" class="left half" src="https://www.youtube.com/embed/kiBtQClK-XQ?rel=0" frameborder="0" allowfullscreen></iframe>
Here is a video demonstration



## The hard way to insert sitemap in Jekyll blog!
{: .clear}
You can also list all the links by yourself. Don't worry, we will be using ```ul``` so that it gets and arranges the links  one by one. Create a file in the root of the repository and name it **whatever.xml**. Copy this code inside it

{% highlight html %}---
---
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    {% raw %}{% for post in site.posts %}{% endraw %}
    <url>
        <loc>{% raw %}{{site.url}}{% endraw %}{% raw %}{{ post.url | remove: 'index.html' }}{% endraw %}</loc>
    </url>
    {% raw %}{% endfor %}{% endraw %}

    {% raw %}{% for page in site.pages %}{% endraw %}
    {% raw %}{% if page.layout != nil %}{% endraw %}
    {% raw %}{% if page.layout != 'feed' %}{% endraw %}
    <url>
        <loc>{% raw %}{{site.url}}{% endraw %}{% raw %}{{ page.url | remove: 'index.html' }}{% endraw %}</loc>
    </url>
    {% raw %}{% endif %}{% endraw %}
    {% raw %}{% endif %}{% endraw %}
    {% raw %}{% endfor %}{% endraw %}
</urlset>
{% endhighlight %}

This is a feed file written in liquid tags. It will look for all the posts and pages you have and list them inside a ``sitemap.xml`` file. It also gets updated upon adding new posts and pages.

In this method, you will have the full control of your sitemap. You can exclude whatever you think is not important and include links that you want it to be in the sitemap.

I hope that helped. If you are having problems with generating a sitemap please leave a comment. I will try to fix it. 

Thanks for reading!