# Chapter-9

A1. The relative path is relative with respect to the currently working 
    directory.

A2. Absolute path starts with the root folder always.

A3. WindowsPath('C:/Users/Al')

A4. TypeError: unsupported operand type(s) for /: 'str' and 'str', anyone 
    of the paths must be represented as Path() object

A5. os.getcwd() : Prints the currently working directory on the screen.
    os.chdir() : Changes the currently working directory to the 
                 specified directory mentioned along with its path. 

A6. '.' --> represents the currently woring directory.
    '..' --> represents the parent directory(previous directory in path 
             before the cwd) to the currently working directory.          

A7. dir name: C:\bacon\eggs\
    base name: spam.txt

A8. 'r' or read mode
    'w' or write mode
    'a' or append mode

A9. The previously existed data is erased or overwritten with the new data 
    we assign to the respective file if the file is opened in write mode  

A10. read() Reads the entire file as a string while readlines() method  
     splits the entire file at the end of newline character into strings inside the list

A11. shelfvalue resembles a dictionary data structure with keys() and 
     values().

Extending the Multi-Clipboard :

   #! python3
   # mcb.pyw - Saves and loads pieces of text to the clipboard.
   # Usage: python3 mcb.pyw save <keyword> - Saves clipboard to keyword.
   #        python3 mcb.pyw <keyword> - Loads keyword to clipboard.
   #        python3 mcb.pyw list - Loads all keywords to clipboard.
   
 import shelve, pyperclip, sys  
 mcbShelf = shelve.open('mcb')

 # Save clipboard content.
 if len(sys.argv) == 3 : 
    if sys.argv[1].lower() == 'save':
          mcbShelf[sys.argv[2]] = pyperclip.paste()
    elif sys.argv[1].lower() == 'delete' :
        del mcbShelf[sys.argv[2]]
    else :
        print('File named:'+sys.argv[2]+'does not exist')    

 elif len(sys.argv) == 2:
    # List keywords and load content.
    if sys.argv[1].lower() == 'list':
      pyperclip.copy(str(list(mcbShelf.keys())))
    elif sys.argv[1] in mcbShelf:
      pyperclip.copy(mcbShelf[sys.argv[1]])
    elif sys.argv[1].lower == 'delete' :
        for i in range(len(list(mcbShelf.keys()))) :
          del mcbShelf[i]
    else :
        print('Command '+sys.argv[1]+' not found') 
    
 mcbShelf.close()

Mad Libs : 

 from pathlib import Path
 import pprint
 madlibFile = open(Path('/home/flyhigh-tej/Documents/hello.txt'))
 anslibFile = open(Path('/home/flyhigh-tej/Documents/madlib_ans.txt'),'w')
 stmnts = madlibFile .readlines()
 print(stmnts)
 letters = ''
 ans_stmnt = ''
 ans = []

 for i in range(len(stmnts)) :
   for j in range(len(stmnts[i])) :
     if stmnts[i][j] != ' ' and stmnts[i][j] != '\n'  :
       letters += stmnts[i][j]
     elif stmnts[i][j] == ' ':
       if letters.upper() == 'ADJECTIVE' or letters.upper() == 'ADJECTIVE.' :
          print("Enter an adjective:")
          adj = input()
          if letters.upper() == 'ADJECTIVE.' :
              letters = adj+'.'
          else :
              letters = adj

       elif letters.upper() == 'NOUN' or letters.upper() == 'NOUN.' :
          print("Enter a noun:")
          noun = input()
          if letters.upper() == 'NOUN.' :
              letters = noun+'.'
          else :
              letters = noun

       elif letters.upper() == 'VERB' or letters.upper() == 'VERB.' :
          print("Enter a verb:")
          verb = input()
          if letters.upper() == 'VERB.' :
              letters = verb+'.'
          else :
              letters = verb

       elif letters.upper() == 'ADVERB' or letters.upper() == 'ADVERB.' :
          print("Enter an adverb:")
          adv = input()
          if letters.upper() == 'ADVERB.' :
              letters = adv+'.'
          else :
              letters = adv

      word = letters + ' '
      letters = ''
      ans_stmnt += word

     elif stmnts[i][j] == '\n':
       word = letters + '\n'
       letters = ''
       ans_stmnt += word

   ans.append(ans_stmnt)
   ans_stmnt = ''
 for i in range(len(ans)) :
    anslibFile.write(f'{ans[i]}')

 anslibFile.close()
 madlibFile.close()

Regex Search :

 from pathlib import Path 
 import re
 #import pyinputplus as pyip
 a = []
 q = 0
 p = Path.home()/'Documents'
 for PathobjFile in p.glob('*.txt') : 
  a.append(PathobjFile.stem)
 Regex = re.compile(r'^\w+$')
 print('Enter the file name to be searched: ')
 searchitem = input()
 try :
  #resp = pyip.inputStr(prompt= 'Enter the file name to be searched: ',default = 'File not found')
  ans = Regex.search(searchitem).group()
  for i in range(len(a)) : 
      if ans == a[i] :
        print('File Found') 
        break
      else :
        q += 1   
  if q == len(a) :
    print('File not found')
    ans = str(a)[1:-1]
    print('.txt files present in the directory are only : '+ans)

 except AttributeError:
  print('File not found')
  ans = str(a)[1:-1]
  print('.txt files present in the directory are only : '+ans)




 # Alternative method with Input Validation
 '''resp = pyip.inputStr(prompt= 'Enter the file name to be searched: ',default = 'File not found')  
 for i in range(len(a)) : 
  if resp == a[i] :
    print('File Found') 
    break
  else :
    q += 1   
 if q == len(a) :
  print('File not found')
  ans = str(a)[1:-1]
  print('.txt files present in the directory are only : '+ans)'''



                                                                                                                 
