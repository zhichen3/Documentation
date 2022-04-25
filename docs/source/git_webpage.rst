***************
Github Webpage
***************

Creating gh-pages
==================
Go to the repository of choice and do the following command:

.. prompt:: bash

   git checkout --orphan gh-pages
   git reset --hard
   git commit --allow-empty -m "Initializing gh-pages"
   touch .nojekyll
   git add .
   git commit -m "update"
   git push origin gh-pages
   git checkout main

Doxygen Configuration
======================
Use Doxygen for documentatng C++ code.

Creating Doxyfile using:

.. prompt:: bash

   doxygen -g

Change Settings in Doxyfile:

* Change ``PROJECT_NAME``
* ``OUTPUT_DIRECTORY = docs``
* ``USE_MDFILE_AS_MAINPAGE = README.md``
* ``GENERATE_LATEX = NO``
* include ``*.H`` in ``FILE_PATTERNS``


Then include a yaml file for github action:

.. code:: yaml

   name: github pages

   on:
     push:
       branches:
         - main

   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v3

         - name: Install pandoc and doxygen
           run: |
             sudo apt install pandoc doxygen

         - name: Setup python
           uses: actions/setup-python@v3
           with:
             python-version: '3.9'

         - name: Install dependencies
           run: python3 -m pip install -r ./requirements.txt

         - name: Build Doxygen
           run: |
                mkdir -p docs
                doxygen Doxyfile

         - name: Deploy
           uses: peaceiris/actions-gh-pages@v3
           with:
             github_token: ${{ secrets.GITHUB_TOKEN }}
             publish_dir: ./docs
             keep_files: true

.. tip::

   Inlucde a requirements.txt to include sphinx packages

   .. code::

      sphinx
      sphinx_rtd_theme
      breathe


.. tip::

   Include a hyperlink to this webpage, which is located in ``html/index.html``


SPHINX
=======

Create sphinx for documentary.

Go to ``docs/`` and do

.. prompt:: bash

   sphinx-quickstart
   rm make.bat

There are two important files, ``conf.py`` and ``index.rst`` inside ``source/`` directory.

Configure conf.py with a sample template below:

.. literalinclude:: ../conf.py
   :language: c++
   :caption: ``conf.py``

