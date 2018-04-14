# Yuuno on Linux/osx
This guide is an attempt to help one installing and using VapourSynth with Yuuno on a non-windows computer.

## Table of contents
+ [Prerequisites](#prerequisites)
+ [Installing Python 3.6.4 via pyenv](#installing-python-364-via-pyenv)
+ [Plugins](#plugins)
+ [Scripts](#scripts)
+ [Using Yuuno](#using-yuuno)

## Prerequisites:
+ [Python 3](https://www.python.org/)
+ osx-only: [homebrew](https://brew.sh/)  
  install it with this command:  
  `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`  
+ [x264](https://www.videolan.org/developers/x264.html)  
  osx: please install from source, since the homebrew version does not support 10bit!  
+ [pyenv](https://github.com/pyenv/pyenv)
+ [pyenv-virtualenv](https://github.com/pyenv/pyenv-virtualenv)
+ [pyenv-virtualenvwrapper](https://github.com/pyenv/pyenv-virtualenvwrapper)
+ [l-smash](https://github.com/l-smash/l-smash)

Install them:  
osx: `brew install python3 pyenv pyenv-virtualenv pyenv-virtualenvwrapper l-smash`  

On Linux, you have to install most of them manually...  
`sudo apt-get update`  
`sudo apt-get install -y build-essential checkinstall git libfaac-dev libgpac-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev librtmp-dev libtheora-dev libvorbis-dev pkg-config texi2html yasm zlib1g-dev python3 libx264-dev`  
Then install the packages that I included.  
They may need some additional configuration apart from the usual CMMI process.

## Installing Python 3.6.4 via pyenv
Python 3.6.6 apparently does not work, but this version does ;)  

Open the file ~/.bash_profile and put this line there:  
`eval "$(pyenv init -)"`  
Then start a new terminal session by closing and reopening a Terminal window.  
Install Python 3.6.4 with pyenv:  
`pyenv install 3.6.4`  
Create a new virtualenv (you can name it whatever you want tho, I chose jupyter3):  
`pyenv virtualenv 3.6.4 jupyter3`  
Activate the pyenv and install internal dependencies:  
`pyenv activate jupyter3`  
`pip install jupyter vapoursynth yuuno numpy`  
`python -m ipykernel install --user`  

## Plugins
Included Plugins are:  
+ [AddGrain](https://github.com/HomeOfVapourSynthEvolution/VapourSynth-AddGrain)
+ [Bilateral](https://github.com/HomeOfVapourSynthEvolution/VapourSynth-Bilateral)
+ [flash3kyuu_deband](https://github.com/SAPikachu/flash3kyuu_deband)
+ [fmtconv](https://github.com/EleonoreMizo/fmtconv)
+ [KNLMeansCL](https://github.com/Khanattila/KNLMeansCL)
+ [L-SMASH-Works](https://github.com/VFR-maniac/L-SMASH-Works)  

Install these packages for your system.  
I included the compiled libraries for osx.  

You can autoload the plugins by putting them into `/usr/local/lib/vapoursynth`, if they don’t appear there after installing.  
More information can be found [here](http://www.vapoursynth.com/doc/autoloading.html#linux).

## Scripts
Navigate to `~/.pyenv/versions/3.6.4/envs/jupyter3/lib/python3.6/site-packages` and put the contents of the folder `scripts` in this directory.  

## Using Yuuno
Start up jupyter: `jupyter notebook`  
You can now navigate in your default browser to some directory and create a new script (choose Python 3).  
Once you created a new script, you have to load yuuno first: `%load_ext yuuno`  
That should be it. More information can be found on the [yuuno page](yuuno.encode.moe/readme.html).
