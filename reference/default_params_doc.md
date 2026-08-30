# This function does nothing. It is intended to inherit is parameters' documentation.

This function does nothing. It is intended to inherit is parameters'
documentation.

## Usage

``` r
default_params_doc(
  beast2_input_filename,
  beast2_options,
  beast2_output_log_filename,
  beast2_output_state_filename,
  beast2_output_trees_filenames,
  beast2_path,
  beast2_working_dir,
  cleanup,
  clock_model,
  clock_models,
  fasta_filename,
  fasta_filenames,
  inference_model,
  mcmc,
  mrca_prior,
  mrca_priors,
  overwrite,
  rng_seed,
  site_model,
  site_models,
  tipdates_filename,
  tree_prior,
  tree_priors,
  verbose
)
```

## Arguments

- beast2_input_filename:

  path of the 'BEAST2' configuration file. By default, this file is put
  in a temporary folder with a random filename, as the user needs not
  read it: it is used as input of 'BEAST2'. Specifying a
  `beast2_input_filename` allows to store that file in a more
  permanently stored location.

- beast2_options:

  'BEAST2' options, as can be created by
  [create_beast2_options](https://docs.ropensci.org/beastier/reference/create_beast2_options.html)

- beast2_output_log_filename:

  name of the log file created by 'BEAST2', containing the parameter
  estimates in time. By default, this file is put a temporary folder
  with a random filename, as the user needs not read it: its content is
  parsed and returned by this function. Specifying a
  `beast2_output_log_filename` allows to store that file in a more
  permanently stored location.

- beast2_output_state_filename:

  name of the final state file created by 'BEAST2', containing the
  operator acceptances. By default, this file is put a temporary folder
  with a random filename, as the user needs not read it: its content is
  parsed and returned by this function. Specifying a
  `beast2_output_state_filename` allows to store that file in a more
  permanently stored location.

- beast2_output_trees_filenames:

  name of the one or more trees files created by 'BEAST2', one per
  alignment. By default, these files are put a temporary folder with a
  random filename, as the user needs not read it: their content is
  parsed and returned by this function. Specifying
  `beast2_output_trees_filenames` allows to store these one or more
  files in a more permanently stored location.

- beast2_path:

  name of either a 'BEAST2' binary file (usually simply `beast`) or a
  'BEAST2' jar file (usually has a `.jar` extension). Use
  `get_default_beast2_bin_path` to get the default BEAST binary file's
  path Use `get_default_beast2_jar_path` to get the default BEAST jar
  file's path

- beast2_working_dir:

  the folder 'BEAST2' will work in. This is an (empty) temporary folder
  by default. This allows to call 'BEAST2' in multiple parallel
  processes, as each process can have its own working directory

- cleanup:

  set to FALSE to keep all temporary files

- clock_model:

  one clock model, see
  [create_clock_model](https://docs.ropensci.org/beautier/reference/create_clock_model.html)

- clock_models:

  one or more clock models, see
  [create_clock_models](https://docs.ropensci.org/beautier/reference/create_clock_models.html)

- fasta_filename:

  a FASTA filename

- fasta_filenames:

  one or more FASTA filename, each with one alignment

- inference_model:

  a Bayesian phylogenetic inference model, as returned by
  [create_inference_model](https://docs.ropensci.org/beautier/reference/create_inference_model.html)

- mcmc:

  the MCMC options, see
  [create_mcmc](https://docs.ropensci.org/beautier/reference/create_mcmc.html)

- mrca_prior:

  one Most Recent Common Ancestor prior, as returned by
  [`create_mrca_prior`](https://docs.ropensci.org/beautier/reference/create_mrca_prior.html)

- mrca_priors:

  a list of one or more Most Recent Common Ancestor priors, as returned
  by
  [`create_mrca_prior`](https://docs.ropensci.org/beautier/reference/create_mrca_prior.html)

- overwrite:

  will 'BEAST2' overwrite files? Like 'BEAST2', this is set to
  [TRUE](https://rdrr.io/r/base/logical.html) by default. If
  [TRUE](https://rdrr.io/r/base/logical.html), 'BEAST2' will overwrite
  the `beast2_options$output_state_filename` if its present. If
  [FALSE](https://rdrr.io/r/base/logical.html), 'BEAST2' will not
  overwrite the `beast2_options$output_state_filename` if its present
  and
  [babette](https://docs.ropensci.org/babette/reference/babette-package.md)
  will give an error message. Note that if `overwrite` is set to
  [FALSE](https://rdrr.io/r/base/logical.html) when a `tracelog` (see
  [create_tracelog](https://docs.ropensci.org/beautier/reference/create_tracelog.html)),
  `screenlog` (see
  [create_screenlog](https://docs.ropensci.org/beautier/reference/create_screenlog.html))
  or `treelog` (see
  [create_treelog](https://docs.ropensci.org/beautier/reference/create_treelog.html))
  file already exists, 'BEAST2' (and thus
  [babette](https://docs.ropensci.org/babette/reference/babette-package.md))
  will freeze.

- rng_seed:

  the random number generator seed. Must be either `NA` or a positive
  non-zero value. An RNG seed of `NA` results in 'BEAST2' picking a
  random seed.

- site_model:

  one site model, see
  [create_site_models](https://docs.ropensci.org/beautier/reference/create_site_models.html)

- site_models:

  one or more site models, see
  [create_site_models](https://docs.ropensci.org/beautier/reference/create_site_models.html)

- tipdates_filename:

  name of the file containing tip dates

- tree_prior:

  one tree priors, as created by
  [create_tree_prior](https://docs.ropensci.org/beautier/reference/create_tree_prior.html)

- tree_priors:

  one or more tree priors, see
  [create_tree_priors](https://docs.ropensci.org/beautier/reference/create_tree_priors.html)

- verbose:

  set to TRUE for more output

## Note

This is an internal function, so it should be marked with `@noRd`. This
is not done, as this will disallow all functions to find the
documentation parameters

## Author

Richèl J.C. Bilderbeek
