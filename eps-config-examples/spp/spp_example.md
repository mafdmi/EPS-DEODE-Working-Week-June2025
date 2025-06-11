# Example: Running CY49t2 with SPP

To run an DEODE 1+2 ensemble with SPP enabled, you can take the `./lspp.toml` file as a starting point and modify it as needed. Remember to update the start date to your needs.

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