# Chapter-12 


A1. webbrowser : It is used to open a browser with specified url 
                 within the function webbrowser.open() as an argument.  

    requests : requests.get() is used to dowload the files and 
               webpages from the internet.

    bs4 : Used to parse the HTML 

    selenium : Launches and controls a web browser. The selenium  
               module is able to fill in forms and simulate mouse clicks in this browser.

A2. Returns a Response object 
    str(requets.get('url'))

A3. res.raise_for_status()

A4. res.status_code == requets.codes.ok

A5. FileObj = open('myfliename.txt','wb')
    for chunk in res.iter_content(100000) : 
         FileObj.write(chunk)
    FileObj.close()

A6. Firefox => Ctrl+Shift+C

A7. Right click on the specific element and => Click Inspect 
    Element 

A8. #main

A9. .highlight

A10. div div

A11. input[type="favourite"]

A12. spam.getText()

A13. linkElem.attrs

A14. from selenium import webdriver

A15. find_element returns a single WebElement object and searches  
     untill a single match is obtained
     
     find_elements returns a list of WebElement objects for every matching element on the page

A16. WebElementObj.click()
     WebElementObj.send_keys()

A17. WebElemObj. submit()

A18. browser.forward()
     browser.back()
     browser.refresh()


Command Line Emailer :  

 from selenium import webdriver
 import sys
 browser = webdriver.Firefox()
 while len(sys.argv) < 2 : 
    print('Syntax : Program_name email_id message')
 recp_mailid = sys.argv[1]
 msg = sys.argv[2: ] 

 browser.get('https://mail.google.com/mail/u/0/#inbox?compose=new')   
 recp_mailidElem = browser.find_element_by_css_selector('#\:lw')
 recp_mailidElem.send_keys(recp_mailid)
 msgElem = browser.find_element_by_css_selector('#\:mk') 
 msgElem.send_keys(msg)
 sendbtn = browser.find_element_by_css_selector('#\:l4')
 sendbtn.click()

Image Site Downloader : 

 import requests, os, bs4

 url = 'https://unsplash.com/photos/5Lw1U5BIumE'               # starting url
 os.makedirs('nature_imgs', exist_ok=True)    # store imgs in ./nature_imgs
 i = 0
 while i < 25:
    # Download the page.
    print('Downloading page %s...' % url)
    res = requests.get(url)
    res.raise_for_status()

    soup = bs4.BeautifulSoup(res.text, 'html.parser')
    
    Elem = soup.select('div.omfF5 > div > div > img')[0]
                          
    
    if Elem == [] :    
        print('Could not find the image.')
        i +=1 
    else : 
        
        Elem_link = Elem.get('src')
        print('Downloading the image %s....' %(Elem_link))
        res = requests.get(Elem_link)
        res.raise_for_status()


        imageFile = open(os.path.join('nature_imgs',str(i)),'wb')
        for chunk in res.iter_content(100000):
            imageFile.write(chunk)
        imageFile.close()
        i += 1

        Elem_url = soup.select('.SMfhx') 
        print(Elem_url)
        url= Elem.get('href')         

 print('Done.')  

2048 : 

 from selenium import webdriver
 from selenium.webdriver.common.keys import Keys
 browser = webdriver.Firefox()
 browser.get('https://play2048.co/')
 htmlElem = browser.find_element_by_css_selector('body')
 for i in range(20) :
    htmlElem.send_keys(Keys.UP)     # scrolls to bottom
    htmlElem.send_keys(Keys.RIGHT) 
    htmlElem.send_keys(Keys.DOWN) 
    htmlElem.send_keys(Keys.LEFT) 
 print('Done.')   

Link Verification : 

 import requests,bs4
 from requests.sessions import InvalidSchema
 res = requests.get('https://time.com/5733328/best-fiction-books-2019/')
 soup = bs4.BeautifulSoup(res.text,'html.parser')  
 Elem = soup.select('p > a')
 def check(q) :
    try :
        for i in range(q,50) :
            link = Elem[i].get('href') 
            res2 = requests.get(link)
            if res2.status_code == '404' : 
                print(link)
    except IndexError: 
        print('Done.')
    except InvalidSchema :
        k = i+1
        check(k)
 check(0)    



  

