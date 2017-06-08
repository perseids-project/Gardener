<h1>Gardener Jekyll Theme for Treebank Publications</h1>

This guide should help you self-publish a collection of treebank fixes produced on the Perseids platform with Arethusa, hosting them in a simple Jekyll-based site via GitHub Pages. 

Prerequisites for using this theme include:
    <ul>
      <li>The ability to use the command line on your operating system.</li>
      <li>Basic knowledge of how to use GitHub</li>
      <li>Treebank files produced on Perseids with Arethusa</li>
    </ul>

To publish your own treebank collection, follow the below instructions. (Command line examples are given as they would be executed on Linux-based operating system).


<ol>
  <li>Create your repository
    <ol>
 	<li>Create a GitHub account (if you don’t have one already) and familiarize yourself with how <a href="https://guides.github.com/activities/hello-world/">GitHub works</a>.</li>
 	<li>Fork this repository (https://github.com/perseids-project/Gardener) to your own GitHub account.</li>
        <li>If you like, you can rename the repository in your account.</li>
 	<li>Clone the forked repository to your local environment, so that you can work with it and test it locally.</li>
    </ol>
  </li>
  <li>Install Ruby and Jekyll in your local environment
    <ol>
 	<li>Install <a href="https://www.ruby-lang.org/">Ruby</a> and <a href="https://rubygems.org/">Rubygems</a>.</li>
        <li>Install the Jekyll and Bundler gems: 
	<pre>gem install jekyll bundler</pre>
        </li>
    </ol>
  <li>Configure your site. 
  Edit the <b>_config.yml</b> file to set the things that are specific to your site:
    <ol>
      <li>Set <b>title</b> to the Title you wan to to appear for your site.</li>
      <li>Set <b>email</b> to your email address (if you want to publish it, otherwise set it to be empty)</li>
      <li>Set <b>description</b> to the text you would like to appear on the home page of your site</li>
      <li>Set <b>baseurl</b> to "/" plus the name of your forked repository (this will be '/Gardener' unless you have changed the name of the repository after forking it.). </li>
      <li>Set <b>url</b> to the full Github.io URL for your repository (e.g. 'https://youraccount.github.io/Gardener__'</li>
      <li>Set <b>twitter_username</b> and <b>github_username</b> as appropriate</li>
     </ol>
   </li>
   <li>Load your treebanks into the xml directory<br/>
     The Gardener theme is designed to work with treebank data files as exported directly from Perseids in BagIt archives. These archives can be exported by clicking the little shopping bag icon that appears to the right of your file on the Perseids home screen.  When you unzip the files will be in a base directory named according to the publication id and download date, and within there in a "data" subdirectory.
     <ol>
       <li>Download the bag from Perseids</li>
       <li>Unzip the downloaded bag in the <b>xml</b> subdirectory of your repository.
           <pre>
             cd xml
             unzip /path/to/downloaded/file .
	   </pre>
       </li>
       <li>You should end up with a directory structure that looks like this:
           <pre>
           xml
             perseidspublication_99999_2017-06-08T11:58:10+00:00
               data
                 perseus-grctb.9999.1.xml
           </pre>
       </li>
       <li>There will be other metadata files extracted from the Perseids bagit archives, but you can ignore them.</li>
       <li>Repeat this process for as many files as you want to publish.</li>
     </ol>
   </li>
   <li>Create index files for each treebank. You can do this in a very basic text editor, or in-browser on GitHub. For each treebank file you publish, add a file in the _tbpages directory of your repository. The filename can be whatever you want but for simplicity we recommend a name that is related to the name your treebank file. E.g.
        <pre>
            _tbpages
              9999.1.html
	</pre>
        The contents of the file should adhere to the format described below under "Template Treebank Index Files"
   </li>
   <li>Install dependencies and use Jekyll to build the site
     <ol>
 	<li>Build and test your site locally (see <a href="https://jekyllrb.com/docs/usage/">full instructions</a>):
           <pre>
	   bundle install
           jekyll build
           jekyll serve
	   </pre>
        </li>
 	<li>Once you are satisfied, you can push to GitHub. Because the Gardener theme uses Jekyll extensions, you must push the locally built files to GitHub, rather than having GitHub generate the files dynamically. This means that you must be sure that the <b>docs</b> directory created by the <b>jekyll build</b> command is included in what gets committed and pushed to GitHub.</li>
      </ol>
   </li>
  <li> Setting up GitHub-pages
    <ol>
      <li>Once you have pushed your site to GitHub, you will need to turn on <a href="https://guides.github.com/features/pages/">GitHub Pages</a>. Make sure to identify the <b>docs</b> directory as the source for your site.</li>
    </ol>
  </li>
</ol>


<h1>Template Treebank Index Files</h1>

<p>The benefit of using Gardener is that you do not need to understand basic html in order to create a basic blog for your trees. In order to generate each treebank display page, you will need to create a simple html file for each treebank file. But that file can be almost entirely empty and only needs to have a yaml header.This header contains the important data that the system needs in order to generate the treebank displays, and the list of treebanks on the main page.  
Here is a sample yaml header and a breif explanation of what each element of the header means:</p> 

<p style="text-align: left;">---<br>
layout: tbpage<br>
title: "Plato Apology"<br>
work: "Apology"<br>
author: Plato<br>
editor: Tim Buckingham<br>
locus: 20b-22b.2<br>
pubdir: perseidspublication_99999_2017-06-08T11:58:10+00:00<br>
tbfile: perseus-grctb.1911.1.xml<br>
---</p>


<ul>
<li>Layout: leave this value as tbpage, this determines which page template jekyll will use when it builds the site. For these treebank display pages, you will always want to use tbpage.</li>
<li>Title: this can be whatever you want to call the treebank, it will appear at the top of the page<br>
<li>Work: the title of the original source of the text for your treebank</li>
<li>Author: the author of the Text for your treebank</li>
<li>Editor: the person(s) who annotated the treebank</li>
<li>Locus: the section(s) of the original text for your treebank</li>
<li>Folder: the name of the folder within the xml directory that contains your treebank file. If you followed the above instructions to export a Perseids BagIt archive, it will contain the publication id and date as in the example.</li>
<li>Tbfile: the name of the treebank file you want to associate with this treebank page. The example is the default naming convention for treebank files when they are downloaded from Perseids.</li>
</ul>

<p>
Any additional content that you want to add to the tbpage, you can add below the yaml header. Even unformated text will appear in the final version of the page above the treebank display. <br>
These html files can be written up in any simple text editor. <br>
</p>
<p>
The repository contains one sample publication. Use it as a template for your own tbpage files. 
</p>
