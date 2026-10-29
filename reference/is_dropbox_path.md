# Detect if a path is inside a Dropbox-backed folder

This helper function checks whether a given file or directory path
appears to be located inside a Dropbox-synced folder. It is used to warn
users about potential file-locking issues when running BEAST2 from
Dropbox-backed locations.

## Usage

``` r
is_dropbox_path(path)
```

## Arguments

- path:

  A character string representing a file or directory path.

## Value

`TRUE` if the path appears to be in a Dropbox folder, `FALSE` otherwise.

## Details

The detection is based on simple case-insensitive string matching and is
intended as a best-effort heuristic rather than a guarantee.

## Examples

``` r
is_dropbox_path("~/Dropbox/myproject")
#> [1] TRUE
is_dropbox_path("/tmp/myproject")
#> [1] FALSE
```
