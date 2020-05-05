#Notes 4/16/20

big O 
O(1) runs at constant time
O(n) run time changes with input
O(log(N)) one of the faster

Scary algorithms
O(N^2)
O(exp(N))
O(N!)

```python
#a Numlist is one of 
#-"mt", or
#-Pair(first, rest)
class Pair:
    def __init__(self, first, rest):
        self.first = first # a number
        self.rest = rest # a Numlist
        #BOILERPLATE OMITTED

# a StrList is one of
# - "mt", or
# - SPair(first, rest)
class SPair:
    def __init__(self, first, rest):
        self.first = first # a string
        self.rest = rest #a strlist (or an SPair)

# strlist -> bool
# Tells the user whether "dark" is a member of a strlist
def contains_dark(strlist):
    if(strlist == "mt"):
        return false
    else:
        #if(strlist.first == "dark"):
        #   return true
        #else:
        #   return contains_dark(strlist.rest)
        return ((strlist.first == "dark") or (contains_dark(strlist.rest)))

# NumList -> number
# SUm the numbers in the list
def list_sum(numList):
    if numList == "mt":
        return 0 
    else:
        return numList.first + list_sum(numList.rest)
```

example of how it runs 
list_sum(Pair(1, Pair(2,"mt")))

return 1 + list_sum(Pair(2, "mt"))
         return 2 + list_sum("mt")
                    return 0 
                    
                    
