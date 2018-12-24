# Development setup

## Install pre-reqs

1. Install Python 2.7 or 3.5 or later from python.org, apt-get, or some other installer.
   Install Pip if it is not included with python.
   python and pip should be available from terminal to proceed. You might need to set aliases in mac and linux to do so since they require you to run python3 and pip3 instead of python and pip. 
   e.g. Adding this to your ~/.bash_profile or ~/.bashrc might be required
   ```
   alias python="python3"
   alias pip="pip3"
   ```

2. Install Virtual Python Environment (virtualenv):
   ```bash
   pip install virtualenv
   ```

## Get the source

1. Clone the Azure Devops CLI extension repository:
   ```bash
   git clone https://github.com/Microsoft/vsts-cli
   ```

2. Optionally, clone the Azure Devops Python SDK repository:
   ```bash
   git clone https://github.com/Microsoft/azure-devops-python-api
   ```

## Create a virtual environment

1. From the `vsts-cli` directory, create a new virtual environment:
   ```bash
   virtualenv env
   ```

2. Activate the new virtual environment:
   On Linux:
   ```bash
   source env/bin/activate
   ```
   On Windows:
   ```bash
   env\Scripts\activate.bat
   ```

3. Run the `dev_setup.py` script to install the Azure Devops CLI packages and other dependencies into your virtual environment:
   ```
   python scripts/dev_setup.py
   ```

## Developing

Run `az extension list` and `az devops -h` to verify your environment is setup properly. 

1. Set the `AZURE_EXTENSION_DIR` environment variable to a directory that will hold the extension(s) being developed:
    ```
    export AZURE_EXTENSION_DIR=~/.azure/devcliextensions
    ```
    The CLI will now look in this directory for extensions.

2. Install your extension into the extensions directory:
    ```
    pip install --upgrade --target ~/.azure/devcliextensions/azure-devops ~/Dev/azure-devops
    ```
    - `~/.azure/devcliextensions/azure-devops-extension` is the directory `pip` will install the extension to.
    - `~/Dev/azure-devops-extension` is the directory with the source code of your extension.

3. Continue to develop your extension:
    Any time you make changes to your extension and want to see them reflected in the CLI, run the command from step 2 again.

    
4. Run `az devops -h` again to verify if extension is installed properly.

5. Run `tests\runTests.ps1` to run recorded tests.





