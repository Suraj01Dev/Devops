
## AWK Syntax

### `awk options "pattern/conditions {action}"`

options
- -F Field Separator
- -v var=value
- -f file


### Terms used in AWK

- NR - No of rows
- NF - No of fields
- $0 - Print everything


1. How to print the last column of the data ?
```bash
awk '{print $NF}' sample.csv
```

The $NF prints the number of fields present in the data, thus using the $NF with `awk` prints the last column.


