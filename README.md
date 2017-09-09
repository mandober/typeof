# NAME
`typeof` - variable typing and dumping


## SYNOPSIS
`typeof [-b|--brief] NAME`


## DESCRIPTION
Type NAME as indexed array, associative array or variable. Dump indexed and associative arrays and variables along with their attributes. A NAME is first passed to `type` bash builtin that will return `alias`, `keyword`, `function`, `builtin` or `file` if NAME is one of these. If not, NAME is presumed to be a variable: `indexed` or `associative` is returned if it is an array, `scalar` oterwise.


## OPTIONS
`-b, --brief`    
only the type, as a single string, is returned. Returned types:
- `scalar`
- `indexed` (indexed array)
- `associative` (associative array)
- `alias`
- `keyword`
- `function`
- `builtin`
- `file`    
Without this option, output is more verbose.   


## OPERANDS
`NAME`
Parameter NAME can be anything: variable's name, identifier, shell keyword, 


## STDOUT
Print results.    
Help, usage, version (to STOUT only if explicitly requested).


## STDERR
Error messages, help and usage.


## RETURN STATUS
0  success
1  failure
2  NAME is not anything significant


## EXAMPLES

````shell
$ typeof -b BASH_VERSINFO
indexed

$ typeof -b BASH_ALIASES
associative

$ typeof BASH_VERSINFO
    Name: BASH_VERSINFO
    Type: indexed array [6]		# [6] - number of elements
   Value:
     [0]: 4 [1]				# [1] - length of an element
     [1]: 3 [1]
     [2]: 42 [2]
     [3]: 4 [1]
     [4]: release [7]
     [5]: x86_64 [6]
    Attr: -r (readonly)

$ typeof BASH_ALIASES
   Name: BASH_ALIASES
   Type: associative array [4]
  Value:
     [la]: ls -la    [6]
   [cd..]: cd ..     [5]
  [unset]:           [0]	# null value
     [sv]: sudo vim  [8]
   
$ typeof UID
   Name: UID
   Type: variable
  Value: 101  		[3]
   Attr: 
       -i (integer)
       -r (readonly)
````


## SEE ALSO
[barf](https://github.com/mandober/barf) - bash array-related functions.


### ID TAG
```
   FILE: typeof
   TYPE: bash function
    WEB: https://github.com/mandober/typeof
 AUTHOR: Ilic Ivan <ilicivan@zoho.com>
LICENSE: MIT
   DATE: 09-Sep-2017 (last revision)
```