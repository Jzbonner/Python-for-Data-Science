# The Efficient Frontier: Markowitz Portfolio Optimization in Python 
> In this blog post you will learn about the basic idea behind Markowitz portfolio optimization as well as how to do it in Python. We will then show how you can create a simple backtest that re-balances its portfolio in a Markowitz-optimal way. We hope you enjoy it and get a little more enlightened in the process.

(_Quantopian Blog_)

For additional documentation on the Quantopian Zipline backtester please refer to this reference guide: http://www.zipline.io/index.html

When working from within the Anaconda distribution of Jupyter Notebook it is necessary to employ a dev environment that has properly configured all the necessary dependencies to run a zipline backtester. I have done this using the conda package manager and creating a python-3.5 spec zipline environment, that must be activated prior to running Jupyter Notebook.
* To activate this environment - `$ source activate env_zipline`
* To deactivate this environment after running the above code - `$ source deactivate`
* Depending on whether you are using the Anaconda distribution for Windows and conda package manager or if you are using a Python terminal from within Linux or macOS your initialization process will differ 

For Utilizing the Conda Package Manager (Windows 10 Batch) you will need the following command to register your Quandl API key to important data into zipline. 
* Important for initializing a Quandl API key in Windows 10 using batch: `cmd /V /C "set "QUANDL_API_KEY=<api-key>" && zipline ingest -b quandl"`



