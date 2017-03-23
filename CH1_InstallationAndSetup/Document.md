# Chapter 1 Installation and Setup

### Python Setup

Install python by visiting https://www.python.org/downloads/.
The python website auto detects the OS of your machine and provide you with the relevant setup. The setup for windows is an exe installer.
Once you have completed the python installation, check if python environment variable is properly setup by running command prompt in windows and typing

```
>python 
Python 3.6.0 (v3.6.0:41df79263a11, Dec 23 2016, 07:18:10) [MSC v.1900 32 bit (Intel)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

The result should be similar to above detailng about python version in my case it is 3.6.0.

#### Pip 

Pip is a package manager for python which work as downloader and installer of python packages from online repository.
To ensure pip is successfully running on your machine run following command

```
>pip3
pip3

Usage:
  pip <command> [options]

Commands:
  install                     Install packages.
  download                    Download packages.
  uninstall                   Uninstall packages.
  freeze                      Output installed packages in requirements format.
  list                        List installed packages.
  show                        Show information about installed packages.
  check                       Verify installed packages have compatible dependencies.
  search                      Search PyPI for packages.
  wheel                       Build wheels from your requirements.
  hash                        Compute hashes of package archives.
  completion                  A helper command used for command completion.
  help                        Show help for commands.
```

This output describes that pip is successfully running on your machine.


#### Installing Pandas and Numpy

We will use pip package manager to download pandas and numpy library.

Run command prompt and execute command to update pip to latest version

```
pip3 install --upgrade pip
```

Then install numpy library using

```
pip3 install numpy
```

Numpy download will start and later after download installtion will auto begin.

After numpy install pandas. **Numpy is prerequisite for pandas so be sure to install numpy first**

```
pip3 install pandas
```

#### Installing Jupyter Notebook

Now we have downloaded the required library, configured our python and all set and ready. Its time to get our canvas to work around. There are various alternative of python editor we will use Jupyter one of the most famous web based notebook for various languages.

To install jupyter use the following command

```
pip3 install jupyter
```

Once the jupyter is intalled use following command from your command prompt to run jupyter notebook.

```
jupyter notebook
```

The interface for jupyter looks like image shown below

![](images/JupyterInterface.png)

Jupyter can be used with various programming languages, each of which is configured using kernels. As jupyter server is build on python and it is available by default. For more on kernels visit [kernels page](http://jupyter.readthedocs.io/en/latest/projects/kernels.html).

To run new python notebook go to new button and click python 3 option. Which will open window for running your python code. The interface will look like the image shown below.

![](images/jupytereditor.png)



With this we come to the end of configuring our python environment. More examples on python will be available in next chapter.


### R Installation

R can be downloaded from the location [R Cran Repository](https://cran.r-project.org/bin/windows/base/). Download the latest version of R, current is R 3.3.3.
Execute the downloaded file and follow the setup with default options. Now run the R from desktop program shortcut created by installer this will open R Gui with R console to work.

#### Installing Pacakages

R is one of the oldest and most favoured language in statistical computing, R at its base is truly efficient and provide some great functions. Still the real power of R lies in packages or user defined modules that can be installed to perform some hard to code operation in very simple way. These packages are developed by R development team or the R community users across the globe. Few very famous packages are
* ggplot2
* dplyr
* swirl
* shiny and etc.

The command to install any package in R is 

```{r}
install.packages("packageName")
```

Lets begin by installing package Rattle, you can read about rattle at http://rattle.togaware.com

```{r}
install.packages("rattle")
```

This command will start download of rattle package and its dependency from CRAN repository. If you are installing a package for first time in your R environment it may ask you to choose CRAN repo location, for which you can proceed with default selected option.

Once this package is downloaded and installed please try command

```{r}
library(rattle)
```

If this command show error or notify to download RGtk2 proceed with its download and installation and run the command once again.
**It is noted installing of package require some dependency which differ from system to system. So read the error message if you are not able to download or install and google it, there are various answer available for the same.**

Once installation is completed run command on R shell

```{r}
library(rattle)
ratlle()
```

This will start rattle on your R,  once started it may ask to download additional packages like 'XML'. So hit yes button and proceed with installation.

#### dplyr

dplyr is very famous package of R for data munging in R like pandas in Python. So please install it using command `install.packages(dplyr)` as we  will need it for later chapters.
