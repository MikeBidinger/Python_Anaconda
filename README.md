# Anaconda for Python

Anaconda is a popular open-source distribution of the Python and R programming
languages, primarily used for data science, machine learning, and scientific
computing. It simplifies package management and deployment, making it easier
for developers to work with data analytics and scientific libraries.

Homepage: https://www.anaconda.com/

Download: https://www.anaconda.com/download

## Key Features

**Package Management**: Anaconda includes conda, a package manager that helps
in installing, updating, and managing packages and their dependencies. Conda
can manage libraries for both Python and R.

**Environment Management**: Conda also allows users to create, manage, and
switch between different environments with different versions of Python and
packages. This is particularly useful for testing and development purposes.

**Pre-installed Libraries**: Anaconda comes with over 1,500 data science
packages pre-installed, including popular libraries such as NumPy, pandas,
Matplotlib, SciPy, Scikit-learn, TensorFlow, and more.

**Integrated Development Environments (IDEs)**: Anaconda includes several IDEs,
most notably Jupyter Notebook, JupyterLab, Spyder, and PyCharm. These tools are
designed to enhance the productivity of data scientists and developers.

**Cross-Platform**: Anaconda is available for Windows, macOS, and Linux, making
it accessible to a wide range of users.

**Commercial and Free Versions**: Anaconda offers a free, open-source version
as well as enterprise versions with additional features for security,
governance, and support.

## Content:

-   [Conda Cheatsheet (PDF)](conda-cheatsheet.pdf)

    Cheatsheet with terminal commands for Anaconda.

-   [Automated Conda environment configuration (YML)](#automated-conda-environment-configuration-yml)

    Automated Anaconda environment creation with the use of a YAML
    configuration file. This file should include the name of the environment
    (`myenv`) and a list of dependencies. Optional are channels when needed and
    the python and dependencies versions for the environment.

## [Conda Cheatsheet (PDF)](conda-cheatsheet.pdf)

-   #### Conda Basics

|                                                 |                                                       |
| ----------------------------------------------- | ----------------------------------------------------- |
| Verify conda is installed, check version number | `conda info`                                          |
| Update conda to the current version             | `conda update conda`                                  |
| Install a package included in Anaconda          | `conda install [PACKAGE_NAME]  `                      |
| Run a package after install, example Spyder\*   | `spyder`                                              |
| Update any installed program                    | `conda update [PACKAGE_NAME]`                         |
| Command line help                               | `[COMMAND_NAME] --help` (e.g. `conda install --help`) |

-   #### Using environments

|                                                                |                                                       |
| -------------------------------------------------------------- | ----------------------------------------------------- |
| Create a new environment named py35, install Python 3.5        | `conda create --name [ENV_NAME] python=3.5`           |
| Activate the new environment to use it                         | `activate [ENV_NAME]`                                 |
| Get a list of all my environments, (\* = active environment)   | `conda env list`                                      |
| Make exact copy of an environment                              | `conda create --clone [ENV_NAME] --name [ENV_NAME_2]` |
| List all packages and versions installed in active environment | `conda list`                                          |
| List the history of each change to the current environment     | `conda list --revisions`                              |
| Restore environment to a previous revision                     | `conda install --revision 2`                          |
| Save environment to a text file                                | `conda list --explicit > [ENV_NAME].txt`              |
| Delete an environment and everything in it                     | `conda env remove --name [ENV_NAME]`                  |
| Deactivate the current environment                             | `deactivate`                                          |
| Create environment from a text file                            | `conda env create --file [ENV_NAME].txt`              |
| Stack commands                                                 | `conda create --name [ENV_NAME] [PACKAGE_NAME]`       |

-   #### Finding conda packages

|                                      |                                                      |
| ------------------------------------ | ---------------------------------------------------- |
| Use conda to search for a package    | `conda search [PACKAGE_NAME]`                        |
| See list of all packages in Anaconda | https://docs.anaconda.com/anaconda/packages/pkg-docs |

-   #### Installing and updating packages

|                                                                        |                                                                  |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------- |
| Install a new package in the active environment                        | `conda install [PACKAGE_NAME]`                                   |
| Run an installed package                                               | `[PACKAGE_NAME]`                                                 |
| Install a new package in a different environment                       | `conda install --name [ENV_NAME] [PACKAGE_NAME]`                 |
| Update a package in the current environment                            | `conda update [PACKAGE_NAME]`                                    |
| Install a package from a specific channel                              | `conda install --channel [CHANNEL_NAME] [PACKAGE_NAME]`          |
| Install a package directly from PyPI into the current active using pip | `pip install [PACKAGE_NAME]`                                     |
| Remove one or more packages from a specific environment                | `conda remove --name [ENV_NAME] [PACKAGE_NAME] [PACKAGE_NAME_2]` |

-   #### Managing multiple versions of Python

|                                                                                     |                                             |
| ----------------------------------------------------------------------------------- | ------------------------------------------- |
| Install different version of Python in a new environment named py34                 | `conda create --name [ENV_NAME] python=3.4` |
| Switch to the new environment that has a different version of Python                | `activate [ENV_NAME]`                       |
| Show the locations of all versions of Python that are currently in the path[^first] | `where python`                              |
| Show version information for the current active Python                              | `python --version`                          |

-   #### Specifying version numbers [^second]

| Contraint type           | Specification                           | Result                               |
| ------------------------ | --------------------------------------- | ------------------------------------ |
| Fuzzy                    | `numpy=1.11`                            | 1.11.0, 1.11.1, 1.11.2, 1.11.18 etc. |
| Exact                    | `numpy==1.11`                           | 1.11.0                               |
| Greater than or equal to | `"numpy>=1.11"`                         | 1.11.0 or higher                     |
| OR                       | <code>"numpy=1.11.1&#124;1.11.3"</code> | 1.11.1, 1.11.3                       |
| AND                      | `"numpy>=1.8,<2"`                       | 1.8, 1.9, not 2.0                    |

## [Automated Conda environment configuration (YML)](environment.yml)

### 1. Create the Conda environment file (.yml)

For example:

```yaml
name: myenv
channels:
    - defaults
dependencies:
    - python=3.10
    - numpy=1.26.4
    - pandas=2.2.2
    - requests=2.32.2
```

### 2. Create the Conda environment

Use the following command to create the Conda environment from the
'environment.yml' file:

```bash
conda env create -f environment.yml
```

### 3. Activate the Conda environment

Use the following command to activate the Conda environment:

```bash
conda activate [myenv]
```

### 4. Exporting an existing Conda environment

It is also possible to export an existing Conda environment to an
'environment.yml' file. This will export its dependencies and can be used with
the following command:

```bash
conda env export > environment.yml
```

[^first]: The first version of Python in the list will be executed.
[^second]: Quotation marks must be used when your specification contains a space or any of these characters: `>` `<` `|` `*`
