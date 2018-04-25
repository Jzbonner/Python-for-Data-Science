# The Efficient Frontier: Markowitz Portfolio Optimization in Python 
> In this blog post you will learn about the basic idea behind Markowitz portfolio optimization as well as how to do it in Python. We will then show how you can create a simple backtest that re-balances its portfolio in a Markowitz-optimal way. We hope you enjoy it and get a little more enlightened in the process.

(_Quantopian Blog_)

For additional documentation on the Quantopian Zipline backtester please refer to this reference guide: http://www.zipline.io/index.html. However a brief description of how to setup the Quantopian Zipline backtester and the Jupyter Notebook locally can be found below: 

When working from within the Anaconda distribution of Jupyter Notebook it is necessary to employ a dev environment that has properly configured all the necessary dependencies to run a zipline backtester. I have done this using the conda package manager and creating a python-3.5 spec zipline environment, that must be activated prior to running Jupyter Notebook.
* To activate this environment - `$ source activate env_zipline`
* To deactivate this environment after running the above code - `$ source deactivate`
* Depending on whether you are using the Anaconda Distribution Conda Package Manager with Windows 10 CMD (batch) or the conda package manager via the Python terminal from within VSCode your initialization process will differ 

For Utilizing the Conda Package Manager (Windows 10 Batch) you will need the following command to register your Quandl API key to important data into zipline. 
* Important for initializing a Quandl API key in Windows 10 using batch: `cmd /V /C "set "QUANDL_API_KEY=<api-key>" && zipline ingest -b quandl"`

For utilizing the Conda Package Manager with VSCode, you can skip setting up a conda dev environment since and just install zipline and jupyter notebook to your initial dev workspace. 
* You will have access to the conda package manager if you already have Anaconda installed but if not you can install it via pip by the following command `pip install conda` 
* Use `conda install -c Quantopian zipline` to install Quantopian's Zipline locally to your dev workspace
* Use `pip3 install jupyter` to install the Jupyter Notebook platform to be ran locally via a localhost, for example `http://localhost:8080` 
* Initialize your zipline installation by connecting it to Quandl's datasets via your Quandl API key. 

After the following is completed you are now ready to work from either Windows 10 CMD (batch) prompt or from directly within your VSCode Python Workspace environment. Utilizing the file manager native to VSCode makes it easier to keep track of Python files, Jupyter Notebooks, etc. So I find it best to utilize VSCode. Nothing wrong with using what you feel is most comfortable. 




