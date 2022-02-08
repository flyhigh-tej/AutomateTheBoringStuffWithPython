# Chapter-10

A1. shutil.copy() is used to copy a single file while shutil.
    copytree() is used to copy an entire folder and its contents.

A2. shutil.move() is used for renaming files

A3. send2trash sends deletes files and sends them to the trash folder 
    which can recovered later whereas the shutil.rmtree() permanently deletes the entire folder and all its contents or files in the path 
    specified.

A4. Creating a zip file object using zipfile.Zipfile('filename.zip')    

Selective Copy :

 from pathlib import Path
 import os, shutil
 def copyPdf(folder) :
    # Searching in all folders
    for foldername, subfolders, filenames in os.walk(folder) : 
        print(f'Searching for files in {foldername}...')
        old_path = os.path.abspath(folder)
        new_path = os.path.join(Path.home(),'Documents')
        # Searching for a match and copying
        for filename in filenames :
            if filename.endswith('.png') or filename.endswith('.pdf') : 
                print(f'Copying {filename} from {old_path} to {new_path}...')
                filename_path = os.path.join(old_path,filename)
                shutil.copy(filename_path, new_path)
            else :
                continue
    print('Done.')
 copyPdf('../../../Pictures')

Deleting Unneeded Files :

 from pathlib import Path
 import os, shutil
 def largeFile(folder) :
    flag = 0
    for foldername, subfolders, filenames in os.walk(folder) : 
        print(f'Searching for files in {foldername}...')
        
        new_path = os.path.join(Path.home(),'Documents')
        for filename in filenames :
            if os.path.getsize(folder) > 104857600 : 
                print(f'{filename} is greater than 100MB...')
                pathObj = os.path.abspath(filename)
                print(pathObj)
                flag = 1
            else :
                continue
    
    if flag == 0 :        
        print('No file greater than 100MB found...')         
    else : 
        print('Done.')
 largeFile('../../../Downloads')

Filling in the Gaps : 

 from pathlib import Path
 import shutil, os, re

 def fileRename(folder) :

    # Create a regex that matches files with the given text format.
    fileNamePatten = re.compile(r"""^(spam) # all text before the digits
       ((\d)?(\d)?\d)             # one or two digits before a digit
       (.txt)$                    # to find text files only
       """, re.VERBOSE)
    a = []
    path_a = []
    ans = []
    i = 0
    k = 0
    
    folder = os.path.join(Path.home(),folder)
    for foldername, subfolders, filenames in os.walk(folder):
         print(f'Searching for files in {foldername}...')
         for filename in filenames:
             fileMatch=fileNamePatten.search(filename)
             if fileMatch != None :
                #print(fileMatch.group(2))
                part1 = fileMatch.group(1)
                part3 = fileMatch.group(5)
                a.append(fileMatch.group(2))
                path_a.append(os.path.realpath(filename))
    #print( a )
    #print(path_a)
    
    for i in range(0,len(a)) :
       if i <= 9 :
           s ='0'+'0'+str(i+1)
           ans.append(s)

       elif i>=10 and i<= 99 :
           s = '0'+str(i+1)
           ans.append(s)

       elif i>=100 and i<=999 :
          s = str(i+1)
          ans.append(s)
    #print(ans)
    
    length_a = len(a)
    while k < length_a : 
        part2 = ans[k]
        final = part1 + part2 + part3
        x = min(a)
        ind = a.index(x)
        filename = part1+x+part3
        filename_path = path_a[ind]
        final1 = Path(filename_path) / '..'/ final
        final_path = os.path.abspath(final1)
        #print(filename_path)
        print(f'Renaming {filename} to {final}...')
        shutil.move(filename_path, final_path)
        del a[ind]
        del path_a[ind]
        k = k+1    
        #print(a)
        #print(ans[1])
        #x = min(a)
        #print(a.index(min(a)))

 fileRename('Documents')

    
   