# Portfolio Management, Strategies, and Optimization in Python 
> In this introductory section you will learn how to go about setting up Quantopian's Zipline backtester to work in tandem with Jupyter Notebook. Zipline is a Pythonic algorithmic trading library. It is an event-driven system for backtesting. Zipline is currently used in production as the backtesting and live-trading engine powering Quantopian -- a free, community-centered, hosted platform for building and executing trading strategies. These notes will also include information about portfolio management and optimization through algorithmic strategies. 

For additional documentation on the Quantopian Zipline backtester please refer to this reference guide: http://www.zipline.io/index.html. However a brief description of how to setup the Quantopian Zipline backtester and the Jupyter Notebook locally can be found below: 

When working from within the Anaconda distribution of Jupyter Notebook it is necessary to employ a dev environment that has properly configured all the necessary dependencies to run a zipline backtester. I have done this using the conda package manager and creating a python-3.5 spec zipline environment, that must be activated prior to running Jupyter Notebook.
* To activate this environment - `$ source activate env_zipline`
* To deactivate this environment after running the above code - `$ source deactivate`
* Depending on whether you are using the Anaconda Distribution Conda Package Manager with Windows 10 CMD (batch) or the conda package manager via the Python terminal from within VSCode your initialization process will differ 

For Utilizing the Conda Package Manager (Windows 10 Batch) you will need the following command to register your Quandl API key to important data into zipline. 
* Important for initializing a Quandl API key in Windows 10 using batch: `cmd /V /C "set "QUANDL_API_KEY=<api-key>" && zipline ingest -b quandl"`
* If initializing your Quandl API key from within iPython/Jupyter Notebook you would use this command: `!QUANDL_API_KEY=<api-key> zipline ingest -b quandl` 

For utilizing the Conda Package Manager with VSCode, you can skip setting up a conda dev environment since and just install zipline and jupyter notebook to your initial dev workspace. 
* You will have access to the conda package manager if you already have Anaconda installed but if not you can install it via pip by the following command `pip install conda` 
* Use `conda install -c Quantopian zipline` to install Quantopian's Zipline locally to your dev workspace
* Use `pip3 install jupyter` to install the Jupyter Notebook platform to be ran locally via a localhost, for example `http://localhost:8080` 
* Initialize your zipline installation by connecting it to Quandl's datasets via your Quandl API key. 

After the following is completed you are now ready to work from either Windows 10 CMD (batch) prompt or from directly within your VSCode Python Workspace environment. Utilizing the file manager native to VSCode makes it easier to keep track of Python files, Jupyter Notebooks, etc. So I find it best to utilize VSCode. Nothing wrong with using what you feel is most comfortable. 

Completing the above steps will allow you to have access to Quandl's Wiki Datasets as well as the ability to back test your trading strategies through the zipline backtester against said data. You can always ingest your zipline backtester with alternative datasets (either free or premium) from Quandl by utilizing the `ingest -b` command. Further details: 

> Quandl WIKI Bundle By default zipline comes with the quandl data bundle which uses Quandl's WIKI datasets. The quandl data bundle includes daily pricing data, splits, cash dividends, and asset metadata. To ingest the quandl data bundle we create an account on quandl.com to get an API key to be able to make more API requests per day. 

Please refer to the folder entitled [AlgoStrategies](https://github.com/Jzbonner/Python-for-Data-Science/tree/master/AlgoStrategies) for further information regarding Algorithmic Python Strategies and Examples. 

