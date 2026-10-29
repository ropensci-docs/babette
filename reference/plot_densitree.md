# Draw multiple trees on top of one another.

Draw multiple trees on top of one another.

## Usage

``` r
plot_densitree(phylos, ...)
```

## Arguments

- phylos:

  one or more phylogenies, must be of class `multiPhylo`

- ...:

  options to be passed to `phangorn`'s
  [densiTree](https://klausvigo.github.io/phangorn/reference/densiTree.html)
  function

## Value

nothing. Will produce a plot.

## Author

Richèl J.C. Bilderbeek

## Examples

``` r
if (beautier::is_on_ci() && is_beast2_installed()) {
  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()

  inference_model <- create_test_inference_model()
  beast2_options <- create_beast2_options()

   out <- bbt_run_from_model(
    get_babette_path("anthus_aco.fas"),
    inference_model = inference_model,
    beast2_options = beast2_options
  )
  bbt_delete_temp_files(
    inference_model = inference_model,
    beast2_options = beast2_options
  )

  plot_densitree(out$anthus_aco_trees)

  # Clean up temporary files created by babette
  bbt_delete_temp_files(
    inference_model = inference_model,
    beast2_options = beast2_options
  )
  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()
}
```
