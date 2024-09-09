# Installing Workshop Dependencies
## Prerequisites
Windows, MacOS, and Linux should all work.

To use the software in this tutorial, you must have Python installed. The tutorials are compatible with Python version >= 3.9. You should have a current version of pip (>= 23) and setuptools (>= 68)

We will use the command `python3` to invoke Python on Linux, but on Windows the appropriate command may be `python`. You should find out what the appropriate command is for Python on your system.

Both pip and setuptools can be updated using pip itself with `python3 -m pip install --upgrade pip setuptools`.

In the tutorials, we use some software which is available from PyPI but is not available as a conda package. If you prefer to use conda, you will have to install some things in a conda environment
using a conda-managed version of pip.

In order to avoid dependency conflicts with other Python packages on your device,
including packages managed by the system package manager rather than pip or conda, you should create a virtual environment to install
all Python packages that will be used in the workshop. Start by navigating to the directory in which you plan to work, and follow the instructions appropriate for your package manager.

## Requirements
The main packages we focus on in this workshop are
- pynapple, a light-weight python library for neurophysiological data analysis
- NeMoS, a statistical modeling framework optimized for systems neuroscience
- CAJAL, a tool for analyzing cell morphology with methods from optimal transport theory
- NAVis, a neuron visualization package
- Scanpy, a Python package for the analysis of single-cell gene expression data

In addition to these core tools, we will rely on some generalities:
- Jupyter, an interactive environment for evaluating Python code and plotting graphs
- ipywidgets, which extends the functionality of Jupyter (e.g., progress bars)
- leidenalg, an implementation of the Leiden clustering algorithm
- umap-learn, which is useful for visualizing the clustering structure of high-dimensional data
- Pandas, a dataframe library for manipulating and filtering tabular data
- Plotly, a rich visualization library

## Pip
Pip is the standard package manager for Python.

```
python3 -m venv ./neuro_workshop
```

After creating the virtual environment, you should activate it, which sets certain environment variables and path variables to 
ensure that Python commands and modules refer to code in the ./neuro_workshop folder. In Windows Powershell, the command is `.\neuro_workshop\Scripts\activate.ps1`.
In Linux, the command is `source ./neuro_workshop/bin/activate`. The section "How venvs work" of the [Python venv documentation](https://docs.python.org/3/library/venv.html)
contains a table containing the appropriate command indexed by operating system and shell. You can deactivate the virtual environment with the command `deactivate`.

Before running the command, please check the left hand side of your terminal prompt to ensure that the virtual environment is activated.
```
python3 -m pip install jupyterlab ipywidgets cajal scanpy leidenalg navis umap-learn pandas plotly pynapple nemos matplotlib requests
```

## Conda
Conda is a package manager commonly used in data science and bioinformatics. We do not provide a conda package for our tools; these instructions discuss how to use conda to create a sandbox for pip.
Instructions for workin with virtual environments in conda can be found [here](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html).
You can open a conda terminal from the Windows start menu by launching the program "Anaconda Powershell Prompt."

Create and activate a virtual environment with
```
conda create --prefix ./neuro_workshop python=3.11
conda activate ./neuro_workshop
```

Install dependencies as follows:
```
conda config --append channels conda-forge
conda install numpy scipy jupyterlab ipywidgets scanpy leidenalg umap-learn pandas plotly 
```

Now run
```
pip install cajal navis pynnapple nemos
```
and pip should install the relevant dependencies into the ./neuro_workshop directory you have just created.

## Building CAJAL from source
We strongly recommend using pip to install precompiled wheels from the Python Packaging Index, PyPI.

If you prefer to build CAJAL from source, some dependencies are required.
- You need a C++ compiler. On Windows, we recommend Microsoft Visual C++ 14.0 or greater, which can be installed via the [Microsoft C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/). On Linux, you can use g++. 
- You should ensure that all necessary header files for compiling C plugins for Python are visible to the C++ compiler. On Ubuntu, this may require the package python3.x-dev; on Windows you should modify the installation of Visual Studio installer as follows:
  Open "Visual Studio Installer." Select "Modify". Select "Workloads". Check the "Python Development" box. On the right, check "Python native development tools" 

Once these dependencies are installed, you should create and activate a virtual environment, following the instructions as for Pip or Conda above. Then run:
```
python3 -m pip install git+https://github.com/CamaraLab/CAJAL.git
```
and install the other workshop requirements as mentioned above.