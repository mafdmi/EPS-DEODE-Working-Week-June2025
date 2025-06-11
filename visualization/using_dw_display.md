# Plotting a 2D field using DW-Display

To plot a 2D field using DW-Display, do the below steps:

1. Follow https://github.com/destination-earth-digital-twins/DW-Display/wiki/Personal-Setup-for-Custom-Visualizations to setup DW-Display in your environment. In case you haven't installed `poetry`, follow the README at https://github.com/destination-earth-digital-twins/DW-Display.

2. After successful setup (and installation of `poetry`), you have to create a new/adjust the existing [`dwdisplay/data/configs/config.toml`](https://github.com/destination-earth-digital-twins/DW-Display/blob/master/dwdisplay/data/configs/config.toml) file to point to the data that you want to plot. Follow the guide here: https://destination-earth-digital-twins.github.io/DW-Display/usage_examples.html#config-file-excerpts.

3. Now you should be ready to execute the plotting. Depending on your liking you can either run DW-Display from the commandline (see https://destination-earth-digital-twins.github.io/DW-Display/usage_examples.html#from-the-command-line) or through a Jupyter Notebook/Python script (see https://destination-earth-digital-twins.github.io/DW-Display/usage_examples.html#from-a-jupyter-notebook-or-python-script). You can also use the default JupyterLab notebook [`DW-Display/notebooks/default_notebook.ipynb`](https://github.com/destination-earth-digital-twins/DW-Display/blob/master/notebooks/default_notebook.ipynb) as a starting point.