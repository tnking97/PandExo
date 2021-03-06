Windows Installing Guide for PandExo
====================================

Created by J. N. van Haastere (Physics and Astronomy Bachelorstudent)
Univesity of Amsterdam and VU University Amsterdam

Step 1 
``````
You may want to uninstall older python versions to prevent troubles along the way. 

Step 2
``````
`Download most recent Anaconda version <https://www.anaconda.com/download/>`_ (tested with Python 3.6.4 64 bit) 
    
Step 3
``````
Install Anaconda as main python and add to path environment

.. note::
    If succesfully installed you can open CMD and type `>>python` and `>>quit()` to check version

Step 4
``````
`Install Build Tools for Visual Studio 2017 <https://www.visualstudio.com/downloads/#build-tools-for-visual-studio-2017>`_.
    
Step 5
``````
`Follow PandExo Installation guide in getting files <https://natashabatalha.github.io/PandExo/installation.html>`_

- get pandeia_data      (pandeia_data-1.2.tar.gz)
- get pysynphot_data        (synphot5.tar.gz)
- get PandExo github folder (pandexo-master.zip)

Step 6
``````
Open pandexo.sh in your favorite text editor (eg. Notepad++) and read through installation steps. Below we will follow these steps but with Windows commands.


Step 7: Setting Reference Data
``````````````````````````````
Using an achiver (eg. Winrar, 7Zip) extract Pandeia and Pysynphot data in two seperate folders.

.. code-block:: bash

    C:/Users/USERNAME/pandeia_data
    C:/Users/USERNAME/pysynphot_data

Check the variable names

.. code-block:: bash

    echo 'export VARIABLE_NAME = ".."'


In case nothing changes these should be `PYSYN_CDBS` & `pandeia_refdata`

Set these in Windows environment variables / registry using SETX. Open CMD or Anaconda Prompt and run:   

.. code-block:: bash

    SETX PYSYN_CDBS 'C:/Users/USERNAME/pysynphot_data'
    SETX pandeia_refdata 'C:/Users/USERNAME/pysynphot_data'

You can check this step by opening a new CMD and run > SET

Step 7: Installing needed Packages
``````````````````````````````````
Add conda channel, in CMD:

.. code-block:: bash

    conda config --add channels http://ssb.stsci.edu/astroconda

Check needed packages, at the moment:

.. code-block:: bash 

    numpy synphot joblib scipy astropy==2.0.2 pyfftw pysynphot photutils sphinx=1.5.6 bokeh=0.12.6

All but `Pyfftw` can be installed using:

.. code-block:: bash

    conda install PACKAGE

or

.. code-block:: bash

    pip install PACKAGE

If they fail check in the error if you are missing a certain .dll or look online.

For `Pyfftw` get a prebuiled wheel from `here <https://bintray.com/hgomersall/generic/PyFFTW-development-builds/view#files>`_.

Get a matching cp36-cp36 for your python version.
For Python 3.6.4 64-bit I used:

- `pyFFTW-0.10.5.dev0+d45d7fe-cp36-cp36m-win_amd64.whl`

Navigate to download folder and install

.. code-block:: bash

    cd 'C:\Users\USERNAME\Downloads'
    pip install pyFFTW-0.10.5.dev0+d45d7fe-cp36-cp36m-win_amd64.whl

With your fingers crossed, install PandExo Engine

.. code-block:: bash

    pip install pandexo.engine

Probabily fail, look what I/you missed and try again. `Troubleshooting here <https://natashabatalha.github.io/PandExo/installation.html#troubleshooting-common-errors>`_.

Step 8: Run Test
````````````````
Navigate to your pandexo-master and run the run_test. Check in the `installation <https://natashabatalha.github.io/PandExo/installation.html#pandexo-startup-bash-script>`_ guide on the exact expected output.

.. code-block:: bash 

    cd '...'
    python run_test.py

Congrats on being persevering/stubborn enough to get it on to work on Windows!
There are some test Jupyter files to try out in `pandexo-master/notebooks`




