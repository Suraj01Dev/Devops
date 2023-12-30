
### AWK Template
```bash
awk <options> '<pattern/condition> {command}'
```


#### Printing a column

Printing the row no 1
```bash
awk '{print $1}' sample.txt
```

Printing the row no 2
```bash
awk '{print $2}' sample.txt
```

Printing all rows
```bash
awk '{print $0}' sample.txt
```

#### Default variables in AWK

1. `NR` - No of Records
2. `NF` - No of Fields

- ##### Examples with NR
	
	1. Printing the records with line numbers.
	```bash
	awk '{print NR, $1}' sample.txt
	```
	
	2. Using conditions using `NR`
		Printing the contents at row number 3 from the dataset.
	```bash
	awk 'NR==3 {print $0}' sample.txt
	```

	3. Using `NR` to print a range of values in the dataset.
	```bash
	awk 'NR==2, NR==6 {print $0}' samples.txt
	```
	
- ##### Examples with NF

	1. NF stands for number of fields, using NF with print will print the all column of the dataset.
	```bash
	awk '{print $NF}' sample.txt
	```
	
	2. Using NF variable to print the rows with no data. (Blank Lines)
	```bash
	awk 'NF==0 {print $0}' sample.txt
	```
	

#### Using AWK with Regex 

The regex pattern in awk can be used before the command clause.
```bash
awk '/<regex pattern/{print}' samples.txt
```

Examples:
1. Printing rows with blank data.
	```bash
	awk '/^$/{print $0}' samples.txt
	```

2.  Printing rows that start with a comment.
	```bash
	awk '/^#/{print $0}' samples.txt
	```
	
3. Searching for multiple words in a dataset.
	```bash
	awk '/Word1|Word2/{print $0}' samples.txt
	```

4. Searching for a character in a specific column.
	```bash
	awk '$1 ~ /A/ {print $0}' samples.txt
	```


#### AWK with delimiters.

Using awk with a csv file with `comma` as a delimiter.
	```bash
	awk -F, '{print $0}' samples.txt
	```


Using awk with multiple delimiters.
	```bash
	awk -F[,:] '{print $0}' samples.txt
	```

#### Essential AWK Functions
- ##### length()
- ##### gsub()
- ##### tolower()
- ##### toupper()
##### Examples with length() function

1. Print the length of each row in the dataset.
	```bash
	awk '{print length($0)}' samples.txt
	```

1. Print the length of row which has max length.
	```bash
	awk 'BEGIN{max=0} {if(length($0)>max) {max=length($0); max_line=NR}} END{print max_line}' sample.txt
	```

##### Example with gsub() function
```bash
awk '{gsub('old', 'new'); print $0}' sample.txt
``` 

##### Example with tolower() function
```bash
awk '{tolower($2); print $0}' sample.txt
```

##### Example with toupper() function
```bash
awk '{toupper($2); print $0}' sample.txt
```

