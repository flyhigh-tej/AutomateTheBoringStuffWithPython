# Chapter-7

A1. re.compile()

A2. The raw strings detect '\' as just a character and not as an escape sequence as the 
    one used in normal string and ignores all escape characters

A3. search() method returns matching objects in group or groups

A4. using the function group()

A5. group(0) / group() : '\d\d\d-\d\d\d-\d\d\d\d'

    group(1) : '\d\d\d'

    group(2) : '\d\d\d-\d\d\d\d' 

A6. using '\' before the respective characters to consider the character as a part 
    of the text

A7. findall() returns a list of tuples when the short-hand characters are mentioned 
    in groups, enclosed within braces whereas a list of strings are returned when the short-hand characters are represented without enclosing them in braces.

A8. It is the bitwise or operator used to combine multiple functions within a 
    single compile() function while checking for a matching object.

A9. The ? has two functions in a regular expression :
    1. To make the compiler in a non-greedy fashion when the re.compile() is     
       used
    2. To find a Matching object which preceds the '?' either Zero or one 
       times

A10. '*' matches with zero or more of the preceding group  
     '+' matches with one or more of the preceding group

A11. {3} looks for a match consisting of the preceding characters/ character 
     occuring three times repeated as one word.
     {3,5} looks for a match consisting of preceding characters/ character occuring either three, four or five times repeated as one word.

A12.  \d : a single digit, numeric chracter  from 0 -9 
      \w : a single digit, letter or underscore character
      \s : a space, tab or a new line character

A13.  \D : any character other than a single digit, numeric chracter ranging from 
           0-9
      \W : any character other than a single digit, letter or underscore character 
      \S : any character other than a space, tab or a new line character

A14. .* : It will match anything and everthing in a greedy fashion.
     .*? : It will match anything and everything in a non-greedy fashion 
          meaning it will match only upto the first occurence.

A15. [a-z0-9]   

A16. by using re.I as a second argument for the re.compile() function.

A17.  The '.' charcter matches every character except a newline character.
      The usgae  of re.DOTALL as the second argument for the re.compile will make the function match with every charcter including the newline chracter.

A18. 'X drummers, X pipers, five rings, X hens'

A19. The re.verbose() ignores the white sapces and comments from their starting '#' 
     to the end of the line while matching cases making the text to be searched for a 
     match more readable.

A20.  w=re.compile(r'\,\d{3}')
      w.findall('6,368,745')  

A21. w = re.compile(r'[A-Z]\w+ Watanabe')
     w.findall('Alice Watanabe') 

A22. w = re.compile(r'(Alice|Bob|Carol)\s(eats|pets|throws)\s(apples|cats|baseballs)\.
     ', re.I)
     w.search('Alice eats apples.').group()          

Date Detection :
 
 import re
 w = re.compile(r'(\d\d)\/(\d\d)\/(\d\d\d\d)')
 q = w.findall('31/04/2021')
 q = list(q[0])
 day,month,year = int(q[0]),int(q[1]),int(q[2])

 # Detect whether its a valid date
 count = 0
 flag = 0
 if month == 04 or month== 06 or month == 09 or month == 11 :
    if date > 30 :
        count += 1
 elif month == 02 :  
    if date > 29 :
        count += 1 
    elif date == 29 :  
        if year % 400 != 0 : 
            if year % 100 != 0 : 
                if year % 4 == 0 : 
                    flag = 1
        if flag == 0 :        
            count += 1
 else : 
    if date > 31 :        
        count += 1
        
 if count == 0 : 
    print('Valid date')
 else :
    print('Invalid date') 

Strong Password Detection  :  

 import re
 a = []
 length_c, upper_c, lower_c, digit_c = 0, 0, 0, 0
 numRegex = re.compile(r'[a-zA-Z0-9]')
 a=numRegex.findall('Findmeifyoucan8')
 if len(a) >= 8 :
    length_c = 1
 for i in range(len(a)) : 
    if a[i].isupper() :
       upper_c = 1
    if a[i].islower() :
       lower_c = 1 
    if a[i].isdigit() : 
       digit_c = 1
 if length_c == 1 and upper_c == 1 and lower_c == 1 and digit_c == 1 :   
  print('Strong')
 elif length_c == 0 and upper_c == 0 and lower_c == 0 and digit_c == 0 :  
  print('Weak')
 else : 
  print('Medium')

Regex Version of the strip() Method : 

import re
def reg_strip(word,match) :
    flag = 0 
    w1 = re.compile(r'^\s.*\s$')   # works as strip() function for words with blank space
    q = w1.findall(word)
    if q != [] :
        ans = q[0][1:len(q[0]) - 1]
    elif q == [] and match !='' : # works as strip() function for specified characters enclosed within() 
        count1 = 0
        count2 = 0
        for i in range(len(word)) :
            if word[i] in match : 
                count1 += 1
            if word[i]not in match :
                point1 = i
                break
        for j in range(len(word)-1 , -1 , -1) :   
            if word[j] in match : 
                count2 += 1
            if word[j]not in match :
                point2 = j
                break
        ans = word[point1 : point2 + 1]
    else :
        print('Second argument not found')
        flag = 1        
    if flag == 0 : 
        return ans    
final_ans = reg_strip('river','')
#final_ans = reg_strip('aSmpkeeSump','Samp')
if final_ans != None :
    print(final_ans)
    #print(reg_strip('aSmpkeeSump','Samp'))







                                     