# Run BEAST2

Do a full BEAST2 run: create a 'BEAST2' configuration file (like 'BEAUti
2'), run 'BEAST2', parse results (like 'Tracer')

## Usage

``` r
bbt_run(
  fasta_filename,
  tipdates_filename = NA,
  site_model = beautier::create_jc69_site_model(),
  clock_model = beautier::create_strict_clock_model(),
  tree_prior = beautier::create_yule_tree_prior(),
  mrca_prior = NA,
  mcmc = beautier::create_mcmc(),
  beast2_input_filename = beastier::create_temp_input_filename(),
  rng_seed = 1,
  beast2_output_state_filename = beastier::create_temp_state_filename(),
  beast2_path = beastier::get_default_beast2_path(),
  overwrite = TRUE,
  verbose = FALSE
)
```

## Arguments

- fasta_filename:

  a FASTA filename

- tipdates_filename:

  name of the file containing tip dates

- site_model:

  one site model, see
  [create_site_models](https://docs.ropensci.org/beautier/reference/create_site_models.html)

- clock_model:

  one clock model, see
  [create_clock_model](https://docs.ropensci.org/beautier/reference/create_clock_model.html)

- tree_prior:

  one tree priors, as created by
  [create_tree_prior](https://docs.ropensci.org/beautier/reference/create_tree_prior.html)

- mrca_prior:

  one Most Recent Common Ancestor prior, as returned by
  [`create_mrca_prior`](https://docs.ropensci.org/beautier/reference/create_mrca_prior.html)

- mcmc:

  the MCMC options, see
  [create_mcmc](https://docs.ropensci.org/beautier/reference/create_mcmc.html)

- beast2_input_filename:

  path of the 'BEAST2' configuration file. By default, this file is put
  in a temporary folder with a random filename, as the user needs not
  read it: it is used as input of 'BEAST2'. Specifying a
  `beast2_input_filename` allows to store that file in a more
  permanently stored location.

- rng_seed:

  the random number generator seed. Must be either `NA` or a positive
  non-zero value. An RNG seed of `NA` results in 'BEAST2' picking a
  random seed.

- beast2_output_state_filename:

  name of the final state file created by 'BEAST2', containing the
  operator acceptances. By default, this file is put a temporary folder
  with a random filename, as the user needs not read it: its content is
  parsed and returned by this function. Specifying a
  `beast2_output_state_filename` allows to store that file in a more
  permanently stored location.

- beast2_path:

  name of either a 'BEAST2' binary file (usually simply `beast`) or a
  'BEAST2' jar file (usually has a `.jar` extension). Use
  `get_default_beast2_bin_path` to get the default BEAST binary file's
  path Use `get_default_beast2_jar_path` to get the default BEAST jar
  file's path

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

- verbose:

  set to TRUE for more output

## Value

a list with the following elements:  

- `estimates`: a data frame with 'BEAST2' parameter estimates

- `[alignment_id]_trees`: a `multiPhylo` containing the phylogenies in
  the 'BEAST2' posterior. `[alignment_id]` is the ID of the alignment.
  For example, when running `bbt_run` with `anthus_aco.fas`, this
  element will have name `anthus_aco_trees`

- `operators`: a data frame with the 'BEAST2' MCMC operator acceptances

- `output`: a numeric vector with the output sent to standard output and
  error streams

- `ns`: (optional) the results of a marginal likelihood estimation, will
  exist only when
  [`create_ns_mcmc`](https://docs.ropensci.org/beautier/reference/create_ns_mcmc.html)
  was used for the MCMC. This structure will contain the following
  elements:

  - `marg_log_lik` the marginal log likelihood estimate

  - `marg_log_lik_sd` the standard deviation around the estimate

  - `estimates` the parameter estimates created during the marginal
    likelihood estimation

  - `trees` the trees created during the marginal likelihood estimation

## Details

Prefer using
[`bbt_run_from_model`](https://docs.ropensci.org/babette/reference/bbt_run_from_model.md),
as it has a cleaner interface.

## See also

Use
[`remove_burn_ins`](https://docs.ropensci.org/tracerer/reference/remove_burn_ins.html)
to remove the burn-ins from the posterior's estimates
(`posterior$estimates`)

## Author

Richèl J.C. Bilderbeek

## Examples

``` r
if (beautier::is_on_ci() && is_beast2_installed()) {
  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()

  # Setup for a short run
  mcmc <- create_test_mcmc()

  # Store filenames for cleanup.
  # Note that 'bbt_run_from_model allows for easier cleanup
  mcmc$tracelog$filename <- tempfile()
  mcmc$treelog$filename <- tempfile()
  mcmc$screenlog$filename <- tempfile()
  beast2_input_filename <- tempfile()
  beast2_output_state_filename <- tempfile()

  bbt_run(
    fasta_filename = get_babette_path("anthus_aco.fas"),
    beast2_input_filename = beast2_input_filename,
    beast2_output_state_filename = beast2_output_state_filename,
    mcmc = mcmc
  )

  # Cleanup
  # Again, note that 'bbt_run_from_model allows for easier cleanup
  file.remove(mcmc$tracelog$filename)
  file.remove(mcmc$treelog$filename)
  file.remove(mcmc$screenlog$filename)
  file.remove(beast2_input_filename)
  file.remove(beast2_output_state_filename)
  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()
}
```
