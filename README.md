# <http://www.jack003.com>

Jack's blog.

![Blog](blog.jpeg)

This is a simple, beautiful and swift theme for Jekyll. It's mobile first, fluidly responsive, and delightfully lightweight.

It's pretty minimal, but leverages large type and drastic contrast to make a statement, on all devices.

The landing page of the blog is bilingual page.

Jekyll theme.

## Getting Started

If you're completely new to Jekyll, I recommend checking out the documentation at <http://jekyllrb.com> or there's a tutorial by Smashing Magazine.

```
$ git clone https://github.com/Jack614/jack_blog.git
$ cd jack_blog
$ gem install jekyll # If you don't have jekyll installed
$ rm -rf _site && jekyll server
```

#### Fork, then clone

Fork the repo, and then clone it so you've got the code locally.


### Modify the _config.yml

The _config.yml located in the root of the jack_blog directory contains all of the configuration details for the Jekyll site. The defaults are:

```
# Welcome to Jekyll!

# Site settings
title: "Jack's blog"

baseurl: "/"
url: "http://www.jack003.com"
# url: "http://127.0.0.1:4000"

# author
author:
  name: 'Jack'
  first_name: 'Jia'
  last_name: 'Kun'
  email: 'jack19890614@gmail.com'
  facebook_username: 'jiakunnj'
  github_username: 'Jack614'
  head_img: 'static/img/landing/Jack.jpg'

# landing page
landing:
  home: 'Home'
  about: 'About'
  career: 'Career'
  skills: 'Skills'
  blog: 'Blog'
  contact: 'Contact'

# blog index
index:
  home: 'Home'
  python: 'Python'
  linux: 'Linux'
  html: 'HTML'
  database: 'Database'
  mac: 'Mac'
  life: 'Life'
# blog img path
img_path: '/static/img/blog'

# Build settings
encoding: "utf-8"

highlighter: rouge
markdown: kramdown
kramdown:
  input: GFM
  syntax_highlighter: rouge
```
### Jekyll Serve

Then, start the Jekyll Server. I always like to give the --watch option so it updates the generated HTML when I make changes.

```
$ jekyll serve --watch
```

Now you can navigate to localhost:4000 in your browser to see the site.

### Using Github Pages

You can host your Jekyll site for free with Github Pages. [Click here](https://pages.github.com) for more information.

A configuration tweak if you're using a gh-pages sub-folder

In addition to your github-username.github.io repo that maps to the root url, you can serve up sites by using a gh-pages branch for other repos so they're available at github-username.github.io/repo-name.

This will require you to modify the _config.yml like so:

```
# Welcome to Jekyll!

# Site settings
title: Repo Name

baseurl: "/"
url: "http://github-username.github.io"
# url: "http://127.0.0.1:4000"

# author
author:
  name: nickname
  first_name: firstname
  last_name: lastname
  email: your_email@example.com
  facebook_username: facebook_example
  github_username: 'github_example
  head_img: 'path/of/head/img'

# landing page
landing:
  home: landing-1
  about: landing-2
  career: landing-3
  skills: landing-4
  blog: landing-5
  contact: landing-6

# blog index
index:
  home: index-1
  python: index-2
  linux: index-3
  html: index-4
  database: index-5
  mac: index-6
  life: index-7

# blog img path
img_path: '/path/of/blog/img/'
```

If you start server on localhost, you can turn on `# url: "http://127.0.0.1:4000"`.

### Pagination

The pagination in jekyll is not very perfect,so I use front-end web method, please refer to [jPages](http://luis-almeida.github.io/jPages).

### Bilingual Page

#### Step 1

To add i18 support for your app you need to define what text you would like to translate. The best way to define your text is to store it in external json file. For example:

**Each language you should have own json file!**

en.json

```
{
  "website":{
    "title": "Jack's blog"
  },
  "nav":{
    "home": "Home",
    "about_me": "About",
    "skills": "Skills",
    "career": "Career",
    "blog": "Blog",
    "contact": "Contact"
  }
}
```

cn.json

```
{
  "website":{
    "title": "杰克的博客"
  },
  "nav":{
    "home": "首页",
    "about_me": "关于我",
    "skills": "技能",
    "career": "职业",
    "blog": "博客",
    "contact": "联系我"
  }
}
```

#### Step 2

Next you need to add html indicators in all place you want to use i18.(index.html)

```
<a class="navbar-brand" href="#page-top" id="i18_title"><span data-i18n="website.title">{{ site.title }}</span></a>
```

#### Step 3

Next you need to initialise the i18next plugin: 
json files are located in `static/locales` folder.

```
$.i18n.init(
    resGetPath: 'locales/__lng__.json',
    load: 'unspecific',
    fallbackLng: false,
    lng: 'en'
}, function (t)
    $('#i18_title').i18n();
});
```

#### Step 4

After that if you want to change the language you just need to add buttons and fire the i18n.setLng() function.

HTML markup

```
<li>
    <a class="btn btn-sm set_en"><img src="{{"static/img/flags/64/United-States.png"| prepend: site.baseurl }}" height="16px" width="16px"></a>
</li>
<li>
    <a class="btn btn-sm set_cn"><img src="{{"static/img/flags/64/China.png"| prepend: site.baseurl }}" height="16px" width="16px"></a>
</li>
```

Javascript code

```
        $('.set_en').on('click', function (){
            i18n.setLng('en', function(){

                $('#i18_title').i18n();

           });
        });

        $('.set_cn').on('click', function (){
            i18n.setLng('cn', function(){

                $('#i18_title').i18n();

            });
        });
```

Link: [i18next](http://i18next.github.io/i18next/)


### Comment

I use Changyan to realize comment,to configure Changyan, get the appid and conf in <http://changyan.kuaizhan.com/>. Then, in `_config.yml`, edit the changyan value to enable Changyan.

### Put in a Jack's blog Plug

If you want to give credit to the Jack's blog theme with a link to my personal website <http://www.jack003.com>, that'd be awesome. No worries if you don't.

### Web analytics and search engines

I use [Baidu analytics](http://tongji.baidu.com/web/welcome/login) to realize and javascript to realize blog search,the detail you can got to this repo: <https://github.com/androiddevelop/jekyll-search>

### Enjoy

I hope you enjoy using Jack's blog. If you encounter any issues, please feel free to let me know by creating an issue. I'd love to help.

## Upgrading Jack's blog

Jack's blog is always being improved by its users, so sometimes one may need to upgrade.

### Ensure there's an upstream remote

If `git remote -v` doesn't have an upstream listed, you can do the following to add it:

```
git remote add upstream https://github.com/johnotander/pixyll.git
```

### Pull in the latest changes

```
git pull upstream master
```

There may be merge conflicts, so be sure to fix the files that git lists if they occur. That's it!

## Thanks to the following

* [Jekyll](http://jekyllrb.com)
* [Bootstrap](http://www.bootcss.com)
* [jPages](http://luis-almeida.github.io/jPages)
* [i18next](http://i18next.github.io/i18next)
* [pixyll](https://github.com/johnotander)
* [androiddevelop](https://github.com/androiddevelop)

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

