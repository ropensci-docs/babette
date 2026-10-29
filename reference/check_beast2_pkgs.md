# Checks if [`bbt_run`](https://docs.ropensci.org/babette/reference/bbt_run.md) has the 'BEAST2' packages needed to process its arguments. Will [stop](https://rdrr.io/r/base/stop.html) if not.

For example, to use a Nested Sampling MCMC, the 'BEAST2' 'NS' package
needs to be installed.

## Usage

``` r
check_beast2_pkgs(mcmc, beast2_path = get_default_beast2_bin_path())
```

## Arguments

- mcmc:

  the MCMC options, see
  [create_mcmc](https://docs.ropensci.org/beautier/reference/create_mcmc.html)

- beast2_path:

  name of either a 'BEAST2' binary file (usually simply `beast`) or a
  'BEAST2' jar file (usually has a `.jar` extension). Use
  `get_default_beast2_bin_path` to get the default BEAST binary file's
  path Use `get_default_beast2_jar_path` to get the default BEAST jar
  file's path

## Value

Nothing.

## Examples

``` r
if (beautier::is_on_ci() && is_beast2_installed()) {
  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()

  # Minimal BEAST2 setup
  check_beast2_pkgs(mcmc = create_mcmc())

  # BEAST2 with NS package installed
  if (is_beast2_ns_pkg_installed()) {
    check_beast2_pkgs(mcmc = create_ns_mcmc())
  }

  beastier::remove_beaustier_folders()
  beastier::check_empty_beaustier_folders()
}
```
