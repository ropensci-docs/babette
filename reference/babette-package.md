# babette: A package for Bayesian phylogenetics.

'babette' provides for an alternative workflow of using the popular
phylogenetics tool 'BEAST2', including it peripheral tools. From an
alignment and inference model, a posterior of jointly estimated
phylogenies and parameter estimates is generated.

## Note

the imports are created by script 'scripts/create_imports.R'

## See also

Use
[bbt_self_test](https://docs.ropensci.org/babette/reference/bbt_self_test.md)
to do verify babette is installed correctly.  

These are packages associated with 'babette':

- '[beautier](https://docs.ropensci.org/beautier/reference/beautier-package.html)'
  creates 'BEAST2' input files.

- '[beastier](https://docs.ropensci.org/beastier/reference/beastier-package.html)'
  runs 'BEAST2'.

- '[mauricer](https://docs.ropensci.org/mauricer/reference/mauricer-package.html)'
  does 'BEAST2' package management.

- '[tracerer](https://docs.ropensci.org/tracerer/reference/tracerer-package.html)'
  parses 'BEAST2' output files.

## Author

Richèl J.C. Bilderbeek

## Examples

``` r
if (beautier::is_on_ci() && is_beast2_installed()) {
  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()

  inference_model <- create_test_inference_model()
  beast2_options <- create_beast2_options()

  bbt_run_from_model(
    fasta_filename = get_babette_path("anthus_aco.fas"),
    inference_model = inference_model,
    beast2_options = beast2_options
  )

  # Clean up temporary files created by babette
  bbt_delete_temp_files(
    inference_model = inference_model,
    beast2_options = beast2_options
  )
  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()
}
beastier::remove_beaustier_folders()
```
