# Speech Analysis
This project aims to detect autism in children by analysing speech pattens<br>

##Installation and configuration of Kaldi with PyKaldi wrapper<br><br>

#Background<br>
My Operating System is Linux Netrunner which is an Ubuntu variant.<br>
It is better to have Anaconda installed, which will simplify developing [1].<br>
Python version I use is Python 3.7.<br>

#Introduction<br>
Kaldi is an open-source speech recognition toolkit written in C++ for speech recognition and signal
processing, freely available under the Apache License v2.0 [2]. PyKaldi is a Python scripting layer for the
Kaldi speech recognition toolkit [3].<br>

#How to add pykaldi library into conda<br>
Made an empty conda environment which has no python libraries inside. I gave its name as 'kaldienv'
when creating [4].<br>
conda create --name kaldienv<br>
Activated that environment:<br>
conda activate kaldienv<br>
Installed pykaldi into kaldienv [5]. I installed it for CPU only since I do not have a GPU for CUDA support [6].<br>
conda install -c pykaldi pykaldi-cpu<br>
Other related libraries also will be installed into the environment with PyKaldi. The following command<br>
will list all the other related libraries installed with pykaldi.<br>
conda list<br>

4. How to setup computer to install Kaldi<br>
Installed Kaldi using following steps.<br>
I updated my OS.<br>
sudo apt-get update<br>
sudo apt-get upgrade<br>
Installed GIT. If already installed it will say it is up to date.<br>
sudo apt-get install git<br>
Install bc. bc is a programming language [7].<br>
sudo apt-get install bc<br>
Installed c++ compiler, because kaldi is written in c/c++ , to compile it needs a compiler.<br>
sudo apt-get install g++<br>
Install linux packages needed to compile Kaldi. Those are named as make, automake, autoconf, bzip2,<br>
libtool, subversion, libatlas3-base.<br>
sudo apt-get install zlib1g-dev make automake autoconf bzip2 libtool subversion<br>
sudo apt-get install libatlas3-base<br>

5. How to install Kaldi<br>
I made a folder named kaldi.<br>
mkdir kaldi<br>
Cloned kaldi from github [8].<br>
git clone http://github.com/kaldi-asr/kaldi.git kaldi --origin upstream<br>
Changed directory using following command.<br>
cd kaldi/tools<br>
The following command shows you if any dependency is missing.<br>
extras/check_dependencies.sh<br>
I missed sox. Sox is a package to read write sound files [9].<br>
I installed it using:<br>
sudo apt-get install sox<br>
Again, ran this command to see any other dependency is missing.<br>
extras/check_dependencies.sh<br>
Ran the following command to compile kaldi. This will take a long time.<br>
make<br>
To install the irst language model, used the following command.<br>
Current folder is kaldi/tools, changed it to kaldi/src.<br>
cd .. is to go back one directory back. cd is the command to change directory. mkdir is to make a new<br>
directory. I mentioned these simple commands thinking if you are new to linux.<br>
cd kaldi/src<br>
Inside this directory, ran the following commands one after the other which took a long time to complete.<br>
./configure --shared<br>
This gave me an error, MKL library missing error occurred [10]. I fixed it as follows.<br>
Downloaded MKL (Math Kernel) library from Intel website [11].<br>
Installed intel MKL into /opt/intel folder in my machine.<br>
I re-ran the command, ./configure --shared<br>

Then compiled using following commands.<br>
make depend<br>
make<br>
Installed the language model kaldi_lm inside kaldi/tools directory.<br>
cd kaldi/tools<br>
extras/install_kaldi_lm.sh<br>

6. References<br>
[1] Anaconda. 2020. Anaconda Python/R Distribution - Free Download. [online] Available at:
<https://www.anaconda.com/distribution/> [Accessed 24 April 2020].
[2] Kaldi-asr.org. 2020. Kaldi ASR. [online] Available at: <https://kaldi-asr.org/> [Accessed 24 April 2020].
[3] Awesomeopensource.com. 2020. Pykaldi. [online] Available at:
<https://awesomeopensource.com/project/pykaldi/pykaldi> [Accessed 24 April 2020].
[4] Docs.conda.io. 2020. Managing Environments — Conda 4.8.3.Post26+305Bf88e Documentation.
[online] Available at: <https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manageenvironments.html#creating-an-environment-with-commands> [Accessed 24 April 2020].
[5] GitHub. 2020. Pykaldi/Pykaldi. [online] Available at: <https://github.com/pykaldi/pykaldi> [Accessed
24 April 2020].
[6] En.wikipedia.org. 2020. CUDA. [online] Available at: <https://en.wikipedia.org/wiki/CUDA>
[Accessed 24 April 2020].
[7] En.wikipedia.org. 2020. Bc (Programming Language). [online] Available at:
<https://en.wikipedia.org/wiki/Bc_(programming_language)> [Accessed 24 April 2020].
[8] GitHub. 2020. Kaldi-Asr/Kaldi. [online] Available at: <https://github.com/kaldi-asr/kaldi> [Accessed 24
April 2020].
[9] Sox.sourceforge.net. 2020. Sox - Sound Exchange | Homepage. [online] Available at:
<http://sox.sourceforge.net/> [Accessed 24 April 2020].
[10] Groups.google.com. 2020. Google Groups. [online] Available at:
<https://groups.google.com/forum/#!topic/kaldi-help/DJ0ScJ2AXWo> [Accessed 24 April 2020].
[11] Corporation, I., 2020. Download Intel® Performance Libraries - Intel® Products. [online]
Registrationcenter.intel.com. Available at:
<https://registrationcenter.intel.com/en/products/postregistration/?sn=N2R2-
SR38476P&EmailID=vijani.p%40sliit.lk&Sequence=2696843&dnld=t> [Accessed 24 April 2020].
