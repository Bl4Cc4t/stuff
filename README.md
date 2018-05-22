# Yuuno on OS X
===============

This guide is an attempt to help one installing VapourSynth with Yuuno on OS X.

## Prerequisites
----------------
- [Homebrew](https://brew.sh/)  
- [Python 3](https://www.python.org/)
- [x264](https://www.videolan.org/developers/x264.html)  
- [pyenv](https://github.com/pyenv/pyenv)
- [pyenv-virtualenv](https://github.com/pyenv/pyenv-virtualenv)
- [pyenv-virtualenvwrapper](https://github.com/pyenv/pyenv-virtualenvwrapper)

Please install the Homebrew package manager, if you haven’t already.
After doing so, please install the other packages via this command:  

```
brew install python3 pyenv pyenv-virtualenv pyenv-virtualenvwrapper x264 --with-10-bit
```  

## Installing Python 3.6.4 via pyenv
------------------------------------
The newest Python 3.6.6 apparently does not work, but this version does ;)

To work, pyenv has to be initialized first.

```
echo "eval '\$(pyenv init -)'" >> ~/.bash_profile
```

Then start a new terminal session by closing and reopening a Terminal window.

Install Python 3.6.4 with pyenv:

```
pyenv install 3.6.4
```

Create a new virtualenv (you can name it whatever you want tho, I chose jupyter3):

```
pyenv virtualenv 3.6.4 jupyter3
```

Activate the pyenv and install internal dependencies:

```
pyenv activate jupyter3
pip install jupyter vapoursynth yuuno numpy
python -m ipykernel install --user
```

## Plugins
----------
Plugins can be installed by following the directions on [this](https://github.com/Bl4Cc4t/homebrew-vsplugins) repo.

## Scripts
----------
Navigate to `~/.pyenv/versions/3.6.4/envs/jupyter3/lib/python3.6/site-packages` and put the contents of the folder `scripts` in this directory.  

## Using Yuuno
--------------
Start up jupyter: `jupyter notebook`  
You can now navigate in your default browser to some directory and create a new script (choose Python 3).  
Once you created a new script, you have to load yuuno first: `%load_ext yuuno`  
That should be it. More information can be found on the [yuuno page](yuuno.encode.moe/readme.html).
