# Creating a Python Virtual Environment for IRAF/PyRAF
*Last Updated: 2019 Sept 26*

---

**DISCLAIMER**:
This was single-handedly the stupidest piece of software I've had to install in a long while. Don't feel bad if you found it impossible to install. I tried several methods of installation, but many are deprecated, no longer supported, or no longer available. **DO NOT USE PIP FOR INSTALLATION**.


## Installation
_Note_: The following instructions are primarily based on these set of [instructions](https://astroconda.readthedocs.io/en/latest/faq.html) from STScI and astroconda with some modifications.

Ensure you have Anaconda or [Miniconda](https://docs.conda.io/en/latest/miniconda.html) installed. If you do not have either installed, follow their respective instructions. We recommend you install the Python 2.7 version of Miniconda.

### Create an Environment with Commonly Used Astronomy Packages

```
sudo conda create -n astroconda -c http://astroconda.org/channel/main stsci
```

When the program asks for permission to install packages, enter: `y`.
Repeat for the remaining commands.

### Install IRAF & PyRAF to this Environment

```
sudo conda install -n astroconda -c http://astroconda.org/channel/main iraf-all
sudo conda install -n astroconda -c http://astroconda.org/channel/main pyraf-all
sudo conda update -n astroconda -c http://astroconda.org/channel/main --all
```

---

## Getting Started

### To activate this environment:
```
conda activate astroconda
```

### To deactivate the environment:
```
conda deactivate
```


## IRAF
To start, ensure you activate the environment with the activation command above.

Type `cl` from the terminal to open IRAF. Ensure that you have access to modules by typing them (e.g., `stsdas`) once you are in the IRAF command prompt.

To exit, `logout` from the IRAF command prompt and deactivate the environment.


## PyRAF
You **MUST** use Python 2 to use PyRAF. No support was built for Python 3.

After activating your environment, start interactive python from the terminal:

```
python2
```

Check whether PyRAF installed correctly by importing the PyRAF package and loading an IRAF module:

```
from pyraf import iraf
iraf.stsdas()
```

Alternatively, if you are writing a script, ensure that you are specifying python 2 in the first line of the script as in the following example.

```
#!/usr/bin/env python2

from pyraf import iraf

def func(arg):
	iraf.stsdas()
	
if __name__ == "__main__":
	func(0)
```

You can also explicitly specify to use Python 2 when running the script:

```
python2 script.py
```