# Instructions to edit Kovri website

## Table of Contents

1. Intro
2. Instructions
  2.1 To change or add design elements (Jekyll)
    2.1.1 Jekyll
    2.1.2 Required Plugins
    2.1.3 GitHub
  2.2 To edit or add pages (Markdown)
    2.2.1 Of GitHub and Markdown
    2.2.2 .html: frontmatter & more
    2.2.3 Writing Your Page
    2.2.4 Multi-language ready
    2.2.5 Navigation (more multi-language)
  2.3 To translate
    2.3.1 Fork that code!
    2.3.2 Humble beginnings
    2.3.3 Translate it!
    2.3.4 Housekeeping
3. Choosing a layout
4. Questions & Contact

## 1. Intro
Hey everyone, I'm rehrar. The kid responsible for making the custom framework and design that is used in both the getmonero.org and getkovri.org websites. If you're reading this you probably want to know how to edit a page or add content, maybe even take content away. Let me be the first to say, thank you so much! The Monero Project is made and run by the community, and you're helping to make it better. 

There are a couple of differences between the Kovri and Monero websites, so I just want to emphasize *you are reading the Kovri website instructions*.

Feel free to skip down to a relevant section if you already know what you need. Also, any help translating this document into another language is greatly appreciated.

If for any reason you have questions or need to contact me, you can find me on the Monero Slack, reddit, and sometimes the various IRC channels using the same name: rehrar. There's a second 'r' after the 'h'. Don't forget. ;)

If you're also feeling generous, a donation for my work on the website and documentation is apprecaited. Although don't forget to donate to getmonero.org also. Both addresses are provided below:

rehrar XMR address: 44LGJKw6Eda72gGDaiVkB9aVq7aYpCHuC1sFFixT8FNB5vLQ1LTXztaMtYvib3QetCddxFGXZvoWDGEBvcghPLSbTaBbFpY

getmonero.org XMR address: 44AFFq5kSiGBoZ4NMDwYtN18obc8AemS33DBLWs3H7otXft3XjrpDtQGv7SqSsaBYBb98uNbr2VBBEt7f2wfn3RVGQBEP3A

## 2. Instructions

Drumroll please...

### 2.1 To change or add design elements (Jekyll)

This section is for those who want to change any of the following elements of the website:
..* Header
..* Navigation
..* Footer
..* Layouts of pages

The navigation automatically updates with added pages assuming the instructions are followed correctly, so if you just want to add a new page, you don't have to worry about that. If you don't want to do any of the above, skip to section 2.2.

#### 2.1.1 Jekyll

Still here? Alright, let's get down to business. The Kovri website is made using a simple, static website generator called [Jekyll](https://jekyllrb.com/). This means that if you want to make big changes to the website code at large, you will need to install Jekyll on your computer. Jekyll runs on Ruby, so you'll need that as well. I'm going to assume that you've ready through Jekyll's documentation so I won't go over Jekyll in depth here.

#### 2.1.2 Required Plugins

