
Python Project *sphinx-pytype-substitution*
-------------------------------------------

|codeship|_ |readthedocs|_ |license|_ |github_version|_ |pip_version|_
|py_version|_ |pypi_downloads|_


.. |codeship| image:: https://img.shields.io/codeship/452428/master.svg
.. _codeship: https://codeship.com//projects/452428

.. |readthedocs| image:: https://img.shields.io/readthedocs/sphinx-pytype-substitution
.. _readthedocs: https://sphinx-pytype-substitution.readthedocs.io/en/latest/intro.html

.. |license| image:: https://img.shields.io/github/license/sonntagsgesicht/sphinx-pytype-substitution
.. _license: https://github.com/sonntagsgesicht/sphinx-pytype-substitution/raw/master/LICENSE

.. |github_version| image:: https://img.shields.io/github/release/sonntagsgesicht/sphinx-pytype-substitution?label=github
.. _github_version: https://github.com/sonntagsgesicht/sphinx-pytype-substitution/releases

.. |pip_version| image:: https://img.shields.io/pypi/v/sphinx-pytype-substitution
.. _pip_version: https://pypi.org/project/sphinx-pytype-substitution/

.. |py_version| image:: https://img.shields.io/pypi/pyversions/sphinx-pytype-substitution
.. _py_version: https://pypi.org/project/sphinx-pytype-substitution/

.. |pypi_frequency| image:: https://img.shields.io/pypi/dm/sphinx-pytype-substitution
.. _pypi_frequency: https://pypi.org/project/sphinx-pytype-substitution/

.. |pypi_downloads| image:: https://pepy.tech/badge/sphinx-pytype-substitution
.. _pypi_downloads: https://pypi.org/project/sphinx-pytype-substitution/


Introduction
------------

:code:`sphinx-pytype-substitution` generates
`restructuredtext substitutions <https://docutils.sourceforge.io/docs/ref/rst/restructuredtext.html#substitution-references>`_
for
`python cross references <https://www.sphinx-doc.org/en/master/usage/restructuredtext/domains.html#python-roles>`_.

Once added to the
`extensions list <https://www.sphinx-doc.org/en/master/usage/configuration.html#confval-extensions>`_
of the
`Sphinx <https://www.sphinx-doc.org>`_
`configuration <https://www.sphinx-doc.org/en/master/usage/configuration.html#module-conf>`_
file :code:`conf.py`
it adds short and handy substitutions for
`modules <https://docs.python.org/3/tutorial/modules.html#modules>`_
and
`classes <https://docs.python.org/3/reference/compound_stmts.html#class-definitions>`_.

So, on one side it becomes easy to add cross references to some
api documentation in the project. And on the other side these references
are still easy readable, even if the text is displayed directly
(as it happens on `GitHub.com <https://github.com/sonntagsgesicht/sphinx_pytype_substitution>`_
or on `PyPi.org <https://pypi.org/project/sphinx-pytype-substitution/>`_).


Install
-------

The latest stable version can always be installed or updated via pip:

.. code-block:: bash

    $ pip install sphinx-pytype-substitution


Usage
-----

Once available add the extension to then extensions list in :code:`config.py`

.. code-block:: python

    # Add any Sphinx extension module names here, as strings. They can be
    # extensions coming with Sphinx (named 'sphinx.ext.*') or your custom
    # ones.
    extensions = [
        'sphinx_pytype_substitution',
        'sphinx_rtd_theme',
        'sphinx.ext.autodoc',
        'sphinx.ext.autosummary',
        'sphinx.ext.doctest',
        'sphinx.ext.mathjax',
        'sphinx.ext.viewcode',
        'sphinx.ext.napoleon'
    ]

And add the modules or classes to reference to as

.. code-block:: python

    # -- Config for pytype_substitution extension ------------------------------

    pytype_substitutions = pkg,  # package, module or class to reference to


Additional options let select specific references

.. code-block:: python

    pytype_match_pattern = ''  # regex to filter entities to ref to
    pytype_exclude_pattern = ''  # regex to exclude entities to ref to

and decide if the substitution should have *short* or *full* format, i.e.

.. code-block:: python

    pytype_short_ref = True  # drop module from reference (if it does not conflict)

for :code:`|date()|` rather than :code:`|datetime.date()|`.
Note, sometimes the defining module matters as for :code:`|open()|` vs
:code:`|gzip.open()|`.

During initialisation process of Sphinx the list of substitutions is generated
and added to
`rst_epilog <https://www.sphinx-doc.org/en/master/usage/configuration.html#confval-rst_epilog>`_.

So the substitutions are available for every page.


To see which substitutions are added add

.. code-block:: python

    pytype_show = True  # print out all pytype_substitutions


License
-------

Code and documentation are available according to the license (see LICENSE file in repository).
