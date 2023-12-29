

1. How to print columns in AWK ?
```bash
ps aux | awk '{print $1, $2, $3}'
```

2. How to use a separator when printing columns in AWK ?
```bash
ps aux | awk '{print $1 "--" $2 "--" $3}'
```

3. How to use field separators in AWK ?
```bash
ps aux | awk -F: '{print $2}'
```

4. How to use BEGIN in AWK ?
```bash
awk 'BEGIN{printf "HI"}'
```

```bash
ps aux | awk 'BEGIN{printf "col1\tcol2\tcol3\n"} {print $1"\t"$2"\t"$3}'
```

5. How to use regex with AWK ?
```bash
cat /etc/os-release | awk ' /NAME/ {print}'
```

```bash
cat /etc/os-release | awk '/NAME/ {++c} END {print "Total Matched :", c}'
```

6. How to use length function in AWK ?
```bash
ps aux | awk '{print length($0)}'
```
The above example prints the length of every row.

The length function can also be used as a filter.
```bash
ps aux | awk ' length($0) < 100 {print}'
```

Template :
```bash
ps aux | awk ' <filter> {command}'
```

7. How to use the substitute function in AWK ?
```bash
ps aux | awk ' {sub(/root/,"suraj-user"); print}'
```

8. Write a simple AWK Script?
```bash
BEGIN {printf "col1\tcol2\tcol3\n"}
{
print $1"\t"$2"\t"$3
}
END {print "DONE"}
```
