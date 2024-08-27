# Installing Navis

To follow along during the workshop you will need `Navis` and [Jupyter](https://jupyter.org/) lab or notebook.

You have effectively two options:

## Option 1: Using Google Collaboratory

The hassle-free option is where you use Google's [Collaboratory](https://colab.research.google.com/). That way everything runs on Google's Cloud platform and you don't have to worry about a thing.

Try it out! Clicking on this badge will open a test notebook - simply follow the instructions: [![demo](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/navis-org/neuropython2024/blob/main/material/navis/navis_on_colab.ipynb)

The downside of `Colab` is that the environment is not persistent - i.e. you will have to re-install `Navis` (and other packages) every time you start a
new notebook.

In the long run, you might want to check out Option 2 but for this workshop you should be just fine with this setup.

## Option 2: Installing Navis on your own machine

`Navis` is published as a [Python package] and can be installed with `pip`, ideally by using a [virtual environment]. Open up a terminal and install
`Navis` with:

=== "Full Install"

    The full install should set you up for using `Navis` plus a number of
    extra dependencies that are just nice to have. If
    you run into issues, try the minimal install
    instead.

    ``` sh
    pip install navis[all] -U
    ```


=== "Minimal"

    If you're running into issues with the full install, you can try
    the minimal install instead:

    ``` sh
    pip install navis -U
    ```

=== "Dev"

    To install the latest version from Github:

    ``` sh
    pip install git+https://github.com/navis-org/navis@master
    ```

!!! tip

    MacOS (both Intel and the new ARM chips) and Linux should work off the bat without any problems.
    On Windows, you might run into issues with some of the dependencies. If that happens, we recommend you check
    out the [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/install) (WSL).


Don't forget to all install Jupyter lab/notebook!

## What next?

<div class="grid cards" markdown>

-   :material-cube:{ .lg .middle } __Documentation__

    ---

    You're welcome to hop over to `Navis`' documentation and have a browse :nerd:

    [:octicons-arrow-right-24: Documentation](https://navis.readthedocs.io/en/latest/)

-   :material-eye-arrow-right:{ .lg .middle } __Exercises__

    ---

    Check out the exercises!

    [:octicons-arrow-right-24: The Basics](navis/exercises.md)

</div>


  [Python package]: https://pypi.org/project/navis/
  [virtual environment]: https://realpython.com/what-is-pip/#using-pip-in-a-python-virtual-environment
  [Markdown]: https://python-markdown.github.io/
  [Using Python's pip to Manage Your Projects' Dependencies]: https://realpython.com/what-is-pip/