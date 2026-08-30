# Parse BEAST2 NS output

Parse the BEAST2 output when run with the BEAST2 NS ('Nested Sampling')
package.

## Usage

``` r
parse_beast2_output_to_ns(output)
```

## Arguments

- output:

  screen output

## Value

a list with the following elements:

- `marg_log_lik` the marginal log likelihood estimate

- `marg_log_lik_sd` the standard deviation around the estimate

## See also

use
[`create_test_ns_output`](https://docs.ropensci.org/babette/reference/create_test_ns_output.md)
to obtain a test screen output.

## Author

Richèl J.C. Bilderbeek

## Examples

``` r
beastier::remove_beaustier_folders()
beastier::check_empty_beaustier_folders()

parse_beast2_output_to_ns(
  output = create_test_ns_output()
)
#> $marg_log_lik
#> [1] -141.1645
#> 
#> $marg_log_lik_sd
#> [1] 1.160143
#> 
#> $ess
#> [1] 5.659472
#> 

beastier::remove_beaustier_folders()
beastier::check_empty_beaustier_folders()
```
