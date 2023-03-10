# eqchlorine
Python script to generate chlorine 36 profile on fault scarp.

EQCHLORINE is a python package designed to generate synthtic chlorine 36 concentration profiles associated to seismic sequence.
This code is the adaptation in python of an earlier published code : Modelscarp (Schlagenhauf et al. 2010).
Modelscarp (matlab) is the basis of many algorithm to retrieve earthquake sequence 
with chlorine 36 sampling profiles on limestone. 

Install
-------
Just download the package, extract it in your working directory.
- Requirements :
- Python 3.9
- numpy
- matplotlib
- scipy
- colorama

Creating a virtual environment to install those libraries is highly recommended.

With Conda/Miniconda: 

From your terminal : enter the following command

```
conda create -n NAME_OF_YOUR_ENVIRONMENT
conda activate NAME_OF_YOUR_ENVIRONMENT
conda install numpy matplotlib scipy colorama
```

**Check out your installation:**

In your terminal, enter the following command :
```
cd tests
python3 run_test.py
```


Citation
--------

If you use EQCHLORINE in a publication, please cite the original Modelscarp paper ([Sclagenhauf et al.
2010](https://doi.org/10.1111/j.1365-246X.2010.04622.x)).


License
-------

The license for all parts of the code derived from modelscarp is
MIT. The license for each file is explicitly stated at
the top of the file and the full text of each license can be found in
`licenses`.


FAQ
---

**Why go to Python ?**

EQCHLORINE is just the fisrt step of a wider project : Pymodelscarp. The heart Pymodelscarp project
is to make a user-friendly code to invert chlorine 36 data in order to retrieve earthquake sequences. Python was the obvious 
choice because Python is open-source, easy to use and offers a large catalogue of libraries.
EQCHLORINE will be the core of the inversion code, as it will be used as a forward function
for the coming inversion code.


**What's different from modelscarp ?**

- The package was reorganised for readibility and optimization purposes

- The long term history of the fault is calculated following (Tesson & Benedetti 2019)
and is now calculated as a function of the longterm relief

**What is the format for the data files?**

All your data files must be in .txt format.
- The chemistry of the samples must be stored in a "data.txt" file
- The chemistry of the colluvium must be stored in a "coll.txt" file
- The magnetic filed data must be stored in "sf.txt" file.

For further formating see "format_you_data.pdf"

**I am new to Python : How do I use EQCHLORINE ?**

First, give it a try with the example provided in "example" folder : the MA3 site located on the Magnola fault (Schlangenhauf et al. 2010).

Two solutions are avaible to run the script :

1) From a terminal window, in example directory, run the following command :

```
cd MA3
python3 run_forward.py
```

2) From IDE (PyCharm, Spyder, ...) :
Open "run_forward.py" and hit the run button

Few files will be created:

- "results.txt" file will be created and will contain the resulting chlorine 36 concentration profile.
- "plot.png" plot with the synthetic profile associated with the long-term history and the final chlorine 36 concentration profile.

Your plot should look like this : 

![alt text](https://github.com/mllinares/eqchlorine/blob/main/example/MA3/plot.png?raw=true)

Using your own data files :
Make sure your "data.txt", "coll.txt" and "sf.txt" files are in the correct format ('txt') and have the correct name:

- Copy your data files in the src directory
- Open "parameter.py" and enter your site parameters.
- Open "seismic_scenario.py" and set your earthquake sequence.

Follow the same procedure as above, either from a terminal window or from an IDE

**What does my package contain ?**

LICENSE.txt : the declared license
README.md : the read_me file
src : folder with the source code 
example : example folder with data from Magnola Fault (Schlangenhauf et al. 2010)

In the src folder, you will find :

- constants.py : all the constants used
- parameters.py : inputs parameters
- seismic_scenario.py : the input seismic sequence
- chemistry_scaling.py : functions that calculates the 36cl concentration due to chemistry
- geometric_scaling.py : functions that calculates the incident cosmogenic flux
- forward_function.py : the main function from which the final 36cl is calculated
- run_forward.py : script to run the code

You can also find a "util" folder containing basic functions used in the geometric_scaling.py

