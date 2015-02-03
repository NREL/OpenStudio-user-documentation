#OpenStudio User Documentation


This is the repo for OpenStudio user documentation.  

The documentation is written in Markdown, and uses [MkDocs] (http://www.mkdocs.org/) to compile the markdown files into a static site.  The site is hosted on github-pages at: http://nrel.github.io/OpenStudio-user-documentation/.

##Setup
###Mac
Install MkDocs by following the direction at [MkDocs](http://www.mkdocs.org).  You will need python.

To update your MkDocs version:
```python
	sudo pip install -U mkdocs
```

###Windows
Getting mkdocs to work on Windows is very particular.  We recommend uninstalling python and deleting the install directory before following these steps.  If you don't, it probably won't work.  We tried many different ways to do this, and starting from scratch and following these steps is the only thing we could get to work.


1. Install [Python 2.7.8](https://www.python.org/ftp/python/2.7.8/python-2.7.8.msi)
2. Add `C:\Python27` and `C:\Python27\Scripts` to your PATH
3. Download [Pip](https://bootstrap.pypa.io/get-pip.py)
4. Open a command prompt where you saved Pip (get-pip.py) and run: `python get-pip.py`
5. Download [mkdocs v0.11.1 source code](https://github.com/tomchristie/mkdocs/archive/0.11.1.zip)
6. Extract mkdocs source code
7. Open a command prompt where you extracted mkdocs and run: `python setup.py install`
8. Open `C:\Python27\Lib\site-packages\mkdocs-0.11.1-py2.7.egg\mkdocs\gh_deploy.py` and modify line 13 to contain the following:

    ```python
    subprocess.check_call(['python', 'C:/Python27/Scripts/ghp-import', '-p', config['site_dir']])
    ```


##Run
Clone this repo locally.  In a terminal window, navigate to the repo directory, and type: 
```shell
mkdocs serve
```

This will start a server that will let you see what your changes will look like on the site.  Open a browser and go to http://127.0.0.1:8000/ to see your local site.


##Adding and Editing Pages
Edit existing .md files using either markdown or html.  If you need to add a new image, place it in the `docs/img` directory.

If you need to add a new page, first decide where it should go in the site structure.  The folders within the docs/ directory mostly correspond to the top nav.  Once you have decided where the page should go, add a reference to it in the  `mkdocs.yml`  file.

##Deploying

When you are done making changes, test your deployment first and then commit back to the repo.  

To test, first delete the site directory if it already exists, and then build the site and open index.html
```shell
rm -rf site
mkdocs build
```

If you are ready to deploy your changes to the live site, return to the terminal window and type:

```shell
mkdocs gh-deploy
```
This will generate the static site in the `site/` directory and push this directory to the gh-pages branch of the repo, which will update the site.  Do not commit the `site/` directory to the master branch, however.
