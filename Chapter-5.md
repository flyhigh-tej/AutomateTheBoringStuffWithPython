# Chapter-5

A1. {}

A2. {'foo': 42}

A3. Dictionary can store values in indexes of datatypes other than integers such as strings, float, 

A4. A KeyError is occured.

A5. There is no difference in output, both of them look for the matching value in 
    keys of the dictionary.

A6. 'cat' in spam looks for the key named 'cat' in the dictionary whereas 'cat' in 
     spam.values() looks for the value named 'cat' in the dictionary.     

A7. spam = {'age': 3} 
    spam.setdefault('color', 'black')

A8. pprint: Module name
    pprint.pprint(): function used

Chess Dictionary Validator :

count_king = 0
def isValidChessBoard(chessboard) :   
    count_pawn = 0
    count_test = 0
    if 'bking' or 'wking' in chessboard.values() :
        global count_king 
        count_king += 1
    if count_king != 2 :
        return False
    if len(list(chessboard))!= 32:
        return False
    if 'bpawn' or 'wpawn' in chessboard.values() :
       count_pawn += 1
    if count_pawn != 16 :
        return False
    for i in chessboard.keys() :
        val = 12345678
        txt = 'abcdefgh' 
        if i[0] not in val :
            return False
        if i[1] not in txt :
            return False
    test = ['pawn', 'knight', 'bishop', 'rook', 'queen', 'king']
    for j in chessboard.values() :
        for k in range(len(test)) :
            if j != 'b'+test[i] or j!= 'w'+test[i] :
                count_test += 1
        if count_test == 12 :
            return False
        count_test = 0
    
    return True  
    
    
TheChessBoard = {'1h': 'bking', '6c': 'wqueen', '2g': 'bbishop', '5h': 'bqueen', '3e': 'wking'} 
 
print(isValidChessBoard(TheChessBoard))

Fantasy Game Inventory :

stuff = {'arrow': 12, 'gold coin': 42, 'rope': 1, 'torch': 6, 'dagger': 1}

def displayInventory(inventory):
    print("Inventory:")
    item_total = 0
    for k, v in inventory.items():
        print(str(v) + ' ' + k)
        item_total += v
    print("Total number of items: " + str(item_total))

displayInventory(stuff)


List to Dictionary Function for Fantasy Game Inventory :

def addToInventory(inventory, addedItems):
    flag = 0 
    for k in range(len(addedItems)): 
        for i in inventory.keys() :
            if addedItems[k] == i :
                flag = 1
                break
        if flag == 0 :
            inventory.setdefault(addedItems[k],0) 
                
    for k in range(len(addedItems)): 
        for i,j in inventory.items() :
           if addedItems[k] == i : 
               j += 1   
           
    return inventory           
def displayInventory(inventory) :
    items_count = 0 
    for k,v in inventory.items() :
        print(str(v) + ' ' + k) 
        items_count += v
    print('Total number of items:' + str(items_count))     

inv = {'gold coin': 42, 'rope': 1}
dragonLoot = ['gold coin', 'dagger', 'gold coin', 'gold coin', 'ruby']
inv = addToInventory(inv, dragonLoot)
displayInventory(inv)
 




