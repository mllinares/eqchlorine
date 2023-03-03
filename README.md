# eqchlorine
Python script to generate chlorine 36 profile on fault scarp

Install
-------
Just download the package, extract it in your working directory.
- Requirements :
- Python 3.9
- numpy
- matplotlib
- scipy
- colorama

Creating a virtual environment and installing those libraries is highly recommended

1) With Conda/Miniconda: 
From your terminal : enter the following command

```
conda create -n NAME_OF_YOUR_ENVIRONMENT
conda activate NAME_OF_YOUR_ENVIRONMENT
conda install numpy matplotlib scipy colorama
```
**Check out your installation:**
In your terminal, enter the following command :
```
cd test
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
is to make a friendly user code to invert chlorine 36 data in order to retrieve earthquake sequences. Python was the obvious 
choice because its large catalogue of libraries.
EQCHLORINE will be the core of the inversion code, as it will be used as a forward function
for the coming inversion code.


**What changes with modelscarp ?**

- The package was reorganised for readibility and optimization purposes

- The long term history of the fault is calculated following (Tesson & Benedetti 2019)
and is now calculated as a function of the longterm relief

**What is the format for the data files?**

All your data files must be in .txt format. '/n'
The chemistry of the samples must be stored in a "data.txt" file
The chemistry of the colluvium must be stored in a "coll.txt" file
The magnetic filed data must be stored in "sf.txt" file.
For further formating see "format_you_data.pdf"

**How do I use EQCHLORINE ?**

Make sure your "data.txt", "coll.txt" and "sf.txt" files are in the correct format.
Copy your data files in your working directory (same directory of the "run_forward.py" file)
Open "parameter.py" and enter your site parameters.
Open "seismic_scenario.py" and set your earthquake sequence.

1) From a terminal window, run the following command :

```
python3 run_forward.py
```

2) From IDE (PyCharm, Spyder, ...) :
Open "run_forward.py" and hit the run button

Few files will be created:
- "results.txt" file will be created and will contain the resulting chlorine 36 concentration profile.
- "plot.png" plot with the synthetic profile associated with the long-term history and the final chlorine 36 concentration profile.
- "inputs.pckl" file, the input paramters you used to generate the profile

**What does my package contain ?**

LICENSE.txt : the declared license
README.md : the read_me file
src : folder with the source code 

In the src folder, you will find :

- constants.py : all the constants used
- parameters.py : inputs parameters
- seismic_scenario.py : the input seismic sequence
- chemistry_scaling.py : functions that calculates the 36cl concentration due to chemistry
- geometric_scaling.py : functions that calculates the incident cosmogenic flux
- forward_function.py : the main function from which the final 36cl is calculated
- run_forward.py : script to run the code

You can also find a "util" folder containing basic functions used in the geometric_scaling.py

**I have more questions!**
