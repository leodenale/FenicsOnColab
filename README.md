# FenicsOnColab - RUN FENICS ONLINE WITH GOOGLE COLAB 
FINITE ELEMENT ANALYSIS, PYTHON

Reference Article from DHIRENDRA on APRIL 12, 2019:
https://learnsharewithdp.wordpress.com/2019/04/12/run-fenics-on-google-colab/

You can install fenics using

  !apt-get install fenics

But when you try to execute a c++ expression, it does not compile and give the following error,

  RuntimeError: In instant.recompile: The module did not compile with command 'make VERBOSE=1', see '/root/.cache/instant/python2.7/error/dolfin_34ef699da990d9ef4c0fba90db5b123d8422ce12/compile.log'

So, use the following code to configure the fenics on google colab,

  https://colab.research.google.com/drive/1jgGpawb7z0LtjkshhJGJpQUvaWgSmrd8

Just open the above note book on google colab and execute it.

The same code is given below.

  from google.colab import files

  import platform, sys
  python_version=platform.python_version()
  from distutils.version import LooseVersion, StrictVersion

  if ( LooseVersion(python_version) < LooseVersion("3.0.0")):
      print("Python3 is needed!");
      print("How to fix: Runtime/Change_runtime_type/Python 3");
      sys.exit()
  try:
      from dolfin import *; from mshr import *
  except ImportError as e:
      !apt-get install -y -qq software-properties-common python-software-properties module-init-tools
      !add-apt-repository -y ppa:fenics-packages/fenics
      !apt-get update -qq
      !apt install -y --no-install-recommends fenics
      from dolfin import *; from mshr import *

  import matplotlib.pyplot as plt;
  from IPython.display import clear_output, display; import time; import dolfin.common.plotting as fenicsplot 
  import time

  import os, sys, shutil

  dolfin_version = dolfin.__version__
  print ('dolfin version:', dolfin_version)

  !rm -rf * # clean up all files
  # Useful commands
  # Remove an empty folder      : os.rmdir("my_results")
  # Remove a folder with files  : shutil.rmtree("results")
  # Make a folder               : os.mkdir("my_results")
  # Runtime/Change_runtime_type/Python3
