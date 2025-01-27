# Instructions for using Anaconda as a Docker workaround
If you are having issues with installing Docker (in particular if you are using Windows, but not Windows 10 Pro), we will here outline an alternative to get up and running with a local Python environment using Anaconda.

## (Windows) Install & configure Powershell
- Install Powershell if not installed already.
- Open up the startup menu, and type "powershell", after which "Windows Powershell" should show up. Right-click on it, and click "Run as administrator".
- Once Powershell has started running as administrator, allow scripts to be executed by typing `Set-ExecutionPolicy RemoteSigned`, pressing Enter, typing `y` for Yes, and pressing Enter once again. Now you can close Powershell, and will not have to run it as administrator again.

## Download & install Anaconda
1. Download Anaconda Python 3.7 from https://www.anaconda.com/distribution/
1. Run the installer, but first read through **all** of the below remarks.
  - If on Windows, you might need to run the downloaded installation file as administrator, depending on choice of installation directory (right-click the file, and click "Run as administrator").
  - Do not use the default installation path, if it contains spaces or other special characters. We do not know exactly when this could turn out to be an issue, but it is discouraged by Anaconda (more info [here](https://docs.anaconda.com/anaconda/user-guide/faq/#distribution-faq-windows-folder)). For instance, if John Doe ran the installer, the default path might be `C:\Users\John Doe\Anaconda3`, which could be an issue since his username has a space in it. An alternative would be `C:\anaconda3`, although this would probably require you to run the installation as administrator.
  - During the installation, make sure to select the option to add Anaconda to your PATH environment variable. As far as we know, this is usually not recommended by Anaconda and thus deselected by default.
  - You do not need to "Register Anaconda as the default/system Python 3.7"
1. After installation, run the command `conda init` (or optionally `conda init <SHELL_OF_YOUR_CHOICE>`), in order to setup conda to work properly with your command-line interpreter (terminal). You may have been asked for the `conda init` step to be automatically carried out during installation, but if not it is essential that you do it manually, in order to be able to activate your Conda environment later.
1. Close all terminal windows currently open (the `conda init` step above will not have any effect on existing terminal windows - only on new ones).

## Install Git and clone course repository
1. Install Git, https://git-scm.com/book/en/v2/Getting-Started-Installing-Git.
1. Start up a terminal (On Windows, use Powershell)
1. Clone the course GitHub repo, by the following command (this creates a folder in your current directory with the necessary files for the next instructions): `git clone https://github.com/JulianoLagana/deep-machine-learning.git`

## Install Python dependencies, and get started with Conda environments
1. Navigate to the folder created by the cloning, using the command `cd`, followed by the directory's name.
1. Create the Conda environment for the course by typing `conda env create -f conda-environment-files/conda-environment-cpu.yml`
1. Wait for the installations to complete, and make sure there were no errors.
1. Now, you have created a virtual Conda environment with all Python dependencies installed. Still, in order to get access to this environment, you must activate it (and this has to be done every time you start up a new terminal window). Activate it by the command `conda activate dml`.
1. You should from now on see `(dml)` printed at the start of every row in the terminal, indicating, that the `dml` environment is activated. If this does not happen, most probably the `conda init` step was not carried out successfully during installation.
1. Now you can start using Jupyter notebook. To do so, type `jupyter notebook`
1. Please have a look at the two Jupyter notebooks, *testing_notebook.ipynb* and *Getting started with JN.ipynb*, available in the current folder you are in. The first file checks if the installation was successful, whereas the second file give you initial advices regarding how to use Jupyter notebooks.
1. To deactivate the conda environment, you simply type `conda deactivate`.

### Update the Conda environment
**Note:** This is important!

Make sure that your Conda environment is always up-to-date with the latest environment file available from the GitHub repo. We will try to make a Canvas announcement whenever it is updated.

How to update the Conda environment:
- Navigate to the git repo you have cloned.
- Make sure the conda environment is deactivated (see above).
- Type `conda env update -f conda-environment-files/conda-environment-cpu.yml --prune`
- Now you can activate the environment again.

## GPU-version
On GitHub, there is one `conda-environment-cpu.yml` file and one `conda-environment-gpu.yml` file. If you want to work locally with your GPU-enabled computer, you can try to use the GPU version instead, and hopefully this will work for you. It can however be quite a hassle to properly install a GPU-enabled deep learning environment, and we do not have the resources to help you out here.

That being said, this could be an opportunity for you to use your GPU, despite not running Linux (which is the only OS through which you could utilize your GPU via the Docker solution)
