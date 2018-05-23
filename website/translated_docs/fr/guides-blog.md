---
id: blog
title: Adding a Blog
---
## Initial Setup

To setup your site's blog, start by creating a `blog` folder within your repo's `website` directory.

Then, add a header link to your blog within `siteConfig.js`:

```js
headerLinks: [
    ...
    { blog: true, label: 'Blog' },
    ...
]
```

## Adding Posts

To publish in the blog, create a file within the blog folder with a formatted name of `YYYY-MM-DD-My-Blog-Post-Title.md`. The post date is extracted from the file name.

For example, at `website/blog/2017-08-18-Introducing-Docusaurus.md`:

```yml
---
author: Frank Li
authorURL: https://twitter.com/foobarbaz
authorFBID: 503283835
title: Introducing Docusaurus
---

Lorem Ipsum...
```

## Header Options

The only required field is `title`; however, we provide options to add author information to your blog post as well.

* `author` - The text label of the author byline.
* `authorURL` - The URL associated with the author. This could be a Twitter, GitHub, Facebook account, etc.
* `authorFBID` - The Facebook profile ID that is used to fetch the profile picture.
* `authorImageURL` - The URL to the author's image. (Note: If you use both `authorFBID` and `authorImageURL`, `authorFBID` will take precedence. Don't include `authorFBID` if you want `authorImageURL` to appear.)
* `title` - The blog post title.

## Summary Truncation

Use the `<!--truncate-->` marker in your blog post to represent what will be shown as the summary when viewing all blog published blog posts. Anything above `<!--truncate-->` will be part of the summary. For example:

```yaml
---
title: Truncation Example
---

All this will be part of the blog post summary.

Even this.

<!--truncate-->

But anything from here on down will not be.

Not this.

Or this.
```

## Changing How Many Blog Posts Show on Sidebar

By default, 5 recent blog posts are shown on the sidebar.

You can configure a specific amount of blog posts to show by adding a `blogSidebarCount` setting to your `siteConfig.js`.

The available options are an integer representing the number of posts you wish to show or a string with the value 'ALL'.

Example:

```js
blogSidebarCount: 'ALL'
```

## RSS Feed

Docusaurus provides a simple RSS feed for your blog posts. Both RSS and Atom feed formats are supported. This data is automatically to your website page's HTML 

<head>
  tag.</p> 
  
  <p>
    A summary of the post's text is provided in the RSS feed up to the <code>&lt;!--truncate--&gt;</code>. If no <code>&lt;!--truncate--&gt;</code> tag is found, then all text up 250 characters are used.
  </p>
  
  <h2>
    Social Buttons
  </h2>
  
  <p>
    If you want Facebook and/or Twitter social buttons at the bottom of your blog posts, set the <code>facebookAppId</code> and/or <code>twitter</code> <a href="api-site-config.md">site configuration</a> options in <code>siteConfig.js</code>.
  </p>
  
  <h2>
    Advanced Topics
  </h2>
  
  <h3>
    I want to run in "Blog Only" mode.
  </h3>
  
  <p>
    You can run your Docusaurus site without a landing page and instead have your blog load first.
  </p>
  
  <p>
    To do this:
  </p>
  
  <ol>
    <li>
      Create a file <code>index.html</code> in <code>website/static/</code>.
    </li>
    
    <li>
      Place the contents of the template below into <code>website/static/index.html</code>
    </li>
    
    <li>
      Customize the <code>&lt;title&gt;</code> of <code>website/static/index.html</code>
    </li>
    
    <li>
      Delete the dynamic landing page <code>website/pages/en/index.js</code>
    </li>
  </ol>
  
  <blockquote>
    <p>
      Now, when Docusaurus generates or builds your site, it will copy the file from <code>static/index.html</code> and place it in the site's main folder. The static file is served when a visitor arrives on your page. When the page loads it will redirect the visitor to <code>/blog</code>.
    </p>
  </blockquote>
  
  <p>
    You can use this template:
  </p>
  
  <pre><code class="html">&lt;!DOCTYPE HTML&gt;
&lt;html lang="en-US"&gt;
  &lt;head&gt;
    &lt;meta charset="UTF-8"&gt;
    &lt;meta http-equiv="refresh" content="0; url=blog/"&gt;
    &lt;script type="text/javascript"&gt;
      window.location.href = 'blog/';
    &lt;/script&gt;
    &lt;title&gt;Title of Your Blog&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
    If you are not redirected automatically, follow this &lt;a href="blog/"&gt;link&lt;/a&gt;.
  &lt;/body&gt;
&lt;/html&gt;
</code></pre>