# Chapter-6

A1. Escape characters are used along with characters that serve 
    a specific purpose. It is used to view the specific purpose characters like '', " ",etc.,

A2. \n used used to iniate the control flow to the next 
     corresponding line.
    \t is used to print a tab space 

A3. By using '\\' (two backslash consecutively).

A4. "Howl's Moving Castle" --> print("Howl\'s Moving Castle") 
     because the escape character '\' is used.

A5. Using print() multiple times for every individual line.

A6. -> e
    -> Hell
    -> Hell
    -> lo, world!

A7. -> HELLO
    -> True
    -> hello

A8. -> ['Remember,', 'remember,', 'the', 'fifth', 'of', 
       November.']  

    -> There-can-be-only-one.      

A9. Rt-justify -> .rjust()
    Lt-justify -> .ljust()
    Center     -> .center()

A10. Using .strip() function

Table Printer :

tableData = [['apples', 'oranges', 'cherries', 'banana'],
['Alice', 'Bob', 'Carol', 'David'],
['dogs', 'cats', 'moose', 'goose']]

colWidths = [0] * len(tableData)
txt = []
s=''

# Searching for the element having greatest length
for i in range(len(tableData)) :
    for j in range(len(tableData[i])) :
        if len(tableData[i][j]) > int(colWidths[i]) :
            colWidths[i] = len(tableData[i][j])

# Seperating elements row-wise
for i in range(len(tableData[0])) :
    for j in range(len(tableData)) :
        if j != 0 :
            s +=' ' + tableData[j][i]
        else :
            s += tableData[j][i]
    txt.append(s)
    s=''

# Splitting a row of elements into lists inside lists
txt2 = []
for i in range(len(txt)) :
    txt2.append(txt[i].split())
print(txt2)

# Fixing spaces for every charcter wrt the greatest element of the coloumn
for i in range(len(txt2)) :
   for j in range(len(txt2[i])) :
      if j==0 :
          print(txt2[i][j].rjust(colWidths[j]),end=' ')
      elif j==1 :
          print(txt2[i][j].rjust(colWidths[j]),end=' ')
      elif j==2 :
          print(txt2[i][j].rjust(colWidths[j]),end=' ')

   print()

Zombie Dice Bots : 

import zombiedice
class MyZombie:
def __init__(self, name):
   self.name = name
def turn(self, gameState):


diceRollResults = zombiedice.roll() # first roll


brains = 0
while diceRollResults is not None:
  brains += diceRollResults['brains']
  if brains < 2:
    diceRollResults = zombiedice.roll() # roll again
else:
    break
zombies = (
zombiedice.examples.RandomCoinFlipZombie(name='Random'),
zombiedice.examples.RollsUntilInTheLeadZombie(name='Until Leading'),
zombiedice.examples.MinNumShotgunsThenStopsZombie(name='Stop at 2
Shotguns', minShotguns=2),
zombiedice.examples.MinNumShotgunsThenStopsZombie(name='Stop at 1
Shotgun', minShotguns=1),
MyZombie(name='My Zombie Bot'),
)

zombiedice.runTournament(zombies=zombies, numGames=1000)
zombiedice.runWebGui(zombies=zombies, numGames=1000)


  