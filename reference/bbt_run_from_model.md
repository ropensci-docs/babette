# Run BEAST2

Do a full run: create a 'BEAST2' configuration file (like 'BEAUti 2'),
run 'BEAST2', parse results (like 'Tracer')

## Usage

``` r
bbt_run_from_model(
  fasta_filename,
  inference_model = beautier::create_inference_model(),
  beast2_options = beastier::create_beast2_options()
)
```

## Arguments

- fasta_filename:

  a FASTA filename

- inference_model:

  a Bayesian phylogenetic inference model, as returned by
  [create_inference_model](https://docs.ropensci.org/beautier/reference/create_inference_model.html)

- beast2_options:

  'BEAST2' options, as can be created by
  [create_beast2_options](https://docs.ropensci.org/beastier/reference/create_beast2_options.html)

## Value

a list with the following elements:  

- `estimates`: a data frame with 'BEAST2' parameter estimates

- `[alignment_id]_trees`: a `multiPhylo` containing the phylogenies in
  the 'BEAST2' posterior. `[alignment_id]` is the ID of the alignment.
  For example, when running `bbt_run_from_model` with `anthus_aco.fas`,
  this element will have name `anthus_aco_trees`

- `operators`: a data frame with the 'BEAST2' MCMC operator acceptances

- `output`: a numeric vector with the output sent to standard output and
  error streams

- `ns`: (optional) the results of a marginal likelihood estimation, will
  exist only when `create_ns_mcmc` was used for `mcmc`. This structure
  will contain the following elements:

  - `marg_log_lik` the marginal log likelihood estimate

  - `marg_log_lik_sd` the standard deviation around the estimate

  - `estimates` the parameter estimates created during the marginal
    likelihood estimation

  - `trees` the trees created during the marginal likelihood estimation

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

  # Simple short inference
  inference_model <- create_test_inference_model()

  # Default BEAST2 options
  beast2_options <- create_beast2_options()

  bbt_run_from_model(
    fasta_filename = get_babette_path("anthus_aco.fas"),
    inference_model = inference_model,
    beast2_options = beast2_options
  )

  # Cleanup
  bbt_delete_temp_files(
    inference_model = inference_model,
    beast2_options = beast2_options
  )
  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()
}
```
