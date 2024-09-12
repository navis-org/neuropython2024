# :fontawesome-solid-computer: Preparations

## Setting up Python

The workshop will consist of a mix of introductory talks for the individual Python packages and a number of interactive coding sessions - see the [Schedule](schedule.md) for details.

You are welcome to just cruise :sailboat: along but to make the most of it you will probably want to follow the coding and participate in the exercises on your own machine.

In general, we expect you to have at least basic familiarty with Python including the standard data science libraries such as [`numpy`](https://numpy.org/doc/stable/index.html) and
[`pandas`](https://pandas.pydata.org/).

Most of the workshop will be using [Jupyter](https://jupyter.org/) for interactive data analysis. Please see their website for install instructions.

## Prerequisites
Windows, MacOS, and Linux should all work. You can also run Python in a Jupyter notebook in the cloud, using Google Colab.

The tutorials are compatible with Python version >= 3.9. You should have a current version of pip (>= 23) and setuptools (>= 68)

We will use the command `python3` to invoke Python on Linux, but on Windows the appropriate command may be `python`. You should find out what the appropriate command is for Python on your system.

Both pip and setuptools can be updated using pip itself with `python3 -m pip install --upgrade pip setuptools`.

In the tutorials, we use some software which is available from PyPI but is not available as a conda package. If you prefer to use conda, you will have to install some things in a conda environment
using a conda-managed version of pip.

In order to avoid dependency conflicts with other Python packages on your device,
including packages managed by the system package manager rather than pip or conda, you should create a virtual environment to install
all Python packages that will be used in the workshop. Start by navigating to the directory in which you plan to work, and follow the instructions appropriate for your package manager.

Alternatively, if you plan to use Google Colab for everything, you can skip to that section.

## Dependencies
The workshop will focus on four main packages.

<div class="grid cards" markdown>

-   :material-format-font:{ .lg .middle } __Pynapple__

    ---

    [Pynapple](https://github.com/pynapple-org/pynapple) is a light-weight python library for neurophysiological data analysis.

    <!-- [:octicons-arrow-right-24: Install instructions](pynapple/pynapple_setup.md) -->

-   :material-cube:{ .lg .middle } __NeMoS__

    ---

    [NeMoS](https://github.com/flatironinstitute/nemos) (Neural ModelS) is a statistical modeling framework optimized for systems neuroscience and powered by JAX.

    <!-- [:octicons-arrow-right-24: Install instructions](nemos/nemos_setup.md) -->

-   :material-eye-arrow-right:{ .lg .middle } __CAJAL__

    ---

    [CAJAL](https://github.com/CamaraLab/CAJAL) is a Python library for multi-modal cell morphology analyses using Gromov-Wasserstein (GW) distance.

    <!-- [:octicons-arrow-right-24: Install instructions](cajal/cajal_setup.md) -->

-   :material-camera-control: __Navis__

    ---

    [Navis](https://github.com/navis-org/navis) is a package for **N**euron **A**nalysis and **Vis**ualization.

    <!-- [:octicons-arrow-right-24: Install instructions](navis/navis_setup.md) -->


</div>

In addition to these core tools, we will rely on some other software:

- Scanpy, a Python package for the analysis of single-cell gene expression data
- Jupyter, an interactive environment for evaluating Python code and plotting graphs
- ipywidgets, which extends the functionality of Jupyter (e.g., progress bars)
- leidenalg, an implementation of the Leiden clustering algorithm
- umap-learn, which is useful for visualizing the clustering structure of high-dimensional data
- Pandas, a dataframe library for manipulating and filtering tabular data
- Plotly, a rich visualization library

## Installing dependencies with Pip
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
## Installing dependencies with Conda
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

## Google Colab
Google Colab is a cloud computing service which can execute Jupyter notebooks stored in Google Drive. To use Google Colab for this tutorial, go to https://colab.research.google.com/ and click "File > New Notebook in Drive"

Install Python dependencies using Jupyter's pip magic command:
```
%pip install cajal scanpy leidenalg navis umap-learn pandas plotly pynapple nemos matplotlib requests
```

## Getting Help
The workshop organizers can be contacted for installation help in the [Slack group](https://join.slack.com/t/pythontoolsfo-ehx1178/shared_invite/zt-2qjzd1c44-NZ~9kt0~kh47X6t80tK8Mg) for the workshop. 