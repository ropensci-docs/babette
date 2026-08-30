# Get the full paths of files in the `inst/extdata` folder

Get the full paths of files in the `inst/extdata` folder

## Usage

``` r
get_babette_paths(filenames)
```

## Arguments

- filenames:

  the files' names, without the path

## Value

the filenames' full paths, if and only if all files are present. Will
stop otherwise.

## See also

for one file, use
[`get_babette_path`](https://docs.ropensci.org/babette/reference/get_babette_path.md)

## Author

Richèl J.C. Bilderbeek

## Examples

``` r
beastier::remove_beaustier_folders()
beastier::check_empty_beaustier_folders()

get_babette_paths(c("anthus_aco.fas", "anthus_nd2.fas"))
#> [1] "/github/home/R/x86_64-pc-linux-gnu-library/4.6/babette/extdata/anthus_aco.fas"
#> [2] "/github/home/R/x86_64-pc-linux-gnu-library/4.6/babette/extdata/anthus_nd2.fas"

beastier::remove_beaustier_folders()
beastier::check_empty_beaustier_folders()
```
