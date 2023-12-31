

## Basics

```
ABCDEFGHIJKLMNOPQRSTUVWXYZ
abcdefghijklmnopqrstuvwxyz
0123456789

ace    bad    cat   dry    eve
away   bent   crow   dove   ends
attic  brand  crypt  dried  event
annoys baller camera diving ethics

bad this is new
cat this is new

```

1. Capture all 3 letter words.
```r
\b[a-z][a-z][a-z]\b
```

```r
\b[a-z]{3}\b
```

2. Capture words with 3 or more letters.
```r
\b[a-z]{3,}\b
```

3. Capture words with 3 to 4 letters.
```r
\b[a-z]{3,4}\b
```

4. Capture words which does not have vowels.
```r
\b[^aeiou\s]+\b
```


## Intermediate

```
~`!@#$%^&*()-_+=<>,./?;:'"[{
0123456789

In the future:

your toaster will be smarter than you.
Robots will take over the world, but they'll do it in style.
Augmented reality will let you pet virtual unicorns in your living room.
Quantum computing will allow you to calculate the meaning of life in seconds.
Blockchain will make your online shopping experience more secure than Fort Knox.
Cybersecurity will be so advanced, hackers will have to resort to using actual swords.
In the future, we'll all communicate through a universal language made up entirely of emojis.

```

1. Capture valid sentences. Sentences which start with a capital letter and ends with a period.
	```r
	^[A-Z].*\.$
	```

	#### Note:
	Character Classes !!
	
	- \\w - Word
		- Captures all letters, numbers and underscores.
	- \\W
		- Captures all the characters that are not a part of word class
	- \\s - space
		- Captures all the white spaces.
	- \\S -  not space
		- Captures all non white spaces.
	- \\d - digit 
	- \\D - not digit

2. Capture all 3 letter words with word class.
```r
\b\w{3}\b
```


### Exercise

```
KeItH sAyS yOu NeEd To LeArN rEgExEs

wElCoMe To ThE sAlTy SpItOoN, hOw ToUgH aRe YoU?

This is a boring, normal sentence.

lEt Me SeE tHaT sPoNgEbOb MeMe OnE mOrE tImE
```

Capture all the sponge bob meme sentences.
```r
[A-Z]?([a-z][A-Z]).+[a-z]?\??\!?
```

##  Groups Overview

```
123456789
999000999
8712388411235

mississippi
bookkeeping
aggressive
words

```

1. Find number which has repeating sequence.
	Example:
	- `222`45678`222`3891
```r
\d*(\d\d\d)\d*\1\d*
```

2. Find words which has 3 sets of repeating characters.
	 Example:
	 - mi`ss`i`ss`i`pp`i
	 - b`ookkee`ping

```r
\w*(\w)\1\w*(\w)\2\w*(\w)\3\w*
```
