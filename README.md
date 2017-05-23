<h1>Gardener Treebanking Self-publicaiton Platform</h1>



This guide should help you self-publish a collection of treebanks, and host them in a simple Jekyll-based blog via GitHub Pages. 

This guide is written so that anyone should be able to host a small site to display their treebanks. All we require is that you have a basic knowledge of how to use GitHub, and control over your own treebanks.

To publish your own treebank collection, follow the below instructions. 


<ol>
 	<li>fork the GardenerTheme repository
<ol>
 	<li>Create a GitHub account (if you don’t have one already) and familiarize yourself with how <a href="https://guides.github.com/activities/hello-world/">GitHub works</a></li>
 	<li>Fork the GardenerTheme, this repository will be where you will build your blog</li>
 	<li>Clone the repository to your machine, so that you can work with it and test it locally</li>
</ol>
</li>
 	<li>Set up <a href="https://jekyllrb.com/docs/quickstart/">Jekyll</a> on your machine. 
<ol>
 	<li>Requires <a href="https://www.ruby-lang.org/">Ruby</a> and <a href="https://rubygems.org/">Rubygems</a></li>
 	<li>Follow the <a href="https://jekyllrb.com/docs/quickstart/">instructions</a> in the Jekyll documentation to create your own blog</li>
	<li> when initiating a new blog with jekyll, you will need to use the command <code>jekyll new . --force</code> this will allow you to make your blog in the same directory as your original repository</li>
	<li>Initiating a new blog will pregenerate a few files and add them to your repository</li>
  <li>Some of the parts of the GardenerTheme are not complete files by themselves, but require you to edit the pregenerated files in the default blog.</li>
	<li>add "_site.asset-cache" to the .gitignore file</li>
	<li>Change the name of "Gemfile-add-ons" to "Gemfile" and delete the pregenerated Gemfile.</li>
	<li> attach the partial config.yml file that is part of the theme, to the default config file. Delete the partial config.yml file after you copy over the content</li>
	<li>add your sites baseurl and url to the config file. The baseurl should be "/Your-Repository"</li>
	
</ol>
</li>
 	<li>Load your treebanks into the xml directory
<ol>
 	<li>Structure the directory correctly, and name your files correctly (see below instructions)</li>
 	<li>Create the tb.html files for each treebank, you can do this in a very basic text editor, or in-browser on GitHub (see below instructions)</li>
 	<li>Edit your main page via the index.html file</li>
</ol>
</li>
 	<li>Use Jekyll to build the site
<ol>
 	<li>You can serve your blog locally to test it out by following<a href="https://jekyllrb.com/docs/usage/"> these instructions</a></li>
 	<li>Once you are satisfied, you can push to GitHub. </li>
</ol>
</li>
<li> Setting up GitHub-pages
<ol>
<li>Once you have pushed your site to GitHub, you will need to turn on <a href="https://guides.github.com/features/pages/">GitHub Pages</a></li>
</ol>


<h1>Setting Up Your Treebank Publications</h1>

<p>The benefit of using Gardener is that you do not need to understand basic html in order to create a basic blog for your trees. In order to generate each treebank display page, you will need to create a simple html file for each treebank file. But that file can be almost entirely empty and only needs to have a yaml header.This header contains the important data that the system needs in order to generate the treebank displays, and the list of treebanks on the main page.  
Here is a sample yaml header and a breif explanation of what each element of the header means:</p> 

<p style="text-align: left;">---<br>
layout: tbpage<br>
title: "Plato Apology"<br>
work: "Apology"<br>
author: Plato<br>
editor: Tim Buckingham<br>
tblang: Greek<br>
locus: 20b-22b.2<br>
folder: 1911<br>
tbfile: grctb.1911.1.tb.xml<br>
---</p>


<ul>
<li>Layout: leave this value as tbpage, this determines which page template jekyll will use when it builds the site. For these treebank display pages, you will always want to use tbpage.</li>
<li>Title: this can be whatever you want to call the treebank, it will appear at the top of the page<br>
<li>Work: the title of the original source of the text for your treebank</li>
<li>Author: the author of the Text for your treebank</li>
<li>Editor: the person who annotated the treebank</li>
<li>Tblang: this will determine the main language directory the system will look in for the treebank file. The values “Greek” and “Latin” are case sensitive. </li>
<li>Locus: the section of the original text for your treebank</li>
<li>Folder: the name of the folder within the language directory that contains your treebank file.</li>
<li>Tbfile: the name of the treebank file you want to associate with this treebank page. The example is the default naming convention for treebank files when they are downloaded from Perseids.</li>
</ul>

<p>
These html files are named after their original treebank file, although with a different file extension. The above yaml header is named “grctb.1911.1.tb.html” <br>
Any additional content that you want to add to the tbpage, you can add below the yaml header. Even unformated text will appear in the final version of the page above the treebank display. <br>
These html files can be written up in any simple text editor. <br>
</p>
<p>
The default directory structure divides the treebanks by language, and then into categories based on the name of the document. 
Currently we only support this kind of structure, and only three specific language categories, grctb for Ancient Greek treebanks, lattb for Latin treebanks, and misctb for all other language groups. Right now there are two sample trees (one for lattb and one for grctb) as well as two sample tbpages (for those two trees). Use them as a template for your own tbpage files. 
</p>
