# Running CY49t2 with SPP

To run an DEODE 1+2 ensemble with SPP enabled, you can take the below TOML configuration (also available in `EPS-DEODE-Working-Week-June2025/eps-config-examples/spp/lspp.toml`) file as a starting point and modify it as needed. Remember to update the start date to your needs.

```toml
[general.times]
  start = "2025-06-01T00:00:00Z"

[boundaries.ifs]
  bdmembers = [0, 1, 2]
  selection = "IFSENS"

[eps]

[eps.general]
  members = [0, 1, 2]

[eps.member_settings]

[eps.member_settings.boundaries.ifs]
  bdmember = [0, 1, 2]

[eps.member_settings.namelist_update.master.forecast.nam_spp_active]
  "requested_perts(1)" = "PSIGQSAT"

[eps.member_settings.namelist_update.master.forecast.nam_spp_modif]
  "pnx(1)%idistr" = 1
  "pnx(1)%label" = "PSIGQSAT"
  "pnx(1)%ln1" = true
  "pnx(1)%xmag(1)" = 0.6

[eps.member_settings.namelist_update.master.forecast.namspp]
  cspp_model_name = "lam"
  iezdiag_pos = {0 = 1, "1:" = -1}
  lspg_spp = {0 = false, "1:" = true}
  lspp = {0 = false, "1:" = true}
  npatfr = 1
  spgadtmax = 3.0
  spgadtmin = 0.15
  spglambda = -999.0
  spgmaxsubsteps = 50
  spgmu = -999.0
  spgq = 0.5
  spgsigma = -999.0

[eps.member_settings.system]
  wrk = "@CASEDIR@/@YYYY@@MM@@DD@_@HH@@mm@/@MEMBER_STR@"
```

To generate a config file with SPP enabled, run
```
cd /path/to/Deode-Workflow
poetry run deode case --config-file ./deode/data/config-files/config.toml /path/to/lspp.toml ./deode/data/config_files/modifications/cycle/CY49t2.toml
```

To also start the suite, add the `--start-suite` flag to the above command, or execute
```
poetry run deode start suite --config-file /path/to/config.toml 
```
where `/path/to/config.toml` is the path to the config file generated above.