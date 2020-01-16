---
layout: post
title:  "First Day - Install Jekyll"
date:   2020-01-13 14:11:55 -0800
categories: jekyll update
---
This is my first update outlining the steps to install jekyll. Adding a new post is as simple as creating a new markdown file
in the _posts\ folder.


{% highlight ruby %}
stuberadmin@DESKTOP-3EN365M MINGW64 ~
$ cd Documents/
stuberadmin@DESKTOP-3EN365M MINGW64 ~/Documents
$ cd GitHub/
stuberadmin@DESKTOP-3EN365M MINGW64 ~/Documents/GitHub
$ gem install bundler jekyll
stuberadmin@DESKTOP-3EN365M MINGW64 ~/Documents/GitHub
$ jekyll new nape_tca_nn_blog
stuberadmin@DESKTOP-3EN365M MINGW64 ~/Documents/GitHub/nape_tca_nn_blog
$ bundle exec jekyll serve
{% endhighlight %}

{% highlight ruby %}
stuberadmin@DESKTOP-3EN365M MINGW64 ~/Documents/GitHub/nape_tca_nn_blog
$ git init
stuberadmin@DESKTOP-3EN365M MINGW64 ~/Documents/GitHub/nape_tca_nn_blog (master)
$ git checkout -b gh-pages
stuberadmin@DESKTOP-3EN365M MINGW64 ~/Documents/GitHub/nape_tca_nn_blog (gh-pages)
$ git add .
stuberadmin@DESKTOP-3EN365M MINGW64 ~/Documents/GitHub/nape_tca_nn_blog (gh-pages)
$ git commit -m "initializing commit"
{% endhighlight %}

{% highlight ruby %}
stuberadmin@DESKTOP-3EN365M MINGW64 ~/Documents/GitHub/nape_tca_nn_blog (gh-pages)
$ git remote add origin https://github.com/zhounapeuw/nape_tca_nn_blog.git
stuberadmin@DESKTOP-3EN365M MINGW64 ~/Documents/GitHub/nape_tca_nn_blog (gh-pages)
$ git push origin gh-pages
{% endhighlight %}

{% highlight ruby %}
stuberadmin@DESKTOP-3EN365M MINGW64 ~/Documents/GitHub/nape_tca_nn (master)
$ bundle exec jekyll serve
{% endhighlight %}

If you get this problem: error `/' not found, you will need to run the command below instead.
See this post for details: https://github.com/jekyll/jekyll/issues/1432

{% highlight ruby %}
stuberadmin@DESKTOP-3EN365M MINGW64 ~/Documents/GitHub/nape_tca_nn_blog (gh-pages)
$ jekyll serve --baseurl ""
{% endhighlight %}

![Github repo settings - github pages link](/_assets/images/github_pages_config.png)

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
