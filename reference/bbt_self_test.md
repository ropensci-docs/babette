# Do a self test to verify [babette](https://docs.ropensci.org/babette/reference/babette-package.md) that works correctly.

Do a self test to verify
[babette](https://docs.ropensci.org/babette/reference/babette-package.md)
that works correctly.

## Usage

``` r
bbt_self_test(beast2_options = beastier::create_beast2_options())
```

## Arguments

- beast2_options:

  'BEAST2' options, as can be created by
  [create_beast2_options](https://docs.ropensci.org/beastier/reference/create_beast2_options.html)

## Value

Nothing. Will raise an exception if something is wrong.

## Author

Richèl J.C. Bilderbeek

## Examples

``` r
if (beautier::is_on_ci() && is_beast2_installed()) {
  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()

  bbt_self_test()

  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()
}
```
