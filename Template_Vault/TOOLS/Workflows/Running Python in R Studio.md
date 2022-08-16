# Running Python Code in R-Studio
Let me tell you, you can fall into a rabbit hole quite easily in this pursue. At the same time there are multiple and very simple ways to run python code in rmarkdown. After spending hours trying multiple instalations and hitting dead ends, this is what it worked for me in a Windows 10 Machine: 

This [Python in RStudio video](https://www.youtube.com/watch?v=OtINRCXprGg&ab_channel=IDGTECHtalk). The most helpfulp part was in the second slide, for a "super easy" local installation of python. In R or in the RStudio console run:

```
install.packages("reticulate")
library(reticulate)
install_miniconda
```

It was indeed extremely easy to run.  Then, you probably know some of the Python packages you want to use. If this is the case, just go for it and install them typing this into the console: 

```
py_install('Numpy')#for working with arraus (e.g. linear algebra)
py_install('pandas')#for data analysis and manipulation
py_install('scipy')#scienctific calculations
py_install('statsmodel')# for statistical analysis (regressions, etc)
py_install('matplotlib')# for data visualization
py_install('spacy')#for natural language processing
```

  WARNING: The script jupyter-console.exe is installed in 'C:\Users\guer310\AppData\Local\Programs\Python\Python310\Scripts' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location...
