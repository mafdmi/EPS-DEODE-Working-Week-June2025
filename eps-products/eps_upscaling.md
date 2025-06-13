# Calculating ensemble products with the eps-upscaling package

You can use the tool `eps-upscaling` developed by Henrik F and made available by Martin F at https://github.com/mafdmi/eps-upscaling to calculate
- probabilities of crossing specified thresholds
- percentiles
- ensemble means

Please ask Martin F to get access to the repository. Then follow the instructions in the README to install the package and get started.

# Visualization of upscaled fields

You can use the `DW-Display` package to plot the upscaled fields. Follow the instructions in [using DW-Display](visualization/using_dw_display.md) to set up DW-Display.

As a starting point, you can use the config file outlined below for plotting 2m temperature probabilities, percentiles or ensemble means (also available in `EPS-DEODE-Working-Week-June2025/eps-products/config_eps_upscaling.toml`):

```toml
[general]
input_directory_template = "/scratch/$USER/deode/$CASE_NAME/archive/epsupscale/perc"
input_filename_template = "out_T2m_GRIBPFDEOD+{leadtime}.grb2"
output_directory = "/scratch/$USER/dw_plots/eps_upscaling"
output_filename_template = "{shortname}_{init_datetime}_ensmean"

[case]
initdate = "2025-05-25"
inittime = "00:00"


[plots.field.2t_prob]
name = "Probability temperature above 15deg"
shortnames = ["2t"]
unit = "probability"
type_of_level = "heightAboveGround"
level = 2
leadtimes = ["PT0H:PT6H:PT1H"]
step_type = "instant"
plot_type = "pcolormesh"
msl_contours = false
animate = true
clim = [0, 1, 0.1]
cmap = "Reds"

[plots.field.2t_prob.shortnames_renamed]
t2m = "2t"

[plots.field.2t_prob.extra_filter_by_keys]
backgroundProcess = 1
scaledValueOfUpperLimit = 288

[plots.field.2t_perc]
name = "Percentile 75, temperature"
shortnames = ["2t"]
unit = "C"
offset = -273.15
type_of_level = "heightAboveGround"
level = 2
leadtimes = ["PT0H:PT6H:PT1H"]
step_type = "instant"
plot_type = "pcolormesh"
msl_contours = false
animate = true
clim = [-5, 20, 1]
cmap = "RdBu_r"

[plots.field.2t_perc.shortnames_renamed]
t2m = "2t"

[plots.field.2t_perc.extra_filter_by_keys]
backgroundProcess = 1
percentileValue = 75

[plots.field.2t_mean]
name = "ENS mean, temperature"
shortnames = ["2t"]
unit = "C"
offset = -273.15
type_of_level = "heightAboveGround"
level = 2
leadtimes = ["PT0H:PT6H:PT1H"]
step_type = "instant"
plot_type = "pcolormesh"
msl_contours = false
animate = true
clim = [-5, 20, 1]
cmap = "RdBu_r"

[plots.field.2t_mean.shortnames_renamed]
t2m = "2t"

[plots.field.2t_mean.extra_filter_by_keys]
backgroundProcess = 255
```