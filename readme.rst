# python-soap
a python soap Panopto API client that wraps the zeep library for the heavy lifting


Updating dependencies
---------------------
This package has dependencies defined in two places: setup.py and requirements-dev.txt
The **abstract** dependencies defined in setup.py are required for **module dependencies**.
The **abstract** dependencies defined in requirements-dev.txt are only needed for **test and development** dependencies.

The following command will combine both of those abstract dependency files in order to generate the **pinned**
requirements.txt file.  This is what is used by the test systems in order to guarantee a stable testing environment.

.. code:: console
    $ pip-compile --output-file requirements.txt --annotate --header requirements-dev.txt

To update all packages, periodically re-run ``pip-compile --upgrade requirements.txt``.

To update a specific package to the latest or a specific version use the
``--upgrade-package`` or ``-P`` flag:

.. code:: console

    $ pip-compile --upgrade-package requests --output-file requirements.txt --annotate --header requirements-dev.txt

Pushing a new build of the package
----------------------------------

Make sure everything builds

.. code:: console

    tox

If that succeeds, then you can push a source package to artifactory
(This assumes that you've defined our local artifactory as "local" in
~/.pypirc).

.. code:: console
    python setup.py bdist_wheel --universal upload -r local