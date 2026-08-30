# Warn when using files in a Dropbox-backed folder

This helper function issues a warning if the supplied file or directory
path appears to be located inside a Dropbox-synced folder. Running
BEAST2 from Dropbox-backed locations may cause file-locking issues while
files are being written.

## Usage

``` r
warn_if_dropbox(path = getwd())
```

## Arguments

- path:

  A character string representing a file or directory path. Defaults to
  the current working directory.

## Value

Invisibly returns the input `path`.

## Details

The function is intended as a non-blocking safeguard and does not
prevent execution.

## Examples

``` r
warn_if_dropbox("~/Dropbox/myproject")
#> Warning: It looks like you are running babette with files in a Dropbox folder. This may cause file-locking issues (see issue #65: https://github.com/ropensci/babette/issues/65). Consider moving your project to a non-Dropbox folder.
warn_if_dropbox(tempdir())
```
