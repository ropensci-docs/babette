# Internal function to prepare for 'BEAST2' creating files

The inference model and 'BEAST2' options contain paths that may point to
sub-sub-sub folders. Create those folders and test if these folders can
be written to

## Usage

``` r
prepare_file_creation(inference_model, beast2_options)
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

## Examples

``` r
# This example will fail on the CRAN
# r-oldrel-macos-x86_64 platform
if (rappdirs::app_dir()$os != "mac") {
  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()

  # For a test inference model, the files can be prepared
  inference_model <- create_test_inference_model()
  beast2_options <- create_beast2_options()
  prepare_file_creation(inference_model, beast2_options)

  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()
}
```
