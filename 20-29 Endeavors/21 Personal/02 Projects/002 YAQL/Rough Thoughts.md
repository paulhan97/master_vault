* `WHERE` and `WHEN` are both composed of *search conditions* 

Search Condition format from ANSI-92
```
<search condition> ::=
	<boolean term>
  | <search condition> OR <boolean term>

<boolean term> ::=
	<boolean factor>
  | <boolean term> AND <boolean factor>

<boolean factor> ::=
	[ NOT ] <boolean test>

<boolean test> ::=
	<boolean primary> [ IS [ NOT ] <truth value> ]

<truth value> ::=
	TRUE
  | FALSE
  | UNKNOWN

<boolean primary> ::=
	<predicate>
  | <left paren> <search condition> <right paren>
```

A truth value is the terminal value of a predicate: "Specify a condition that can be evaluated to give a truth value of true, false, or unknown."

As YAML:
Option 1:
```
where:
	- search condition
	- search condition
```

Option 2:
```
where:
	all_of:
		- search condition
		- search condition
```

compiles to
```
where
	search condition
	and search condition
```

Types of predicates:
comparison predicates:
- equals
- not equals
- less than
- greater than
- less than or equals
- greater than or equals

Comparison predicates will have alternatives that may be longer to write but easier to read
Option 1:
```
row_value_constructor: 1
```

Option 2:
```
row_value_constructor = 1
```

Option 3:
```
row_value_constructor:
	equals: 1
```

compiles to:
```
row_value_constructor = 1
```

Other comparators will not look quite as clean for option 1
Option 1:
```
row_value_constructor: > 1
```

Option 2:
```
row_value_constructor > 1
```

Option 3:
```
row_value_constructor:
	greater_than: 1
```

Predicates can be mixed formats as part of lists:
```
- row_value_constructor: 1
- row_value_constructor < 2
```

However, the advantage of the YAQL format is to be able to have the following shorthand:
```
row_value_constructor:
	- 1
	- < 2
```

With the most readable option as:
```
row_value_constructor:
	equals: 1
	less_than: 2
```
