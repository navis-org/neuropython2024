# Installing CAJAL

## Prerequisites
Windows, MacOS, and Linux should all work.

To use `CAJAL`, you must have Python installed. CAJAL is compatible with Python version >= 3.9. You should have a current version of `pip` (>= 23) and `setuptools` (>= 68).

We will use the command `python3` to invoke Python on Linux, but on Windows the appropriate command may be `python`. You should find out what the appropriate command is for Python on your system.

Both `pip` and `setuptools` can be updated using `pip` itself with `python3 -m pip install --upgrade pip setuptools`.

It is possible to install `CAJAL` either via pip or from source. `CAJAL` is not available as a conda package, but one can install `CAJAL` in a conda environment using a conda-managed version of `pip`.

We strongly recommend using `pip` to install precompiled wheels from the Python Packaging Index, PyPI.

In order to avoid dependency conflicts with other Python packages on your device,
including packages managed by the system package manager rather than `pip` or conda, you should create a virtual environment to install
all Python packages that will be used in the workshop. Start by navigating to the directory in which you plan to work, and follow the instructions appropriate for your package manager.

## Requirements
In addition to `CAJAL`, we will use the following tools in the workshop in conjunction with `CAJAL`
- Jupyter, an interactive environment for evaluating Python code and plotting graphs
- Scanpy, a Python package for the analysis of single-cell gene expression data
- Navis, a neuron visualization package
- umap-learn, which is useful for visualizing the clustering structure of high-dimensional data
- Pandas, a dataframe library for manipulating and filtering tabular data

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
python3 -m pip install jupyterlab cajal scanpy navis umap-learn pandas
```
## Conda
Conda is a package manager commonly used in data science and bioinformatics. We do not provide a conda package for CAJAL; these instructions discuss how to use conda to call pip.
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
conda install numpy scipy jupyterlab scanpy umap-learn pandas pip
```

Now run
```
pip install cajal navis
```
and pip should install cajal and navis into the ./neuro_workshop directory you have just created.

## From source
To build CAJAL from the source on Github, some dependencies are required.
- You need a C++ compiler. On Windows, we recommend Microsoft Visual C++ 14.0 or greater, which can be installed via the [Microsoft C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/). On Linux, you can use g++.
- You should ensure that all necessary header files for compiling C plugins for Python are visible to the C++ compiler. On Ubuntu, this may require the package python3.x-dev; on Windows you should modify the installation of Visual Studio installer as follows:
  Open "Visual Studio Installer." Select "Modify". Select "Workloads". Check the "Python Development" box. On the right, check "Python native development tools"

Once these dependencies are installed, you should create and activate a virtual environment, following the instructions as for Pip or Conda above. Then run:
```
python3 -m pip install git+https://github.com/CamaraLab/CAJAL.git
```
and install the other workshop requirements as mentioned above.