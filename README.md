# Pvinsight Onboarding

This document is intended to help new collaborators to the PVInsight project get set up with a Python environment for running PVInsight algorithms. We recommend using miniconda as a package and virtual environment manager. 

There are two YAML files included in this repository: `pvi-dev` and `pvi-user`. The difference is whether or not the PVInsight code repositories `solar-data-tools` and `statistical-clear-sky` are installed from conda on the Python path (the “user” configuration) or not (the developer or “dev” configuration). 

## Steps for both environments:
1) Make sure that gcc and g++ are installed on your system. For Mac OS we suggest using homebrew to install these two pieces of software. For Ubuntu, you can use apt-get.
2) Install miniconda: https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html
3) Obtain a Mosek license. Personal-use academic licenses are available for free to people with `.edu` email addresses here: https://www.mosek.com/products/academic-licenses/
4) Put license here: `~/mosek/mosek.lic`

## Create `pvi-user` environment
This environment grabs the latest published versions of `solar-data-tools` and `statistical-clear-sky` from Anaconda, and installs them in an environment with all the necessary support software. This is intended for _users_ of PVInsight software.
1) Create a new environment from the `pvi-user.yaml` file. Instructions: https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-from-an-environment-yml-file
2) Activate the new environment: `conda activate pvi-user` (“pvi-user” is the name of the environment)
3) Check that everything is installed and working correctly by running `nosetests cvxpy` from within the new environment 


## Create `pvi-user` environment
This environment installs all the necessary support software, but does not install `solar-data-tools` or `statistical-clear-sky` from Anaconda. Instead, these packages are cloned from GitHub (pre-published coded) and installed as "editable" packages with pip. This allows for local editing and testing of the packages and is intending for _developers_ of PVInsight software.
1) Clone [`solar-data-tools`](https://github.com/slacgismo/solar-data-tools/) and [`statistical-clear-sky`](https://github.com/slacgismo/StatisticalClearSky) to your local machine
2) Create a new environment from the `pvi-dev.yaml` file. Instructions: https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-from-an-environment-yml-file
3) Run the following two commands: `pip install -e path/to/solar-data-tools` and `pip install -e path/to/statistical-clear-sky`
4) Activate the new environment: `conda activate pvi-dev` (“pvi-dev” is the name of the environment)
5) Check that everything is installed and working correctly by running `nosetests cvxpy` from within the new environment 

## Comment on the final test step
You may find that there are a small number of errors. I currently get the following:

```
Ran 752 tests in 44.747s

FAILED (SKIP=147, errors=1, failures=1)
```

That is okay. If you get a large number of errors, then something probably went wrong.

