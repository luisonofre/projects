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
                    
design recipe
1. data definitions 
2. fuction prodotypes
 - function signature
 - function description
3. test cases
4. template

                    
```python
# Numlist number -> number
# add the given number to the sum of the numbers in the list
def list_sum_accum(numlist,rest):
    if (numlist == "mt"):
        return sumval
    return list_sum_accum(numlist.rest, numlist.first + sumval)
```                    

how it works
list_sum_accum(Pair(1, Pair(2, "mt")), 0)

return list_sum_accum(Pair(2,"mt"), 1+0)
return list_sum_accum(Pair("mt"), 2+(1+0))                    
return 3      since mt is encounter 

this one is doing the sumation as it goes unlike the other sum that does the sum at the end


steps to append

append(Pain(1, Pair(2, "mt")), Pair(3,"mt"))
#find the end of the list 
#Replace "mt" with Pair(3, "mt")


Trees

```python
# this is a list 
   0
  / \
 2   0
    / \
  27   0
      / \
    22    "mt"
    
# now this this a tree

       Andrew
       /      \
   Lauren       Steven
   /    \       /     \
 Audrey Robert Elaine Michael
 / \      / \       / \    /\
"unk"    "unk"     "unk"  "unk"

# a FamilyTree is one of 
# ="unk"
# -Person(name, mother, father)
class Person:
    def __init__(self, name, mother, father):
        self.name = name    #str
        self.mother = mother #Person
        self.father = father #Person
        
        
#templete
def list_temp(vals):
    if ("mt"):
        ...
    else:
        ...elem.first ... list_temple(elem.rest)
 
def ft_temp(tree):
    if (tree == "unk"):
        ...
    else
        ... tree.name .... ft_temp(tree.mother) ... ft_temp(tree.father)
        
 # function that returns true if an ancestor is named "Thomas"
 def find_tomas(tree):
    if tree == "unk":
        return False
    else
        rerturn tree.name == "thomas or find_thomas(tree.mother) or find_thomas(tree.father)
 
```

lecture 8

```python
# A StrBST is one of
# - None
# - BSTNode(str, Strbst, strBSt) where strings in left are < value, string in right are not
class SBTNode
    def __init__(value, left, right):
    self.value = value 
    self.left = left
    self.right = right
    
    #StrBST str -> bool
    #return true if the given string is in the tree
    def search(tree, sought):
        pass
```

write test cases
- test for a false return
- test for a true return
- test for a treee that is none

then write the template

def tree_temp(tree, arg):
    if(tree is None):
        pass
    else
        tree.value .... tree_temp(tree.left) ...tree_temp(tree.right)
 
 ```python
    #StrBST str -> bool
    #return true if the given string is in the tree
    def search(tree, sought):
        if tree is None:
            return False
        else:
            
            #dumb search return (tree.value == sought or self.search(tree.left, sought) or self.search(tree.right, sought))
            
            #smart binary search
            if sought < tree.value:
                return self.search(tree.left, sought)
            elif sought > tree.value:
                return self.search(tree.right, sought)
            else:
                return True

# StrBST str -> StrBst
# insert the given strig into the tree
def insert(tree, newstr):
    if(tree is None):
        return BSTNode(newstr, None, None)
    else:
        if newstr < tree.value:
            return BSTNode(tree.value, insert(tree.left, Newstr), tree.right)
        else:
            return BSTNode(tree.value, tree.left, insert(tree.right,Newstr)
```

----------------------------------------------------------------------------------
Lecture 11
- soring algorithems we will assume that all elem size is small enough that all elements can fit into RAM
- most run in (n(logn))

Selection sort 
[1 17 0 5 6 8 9]
[0 1 17 5 6 8 9]
[0 1 5 17 6 8 9]
[0 1 5 6 17 8 9]
[0 1 5 6 8 17 9]
[0 1 5 6 8 9 17]
