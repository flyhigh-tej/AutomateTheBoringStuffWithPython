# Chapter-4 

A1. [] are used to refer to lists used in python language.

A2. spam[2] = 'hello'

A3. d

A4. d

A5. a b 

A6. 1

A7. [3.14, 'cat', 11, 'cat', True, 99]

A8. [3.14, 11, 'cat', True]

A9. + : List concatenation
    * : List replication

A10. append(): just adds the value given in brackets to the the end of the    
               list.
     insert(): adds the given value in the given index position. It takes 
               two arguments, the first one is the index position and the second one is the value to be added at that index position.

A11. 1. using del keyword Eg. del eggs[3]
     2. using remove() method Eg. spam.remove('bat')

A12. 1. Concatenation operator and replication operators works the 
        same way in both strings and lists.
     2. Slicing can be performed similar to the one that can be done in 
        strings. 

A13. 1. Lists are mutable whereas tuple datatypes are immutable
     2. Lists are enclosed in square brackets [], whereas tuples are enclosed 
        in closed brackets () 
     3. Tuples are efficient in working much faster as compared to lists 
        due an advantage of having immutable nature.

A14. tuple_name = (42)

A15. list(())
     tuple([])   

A16. Variables that contain list values actually contain references to the 
     list values.

A17. copy.copy() is used to copy list values from one variable to another 
     variable.
     copy.deepcopy() is used to copy list values which contain lists 
     as the main list values from one variable to another variable. 

Comma code :

def example(fruits) :
    fruits[-1] = 'and ' + fruits[-1]
    for i in range(len(fruits)) :
        print(fruits[i], sep=',', end=' ')
example(['apples', 'bananas', 'tofu', 'cats'])

Coin Flip Streaks :

import random
numberOfStreaks = 0
for experimentNumber in range(10000):
    # Code that creates a list of 100 'heads' or 'tails' values.
    hort = []
    countH= 0
    countT= 0
    for i in range(100):
        hort.append(random.randint(0,1))    
    # Code that checks if there is a streak of 6 heads or tails in a row.
    for i in range(0,95,1):
        if hort[i] == 0 :
            for j in range(1,6):
                if hort[i+j] == 0 :
                    countH += 1
        if hort[i] == 1 :
            for j in range(1,6):
                if hort[i+j] == 1 :
                    countT += 1 
    if countH != 0 and countH % 6 == 0 :
        numberOfStreaks += countH / 6
    if countT != 0  or countT % 6 == 0 :
        numberOfStreaks += countT / 6         
print('Chance of streak: %s%%' % (numberOfStreaks / 100))

Character Picture Grid :

grid = [['.', '.', '.', '.', '.', '.'],
        ['.', 'O', 'O', '.', '.', '.'],
        ['O', 'O', 'O', 'O', '.', '.'],
        ['O', 'O', 'O', 'O', 'O', '.'],
        ['.', 'O', 'O', 'O', 'O', 'O'],
        ['O', 'O', 'O', 'O', 'O', '.'],
        ['O', 'O', 'O', 'O', '.', '.'],
        ['.', 'O', 'O', '.', '.', '.'],
        ['.', '.', '.', '.', '.', '.']]
for i in range(6) :
    for j in range(9) :
        print(grid[j][i],end='')
    print()    





                          
