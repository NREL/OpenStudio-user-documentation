#OpenStudio User Documentation


This is the repo for OpenStudio user documentation.  

The documentation is written in Markdown, and uses [MkDocs] (http://www.mkdocs.org/) to compile the markdown files into a static site.  The site is hosted on github-pages at: http://nrel.github.io/OpenStudio-user-documentation/.

##Setup
Install MkDocs by following the direction at [MkDocs] (http://www.mkdocs.org).  You will need python.

Clone this repo locally.  In a terminal window, navigate to the repo directory, and type: 
````
mkdocs serve
````

This will start a server that will let you see what your changes will look like on the site.  Open a browser and go to http://127.0.0.1:8000/ to see your local site.


##Adding and Editing Pages
Edit existing .md files using either markdown or html.  If you need to add a new image, place it in the ````docs/img```` directory.

If you need to add a new page, first decide where it should go in the site structure.  The folders within the docs/ directory mostly correspond to the top nav.  Once you have decided where the page should go, add a reference to it in the  ````mkdocs.yml````  file.

##Deploying

When you are done making changes, commit back to the repo.  

If you want to deploy your changes to the live site, return to the terminal window and type:

````
mkdocs gh-deploy
````
This will generate the static site in the ````site/```` directory and push this directory to the gh-pages branch of the repo, which will update the site.  Do not commit the ````site/```` directory to the master branch, however.
