# speech_rec
Veerandi's implementation of PyKaldi

Installation and Configuration of Kaldi with PyKaldi wrapper  
Author: Veerandi Kulasekara

## Prerequisites
Linux OS - I have used Debian Linux Distribution

## Install Anaconda 
Download the anaconda bash script [1]  
curl -O https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh  
Run the anaconda script [2]  
bash Anaconda3-2020.02-Linux-x86_64.sh  
conda init  
source ~/.bashrc  
To run terminal without having the conda base environment activated by default  
conda config –set auto_activate_base False  
Close and open the terminal. Or run source ~/.bashrc  
Made an empty conda environment which has no python libraries inside. I gave its name as 'speech_rec' when creating. conda create --name speech_rec Activated that environment: conda activate speech_rec  
Install anaconda pykaldi packages into speech_rec.  
conda install -c pykaldi pykaldi-cpu  

## PyKaldi Installation [3]

Install python and package manager: sudo apt-get install python python-pip  
Running the commands below will install the python packages for building PyKaldi from source:  
pip install --upgrade pip  
pip install --upgrade setuptools  
pip install numpy pyparsing  
Running the commands below will install the system packages needed for building PyKaldi from source:  
sudo apt-get install autoconf automake cmake curl g++ git graphviz libatlas3-base libtool make pkg-config subversion unzip wget zlib1g-dev  
Clone the PyKaldi Repository and Create a new Python Environment: git clone https://github.com/pykaldi/pykaldi.git  
cd pykaldi/tools  
check if system dependencies are installed  
./check_dependencies.sh  
./install_kaldi.sh  
  
 This will check dependencies required for kaldi and if there is any missing package you will get recommend command to install those packages. Run that command and run ./install_kaldi.sh command again to build kaldi.
   
     
## References 
[1]"How To Install Anaconda on Ubuntu 18.04 [Quickstart] | DigitalOcean", Digitalocean.com, 2020. [Online]. Available: https://www.digitalocean.com/community/tutorials/how-to-install-anaconda-on-ubuntu-18-04-quickstart. [Accessed: 24- Apr- 2020].  
[2]"Installing on Linux — Anaconda documentation", Docs.anaconda.com, 2020. [Online]. Available: https://docs.anaconda.com/anaconda/install/linux/. [Accessed: 24- Apr- 2020].  
[3]"pykaldi/pykaldi", GitHub, 2020. [Online]. Available: https://github.com/pykaldi/pykaldi#installation. [Accessed: 24- Apr- 2020].
