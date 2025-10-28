# poppy_uppsala_config

A repository for storing Uppsala specific configurations of the poppy-uppsala pipeline in production.

This includes configuration files for different offline and online environments 
(e.g. miarka and marvin compute clusters) 
as well as a list of the design and reference data files with their checksums on CGU's compute cluster.

As poppy-uppsala is based on [poppy GMS](https://github.com/genomic-medicine-sweden/poppy),
a configuration file for poppy is also included here. 
Note that poppy GMS uses its own versions of various modules from [hydra-genetics](https://github.com/hydra-genetics).

**Important**: The module `snv_indels` from `hydra-genetics` is included twice in the Snakefiles:
- once as part of poppy GMS (version v0.6.0) 
- once as part of poppy-uppsala (version v1.1.0) 

It is essential that both versions are kept and used in the correct order to avoid 
Snakemake raising errors in the workflow such as "MissingInputException" or "AmbiguousRuleException".
If the module versions are specified in the config file as they are for miarka, you should use 
distinct keys `snv_indels_gms` and `snv_indels_uppsala` to avoid overloading what version is used
in the different steps of the workflow.
