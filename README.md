# Learning Python

It had to happen at some point I guess... time to learn Python. These notes will be written specifically for someone that learned C several years ago, smashed around in MATLAB for a bit, currently knows R well enough to do pretty much anything they want to in R, and is learning Bash and Perl at the same time. If this is you, welcome! If not, sorry for the gaps.

### Scripts vs Shell

Python is a language. IPython is an interactive shell (which is itself tautologous, as all shells are interactive, surely?). Python is the name of the language, and there are multiple implementations of Python, including CPython (the reference implementation), PyPy (a faster implemenetation), and more. This is different to R, which is both a language AND an implementation, meaning that the R language is defined by the behaviour of the R interpreter. R runs in both script mode and interactive mode, which is again a key difference. So Python is to R as IPython is to R as CPython is to R. Easy!

### Comments

Comments start with the `#`, just like in R and Bash. Is this a rule that all scripting languages follow? I guess we'll never know.

### Basic operations

Apart from the obvious ones, exponentiation is `**` (i.e. `4**2`) instead of `^`. Why would you do this Guido? Everything else sort of makes sense. Oh, and the "assignment" operator is the same "argument" operator, which is to say that they're both `=`, unlike R (where you should use `<-` for assignment).

### Types

Python is "dynamically typed" which means that it can automatically infer the types of variables, and these types can change throughout the course of your script. This is similar to R, but **very** different to C. I don't remember how MATLAB worked. To see the type of an object in Python, use `type(var)` (is everything an object, like in R? We'll see!).

### Strings

It looks like Python accepts both single `'` and double `"` quotes, just like R. Which is nice - why wouldn't you accept both? Looking at you SQL... It also seems that you can concatenate strings using the `+` operator - cool! Python does not automatically cast between strings and other types (booooooo) which means you have to cast it explicitly when you want to build error messages, turn strings into numeric types, etc.

### Lists / Arrays / Columns / Vectors

In R, if you define something using the inline notation `c(1.73, 1.68, 1.71, 1.89)` then you are creating an "atomic vector" (i.e. a vector containing only one type of data). In Python, if you define something using the inline notation `[1.73, 1.68, 1.71, 1.89]` then are creating a "list". "List" seems to have the same meaning as R (can contain multiple types, can contain other lists, etc), so it is just the notation that differs.

### Indexing

Python uses 0-based indexing, whereas R uses 1-based indexing. If you want to select the 4th element in a vector, you would use index 4 in R (1,2,3,4), but index 3 in Python (0,1,2,3). The syntax for this is the same as R - `var[3]`. 

Negative indices work very differently! In R, a negative index will return the vector with the specified item *removed* i.e. if you use var[-3] then you will get the vector *without* the third element. In Python however, it will select a single element by *counting backwards*. An index of `-1` returns the final element (because you start at index zero and take one step backwards), `-2` returns the second last element, and so on.

Slicing works even more strangely in Python. Whilst in R, using index `var[3:5]` will return the 3rd, 4th and 5th elements, in Python this will only return the 4th and 5th elements. This is because the syntax in Python is `[inclusive:exclusive]` and because of 0-based indexing. Both of these are super confusing, and stem from decisions made by Guido (the Python creator) in the misguided pursuit of "elegance". These decisions might make some Python code more elegant, but for data science this is a serious pain, and hinders readability. 

One nice shortcut in Python (not present in R) is the `[:n]` and `[n:]` syntax. In the first case, the blank argument to the infix operator `:` is interpreted as a 0, and in the second case the blank argument is interpreted as the length of the vector (so that it will select the rest of the vector). This does little to restore the elegance Guido longs for, but it is a nifty shortcut. (The "elegance" comes from these shortcuts, apparently... If you select [:6] then you are selecting the first 6 elements, and if you select [6:] then you are skipping the first 6 elements... I'm not sure I agree this is elegant!)

Python lists override the `+` operator; if you want to concatenate two lists, then you can do so using `+`. Deleting elements is a bit different - you need to use `del(var[3])` to remove an element from the list.

### Copy / Modify

R has a nice "copy on modify" behaviour, which means that when you assign a list (or anything else) to a new variable, it doesn't copy it until you make a change, at which point it saves a modified copy of that object. In Python however, the behaviour is different for different data types (booooooo). Lists, for example, are copied by reference, which means that changing an element in a "copied" list also changes the same element in the original list. To get around this you need to do something like `y = list(x)` or `y = x[:]` to explicitly copy all items from the list.

### Grouping

Python does not use braces - it uses indentation to group blocks of code. This is supposed to improve readability, but in practice it can be super messy.

## Scripting

### Boilerplate

```
#!/usr/bin/env python

# import modules used here -- sys is a very standard one
import sys

# Gather our code in a main() function
def main():
    print 'Hello there', sys.argv[1]
    # Command line args are in sys.argv[1], sys.argv[2] ...
    # sys.argv[0] is the script name itself and can be ignored

# Standard boilerplate to call the main() function to begin
# the program.
if __name__ == '__main__':
    main()
```


