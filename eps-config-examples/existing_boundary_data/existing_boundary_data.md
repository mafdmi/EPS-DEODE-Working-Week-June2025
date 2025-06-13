# Running an ensemble with existing boundary data

To run a DEODE 1+6 ensemble on existing boundary data fetched from mars, you can take the below TOML configuration (also available in `EPS-DEODE-Working-Week-June2025/eps-config-examples/existing_boundary_data/6member_IFSENS.toml`) file as a starting point and modify it as needed.

```toml
[submission]
  account = "#SBATCH -A msdeode"

[system]
  marsdir = "/scratch/snh02/deode/IFS/IFSENS/@YYYY@/@MM@/@DD@/@HH@"

[general] 
  csc = "HARMONIE_AROME"

[general.times]
  forecast_range = "PT6H"
  start = "2025-05-25T00:00:00Z"


[domain]
  gridtype_oro = "cubic"
  ilate = 11
  ilone = 11
  lspsmoro = false
  name = "EPS_1_6"
  nbzong = 28
  nbzonl = 28
  ndglg = 1000
  ndguxg = 1000
  nimax = 989
  njmax = 989
  nmsmax = 249
  nmsmax_oro = 249
  nsmax = 249
  nsmax_oro = 249
  orographic_smoothing_method = "spectral"
  tstep = 15
  xdx = 750
  xdy = 750
  xlatcen = 60.1
  xloncen = 8.2

[boundaries.ifs]
  bdmembers = [0, 1, 2, 3, 4, 5, 6]
  selection = "IFSENS"

[eps.general]
  members = "0:7"

[eps.member_settings.boundaries.ifs]
  bdmember = "@MEMBER@"
```