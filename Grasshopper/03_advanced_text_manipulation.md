# **Advanced Text**

## **regex** (Regular Expressions)
```regex``` is  powerfull tool for select  pattern in text.

using this phrase:
```sh
sally sells seashells 
by the seashore
```

* Beginning of a line with ```^```:
```sh
^by  

would match the line "by the seashore"
```

* End of a line with ```$```:
```sh
seashore$  

would match the line "by the seashore"
```

* Matching any single character with ```.```:
```sh
b.  

would match by
```

* Bracket notation with ```[]```:
_brackets allow to specify characters found within the bracket:_
```sh
d[iou]g

would match: dig, dog, dug
```

_tag ```^``` when used in a bracket means anything except the characters within the bracket:_
```sh
d[^i]g

would match: dog and dug but not dig
```

_use ranges to increase the amount of characters you want to use:_
```sh
d[a-c]g

will match patterns like dag, dbg, and dcg
```

**note:***  brackets are case sensitive:
```sh
d[A-C]g

will match dAg, dBg and dCg but not dag, dbg and dcg
```

* combine with ```grep```:
```sh
grep [regular expression here] [file]
```


## **Text Editors**
_Vim_
_emacs_



## **Vim** (Vi Improved)
* To fire up ```vim``` just type:
```sh
vim
```


