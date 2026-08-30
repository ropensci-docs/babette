# Delete all the temporary files created by [bbt_run_from_model](https://docs.ropensci.org/babette/reference/bbt_run_from_model.md)

Delete all the temporary files created by
[bbt_run_from_model](https://docs.ropensci.org/babette/reference/bbt_run_from_model.md)

## Usage

``` r
bbt_delete_temp_files(inference_model, beast2_options)
```

## Arguments

- inference_model:

  a Bayesian phylogenetic inference model, as returned by
  [create_inference_model](https://docs.ropensci.org/beautier/reference/create_inference_model.html)

- beast2_options:

  'BEAST2' options, as can be created by
  [create_beast2_options](https://docs.ropensci.org/beastier/reference/create_beast2_options.html)

## Value

Nothing.

## Author

Richèl J.C. Bilderbeek

## Examples

``` r
if (beautier::is_on_ci() && is_beast2_installed()) {
  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()

  # Do a minimal run
  inference_model <- create_test_inference_model()
  beast2_options <- create_beast2_options()
  bbt_run_from_model(
    fasta_filename = get_fasta_filename(),
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
