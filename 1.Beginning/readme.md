## [Back](https://github.com/ifanzilka/Statistic_for_R/blob/main/README.md)
# For Linux

### Step 1: Update System
Like always, update system package index, and optionally upgrade all installed packages to latest.
    
    sudo apt update
    sudo apt -y upgrade
### Step 2: Install R on Ubuntu / Debian
We need to install r-base package which contains the basic R functions that let you perform arithmetic operations and basic programming in R. Use the command below to install.
        
        sudo apt -y install r-base
### Step 3: Download and Install RStudio
Now visit the  [RStudio downloads page](https://rstudio.com/products/rstudio/download/#download) to grab the latest release of RStudio for Debian based Linux distributions.

        sudo apt -y install wget
        wget https://download1.rstudio.org/desktop/xenial/amd64/rstudio-1.2.5042-amd64.deb
        sudo apt install ./rstudio-1.2.5042-amd64.deb
If you encounter any dependency problems, run:
        
        sudo apt -f install
### Step 4: Launch RStudio
Launch RStudio from Applications search section of your Desktop Environment or from the terminal.
    
    rstudio

