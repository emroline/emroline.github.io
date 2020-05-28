---
#subtitle: "Algorithms"
#author: anuroop
categories: [ Jekyll, Miscellaneous]
#excerpt: 
tags: []
under_development: false
---

To build and run your site using Jekyll, first navigate to the site's direcory, the you can use the following commands.

### Serve
{% highlight terminal %}
{% raw %}
jekyll serve
{% endraw %}
{% endhighlight %}

`serve` command builds and stores the build site to `_site` directory and runs a local development server at <a href="http://localhost:4000">http://localhost:4000</a> by default. Any changes we make to a site (except edits to _config.yml) trigger the site to rebuild and the development server to refresh. This command is typically used during development.

### Build
{% highlight terminal %}
{% raw %}
jekyll build
{% endraw %}
{% endhighlight %}

`build` command builds the site to `_site` diectory. We can copy the contents of `_site` directory to some web hosting provider and our site will come live on internet.

### Runtime flags
Runtime flags are used to modify how the site is build. Following are some of the build runtime flags that you can use:

## Tables

| Setting         | Flags |                                                              |
| --------         | ------ | ------------------------------------------------------------ |
| Change the source directory    |  `-s, --source DIR`    | 
| Change the destination directory of `_site`    | `-d, --destination DIR`  | 
| Disable custom plugins and ignore symbolic links. | `--safe`  | 
| Automatically regenerate the site when files are modified. | -w, --[no-]watch  |
| Specify config files instead of using `_config.yml` automatically. Settings in later files override settings in earlier files. | `--config FILE1[,FILE2,...]`  |
| Process and render draft posts. | `--drafts`  |
| Change jekyll build environment | `JEKYLL_ENV=production`  |
| Publish posts or collection documents with a future date. | `--future`  | 
| Limit the number of posts to parse and publish. | `Limit the number of posts to parse and publish.`  | 
| Print verbose output. | `-V, --verbose`  | 
| Silence the normal output from Jekyll during a build. | `-q, --quiet`  | 
| Enable the incremental build feature | `-I, --incremental`  | 
| Change the host address of running site | `-H, --host HOST`  | 
| Change the port of running site | `-P, --port PORT`  | 

**Note:** Incremental build only re-builds posts and pages that have changed, resulting in significant performance improvements for large sites, but may also break site generation in certain cases.

Following example shows how to use these flags:

{% highlight terminal %}
{% raw %}
JEKYLL_ENV=production jekyll build
{% endraw %}
{% endhighlight %}

{% highlight terminal %}
{% raw %}
JEKYLL_ENV=development jekyll serve --drafts --host 0.0.0.0 --port 8080 --incremental
{% endraw %}
{% endhighlight %}