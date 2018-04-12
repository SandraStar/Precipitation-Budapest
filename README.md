import smtplib
import urllib.request
import re

#server = smtplib.SMTP('smtp.gmail.com', 587)
#server.starttls()
#server.login("", "") #YOUR EMAIL ADDRESS, YOUR PASSWORD
    
url= 'https://www.google.de/search?q=wetter+morgen+budapest&oq=wetter+morgen+budapest&gs_l=psy-ab.3..0.270658.273017.0.273273.7.7.0.0.0.0.133.643.6j1.7.0.dummy_maps_web_fallback...0...1.1.64.psy-ab..1.6.546...0i13k1j0i7i30k1.0.Z4S9VU0EJuk'

headers = {}
headers ['User-Agent'] = 'Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.17 (KHTML, like Gecko) Chrome/24.0.1312.27 Safari/537.17'
req = urllib.request.Request(url, headers=headers)
resp = urllib.request.urlopen(req)
content = resp.read()
stringtext = str(content)

s2 = '<span id="wob_pp">'

post= (stringtext.find(s2))+ 18

post1 = post + 2
post2 = post1 + 1
post3 = post2 + 1
post4 = post3 + 1
post5 = post + 1

Precipitation1 = stringtext[post:post1] #0%

      
Precipitation2 = stringtext[post:post2] #10%
Precipitation3 = stringtext[post:post3] #100%
Precipitation4 = stringtext[post1:post2] #zeigt Position 3, 10%
Precipitation5 = stringtext[post5:post1] #zeigt Position 2, 0%
Precipitation6 = stringtext[post2:post3] #zeigt Position 4, 100%

if Precipitation4 == str('%'):
    #msg = 'The forecasts predicts for tomorrow a ' + Precipitation2 + ' chance of rain.'
    #server.sendmail("", "", msg) #YOUR EMAIL ADDRESS, THE EMAIL ADDRESS TO SEND TO
    #server.quit()
    print(Precipitation2)
       
if Precipitation5 == str('%'):
    #msg = 'The forecasts predicts for tomorrow a ' + Precipitation1 + ' chance of rain.'
    #server.sendmail("", "", msg) #YOUR EMAIL ADDRESS, THE EMAIL ADDRESS TO SEND TO
    #server.quit()
    print(Precipitation1)

if Precipitation6 == str('%'):
    #msg = 'The forecasts predicts for tomorrow a ' + Precipitation3 + ' chance of rain.'
    #server.sendmail("", "", msg) #YOUR EMAIL ADDRESS, THE EMAIL ADDRESS TO SEND TO
    #server.quit()
    print(Precipitation3)
