This is the www.docker.io website repository
==============================================

It intends to be small, simple and straightforward.

Builds on
----------

* Django 1.5
* Twitter Bootstrap
* Includes tracking options such as from Google Analytics and Intercom.io


Making simple changes
---------------------

This project uses a simplified Django structure, and has the notable feature that all major text contained on this
 website can be maintained by changing the markdown files contained in /_pages/. There is a good chance this will
 be the only part you need to touch.

Files which can be easily be edited are in the _pages directory and have the .md extension.


Simple installation
-------------------

* Clone this repository
* ``pip install -r requirements.txt``
* run ``./local_setup.sh`` to setup everything related to the database.
* Done!

To preview the website run: `` ./manage.py runserver``. It will pick the local settings by default, which are
based on a local mysqlite database. Please note the tweets are now cached in the Database.

To load some data into the news, team page and events
``python manage.py loaddata base/migrations/[datafiles]``


Secrets
-------

Because this repository is in a public repository, we keep our secrets in environment variables. If you do not
set these keys, running the app might fail.

Most notable:

* SECRET_KEY
* MAILCHIMP_API_KEY


About the .md files
--------------------

Using markdown-formatted text allows separation of content (tekst) and markup (html). Depending on your setup
you might want to setup your editor to show the content with either markdown highlighting or jinja shortcuts.


Building CSS from LESS
-----------------------
We build our css from less, and we (heavily) customize bootstrap. The goal is to always have a working .css file
in the repository, so when you check it out you should not need to build the css. If, however you want to make
changes to it:

* Make changes to main.less (preferred over changing bootstrap's .less files
* Compile this using your favorite tool like recess or LiveReload

If you do make changes to the Bootstrap variables which should be reflected in the bootstrap-custom
* Find the makefile in the sources dir
* In that directory run npm install to install the required build libraries
* Run 'make docker-css' to compile the styles to bootsrap-custom

OR, if it mysteriously fails

lessc sources/less/bootstrap.less > bootstrap-custom.css