The Kovri website uses the following plugins:
..* [Jekyll plugin for multi-language functionality](https://github.com/Anthony-Gaudino/jekyll-multiple-languages-plugin) 

_PLEASE READ ALL DOCUMENTATION ASSOCIATED WITH EACH PLUGIN_

If any further plugins are added to the website over time, this document will be updated with names and links.

#### 2.1.3 GitHub

Secondly, you'll need to fork the [Kovri website from GitHub](https://github.com/anonimal/kovri-site) be willing to work with your own repository. Yeah, that means you kind of have to know how GitHub and version control works too. Don't worry, if you have questions, the Kovri community is really happy to help out.

You can test whether everything is building correctly before you get started. Once the website builds successfully, you've got a working environment ready to go. All that's left is a working knowledge of HTML and CSS, which, unfortunately, is outside the scope of this document.

### 2.2 To edit or add pages (Markdown)
If all you want to do is add or edit a page on the website, well lucky you! You don't have to know a lot of the stuff in section 2.1. There is a couple of things you'll need to be able to do however, so let's get started.

You're still going to need the website files, because you're actually going to be editing a couple other files besides the one you're trying to add. Don't worry though, I'll take you through everything here and if you follow the steps, it'll be working like a charm. 

#### 2.2.1 Of GitHub and Markdown 

Go ahead and fork the Kovri website or download the [files from GitHub](https://github.com/anonimal/kovri-site). Don't worry, you won't need Jekyll or anything on your computer. You should be able to edit the files from within the GitHub website interface.

First things first, you're going to need to know how to use Markdown. It's basically a in-between language that enables people who don't know HTML to just write, and it will be compiled into HTML for you. You can find a great Markdown cheat sheet with examples [here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links). IF you need more help, Google and YouTube are great resources.

_Note:
If you're confused, feel free to click other files in the same directory (folder) that you are in for the step that you are on to see some working examples. Compare them to the instructions and you should understand better._

#### 2.2.2 .html: frontmatter & more

Alright, let's make a page. The first step is to go into the *'doc'* folder at the root of the website. Here you'll see a few pages with the ending *.html*. Click *'Create New File'* and name the file, with a .html at the end. We'll use *kovri-example.html* as an example.

Ok, now here's where we're going to put all of our awesome content, right? Well, not quite. Jekyll requires some front matter at the top of the page which looks like this:

```
---
layout: default
title: titles.faq
permalink: /FAQ
---
```

This is the front matter for faq.html. Let's break this down.
..* layout: Every page needs a layout. For most purposes 'default' will work fine. It's just a single full-width info block like can be seen on the [Kovri home page](https://getkovri.org). Please check out section '3. Choosing a Layout' for more info.
..* title: This is the title of your page. You're not actually going to put a title here, but something that will point to your title in the multi-translation mix. You're going to put the word 'titles', followed by a period, followed by a unique word that describes your page. In the example above, that looks like *titles.faq*. For our example of *kovri-example.html* we can make it *titles.example*. When all else fails, the name of the page works just fine.
..* permalink: This is how your page will be accessed. For example, you can access the Kovri FAQ page by typing [https://getkovri.org/faq](https://getkovri.org/faq). The */faq* at the end is the permalink. Choose a unique word for your page and put a '/' in front of it. For our example, we can choose something like */kovri-example*.

Ok, now that that's taken care of, let's get on to the rest of the page. Let's see what the FAQ page has for the remainder:

```
{% tf faq.md %}
```

Wait, that's it? Yep, that's it. Don't believe me? Click on *faq.html* in the *doc* folder and see for yourself. The front matter, and that single line compose the entire file. What is this saying? Well let's break it down one more time:
..* {%  %}: these brackets at the front and at the end just say that this is code to be run. These are important, be sure to include these.
..* tf: tf stands for translate file. It's saying to find the correct translation of your page and put it here depending on the user's chosen language.
..* faq.md: Here's where you need to do something. You need to choose a unique name again and put it here followed by *.md*. Remember this name. We're going to need it later. For our example, we can put: *kovriexample.md*.

_Note:
If you want to use the same unique name for all of the above variables (title, permalink, and the md filename), that's fine. It just has to be unique to your page throughout the website._

#### 2.2.3 Writing your page

Expecting more? Don't worry, we're not done yet. Get out of the *doc* folder and find the *_il8n* folder. Depending on the number of current languages on the site, there will be any number of folders and files. Unfortunately, there is some busywork here. Not difficult, just a bit time-consuming. Let's start by visiting the *en* folder (stands for English). In here you'll see some files with the same *.md* ending. Remember the unique name you came up with earlier for your .md? We're going to use that here. Click *Create New File* and name it _THE SAME THING_ as your chosen name. In our example, *kovriexample.md*.

Here is where you're going to use your newly acquired markdown skills to make your page. Don't make frontmatter for this page. It will mess things up. Just write your content. I'll wait.

...

...

All done? Great! Save that sucker so you don't lose your work. It should take you to the page on GitHub where it shows what your markdown looks like. If there's changes that need to be made, change them now. Believe me. Triple check everything to make sure it's how you want it. If you don't, don't say I didn't warn you.

#### 2.2.4 Multi-language ready

Now press the *Raw* button on the top right above your work and press *CTRL + A* plus *CTRL + C*. You should now have your page copied to your clipboard. Click the back arrow and go to the next language folder. We'll say it's *es* for Spanish. Click *Create New File* here as well, name it the *SAME THING* (in our case *kovriexample.md*), paste in your page, and save it. Yes, I know it's not in Spanish. It can be translated to Spanish later. The website simply will not build unless every single language folder has a file with the same name, so we're putting placeholder text (which is just our original text) while we wait for some great translator to come along and translate it.

Yes, your sinking feeling is correct. You're going to have to do the above steps for all of the language folders. When you're done, it'd be nice if you quickly went through the language folders and make sure each one has your file. In our example, make sure each folder has *kovriexample.md*. When you're sure, it's time for the next step.

Alright, next up, in the *_il8n* folder there are not just language folders, but a couple *.yml* files as well for each language. Here we go again. Open up the first, we'll say *en.yml* and find the section at the bottom labeled *titles*. Make a new line underneath the existing page titles and indent it two spaces (so it's flush with the others). The unique name you made in the front matter for the *title* section (in our example *titles.example*) just put the word AFTER *titles* on the line followed by a colon and a space (for our example, we would simply put *example: *). Yes, it has to have the colon and one space. Jekyll can be very picky sometimes. After that, type in the desired title for your page. I'll choose 'Kovri Example Page' for my example.

You guessed it, go ahead and do the same thing for the other language .yml files as well. Hopefully someone will come translate those.

#### 2.2.5 Navigation (more multi-language)

Believe it or not, we're almost done. Just one more thing to do. Navigate to the root of the filesystem and find the *_data* folder. There's only one file in there: *navigation.yml*. Go ahead and open it up. You should see a set of lists starting with the same short codes of the languages we dealt with earlier. This step places your page in the navigation somewhere. You need to decide where it best fits and place it there.

_Note:
We all like to think our content is worthy of being a top level navigation item (or one of the main navigation buttons). Unless you're very sure, I would discuss with the website maintainer to see if your page needs to be in the top level navigation. If not, please don't put it there._

Let's say that kovri-example.html is a page that talks about how to get Kovri up and going for a new user. It'd probably best go under the 'Get Started' section. Find *title: Get Started*, go underneath the *subfolderitems* and copy the code from one dash to the next, paste it at the end but before the next *title:*

```
- page: General
  url: contributing.html

```
and change it to the name and url of your new page that you. Let's break it down:
..* page: this is how your page will appear on the navigation bar or in a dropdown. For our example, we'll name change it to *Kovri Example*
..* url: This is the url that you made at the very beginning of this process. For us it's *kovri-example.html*.

```
- page: Kovri Example
  url: kovri-example.html
```

*MAKE SURE THE DASHES AND START OF THE LINES ARE FLUSH WITH THE OTHERS!* Is this formatting a bit stupid? Yes, but Jekyll doesn't like to build a lot of times if these are even a space off. Seriously. Make it flush.

Once more, copy your work for the remainder of the languages. Somebody will come change the translations to what they should be.

Great job! You just made a page and contributed to Kovri. Double check all of your work and then submit a pull request to get your work merged into the site.

### 2.3 To translate
If you just want to help with translating pages that are already in existence to another language, it'd still be a good idea to look over the section above (2.2 To edit or add pages (Markdown)) and follow the steps as if you were making a page to get a feel for the filesystem and process. But don't worry, I'll provide instructions below.

Let's say that we're going to translate the [Building Page](https://getkovri.org/building.html) into Spanish.

#### 2.3.1 Fork that Code!

The first step is to get the website files. You can do everything I'm going to show you from within the GitHub website, so you don't need any programs on your computer. Fork the Kovri website or download the [files](https://github.com/anonimal/kovri-site). 

For this, you're going to need to know how to use Markdown. It's basically a in-between language that enables people who don't know HTML to just write, and it will be compiled into HTML for you. You can find a great Markdown cheat sheet with examples [here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links). If you need more help, Google and YouTube are great resources.

#### 2.3.2 Humble beginnings

Let's begin by going to the *doc* folder and finding the page we want to translate, in our case *building.html*. Open the file and take note of the content within the {%  %}'s.

```
{% tf building.md %}
```

for our example, it's *building.md*.

Keep note of this filename and navigate to the *_i18n* folder. You'll see a number of folders and files here depending on the languages currently supported. 

You're  going to need to open up the original file from the correct language folder (which will probably be English or the *en* folder) in another tab or window so you can translate, although every person's translation environment is different. Do it your way. :) Find the file with the same name that you found earlier (in our example: *building.md*) and open it up.

Keep that tab or window open and open another one. Find the folder that represents your language (don't know which? contact me and I'll let you know) and open it. Find the file with the same name as the other one (*building.md* in our example) and open it.

#### 2.3.3 Translate it!

You can leave all of the markdown formatting intact and simply change the words after or between it. So for example you can take this text:

```
## Friend
```

and turn it to this

```
## Amigo
```

or this:

```
*friend*
```
into this
```
*amigo*
```

Again, this will go much easier if you're able to recognize the markdown formatting so you can leave it.

Alright, now it's your time to shine. Get translating!

#### 2.3.4 Housekeeping

Just a couple more things! The title of the page (the centered copy that opens the page after the navigation) is not changed yet. You change that by going back to the *_i18n* folder and finding the .yml file that stands for your language. In this case, *es.yml*. Open it and find the section labeled *titles*. Find the name of the page you're working on (in our case *building*) and change the text after it to the translated version. Save and close the file. Voila, title changed.

Navigate to the root folder and enter the folder labeled *_data*. You should see a file called *navigation.yml*. Open it and you should see a set of lists. Find the list with the shortcode for the language you've been working with and search for the URL of the page you're translating (in our example *building.html*) within the language list. Right above the url should be a *page:*. Translate the text the *page:*. This changes how the page will appear in the site navigation in this particular language.

And with that, you're all done! Your chosen page is now translated. Thank you for helping to expand Kovri to a wider, global audience.

## 3. Choosing a Layout
Here, the various layouts are listed that you can take advantage of, as well as a description of what they accomplish. There's also the ability to make your own layouts, but for that you'll need to follow the instructions of section 2.1 To change or add design elements.

Depending on the version of this document you're viewing, there may be many layouts or as few as one. As layouts are added to the site, this documentation will be updated.

### 3.1 Layouts
Currently, the following layouts are available to choose from:
  * default: this layout is a single full-width info block as seen in [the Kovri homepage](https://getkovri.org). Nothing fancy. Should work for the majority of text-based pages.
  
_More layouts to be added later_

## Questions & Contact
That should be everything that you need. There will be an assets document released as well for the framework at large that will show how to make your own layouts by simply copy and pasting out of the document. This instructions document will be updated with the link when it is released.

Once again, I am rehrar. Feel free to contact me with any questions regarding translation, page-creation, content, markdown, jekyll, html/css, or anything else.

Thank you for being a part of, and contributing to, the Monero community. This coin is all the stronger for your help.