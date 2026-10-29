# Process the 'BEAST2' output dependent on 'BEAST2' package specifics

Process the 'BEAST2' output dependent on 'BEAST2' package specifics

## Usage

``` r
parse_beast2_output(out, inference_model)
```

## Arguments

- out:

  a list with the complete babette output, with elements:

  - `output` textual output of a 'BEAST2' run

- inference_model:

  a Bayesian phylogenetic inference model, as returned by
  [create_inference_model](https://docs.ropensci.org/beautier/reference/create_inference_model.html)

## Value

complete babette output with added attributes, which depends on the
'BEAST2' package.

- `marg_log_lik` the marginal log likelihood estimate

- `marg_log_lik_sd` the standard deviation around the estimate

- `estimates` the parameter estimates created during the marginal
  likelihood estimation

- `trees` the trees created during the marginal likelihood estimation

## Author

Richèl J.C. Bilderbeek
