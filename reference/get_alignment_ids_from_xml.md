# Get the alignment IDs from one or more 'BEAST2' XML input files.

Get the alignment IDs from one or more 'BEAST2' XML input files.

## Usage

``` r
get_alignment_ids_from_xml(xml_filename)
```

## Arguments

- xml_filename:

  name of a 'BEAST2' XML input file.

## Value

a character vector with one or more alignment IDs.

## Author

Richèl J.C. Bilderbeek

## Examples

``` r
beastier::remove_beaustier_folders()
beastier::check_empty_beaustier_folders()

alignment_ids <- get_alignment_ids_from_xml(
  get_babette_path("anthus_2_4.xml")
)

beastier::remove_beaustier_folders()
beastier::check_empty_beaustier_folders()
```
