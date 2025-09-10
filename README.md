# 1column-diff

Ever have data like a list of cities and popultaions, but you don't want to know what changed, just what cities were added?

This tool takes 2 different sets of tabular data, and diff's only the specified columns.

## Example

Using US Census data for Illinois

    wget -O sub-est2010-allus.csv https://www2.census.gov/programs-surveys/popest/datasets/2010/2010-eval-estimates/sub-est2010.csv
    head -1 sub-est2010-allus.csv > sub-est2010-il.csv
    grep Illinois sub-est2010-allus.csv >> sub-est2010-il.csv
    wget -o sub-est2020.csv https://www2.census.gov/programs-surveys/popest/datasets/2010-2020/cities/SUB-EST2020_17.csv

Now that data is prepped, we can see which cities were added:

    ./1column-diff --file2 ./sub-est2010-il.csv --file1 ./SUB-EST2020_17.csv -k1 9 -k2 7 -t ,

And you will see that Astoria Town was a new town in 2020 (removed in the 2010 set)



