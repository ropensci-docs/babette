# Get the full path of a file in the `inst/extdata` folder

Get the full path of a file in the `inst/extdata` folder

## Usage

``` r
get_babette_path(filename)
```

## Arguments

- filename:

  the file's name, without the path

## Value

the full path of the filename, if and only if the file is present. Will
stop otherwise.

## See also

for more files, use
[`get_babette_paths`](https://docs.ropensci.org/babette/reference/get_babette_paths.md)

## Author

Richèl J.C. Bilderbeek

## Examples

``` r
beastier::remove_beaustier_folders()
beastier::check_empty_beaustier_folders()

get_babette_path("anthus_aco.fas")
#> [1] "/github/home/R/x86_64-pc-linux-gnu-library/4.6/babette/extdata/anthus_aco.fas"

beastier::remove_beaustier_folders()
beastier::check_empty_beaustier_folders()
```
