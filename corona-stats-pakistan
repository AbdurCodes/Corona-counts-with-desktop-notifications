# pip install plyer (for notifications in windows)

from plyer import notification
import requests
from bs4 import BeautifulSoup

def gethtml(url):
    r=requests.get(url)
    return r.text

def notifyMe(title, message):
    notification.notify(
        title = title,
        message = message,
        app_name = "Realtime Corona Stats",
        app_icon = "icon.ico", #img must be .ico format
        timeout = 10,
        ticker = "I am coming",
        toast = False
        )
    
# notifyMe("Corona News", "Corona has almost subsided in the world.")

website = "http://covid.pastic.gov.pk/"

x = gethtml(website)
# print(x.pre)
soup = BeautifulSoup(x, "html.parser")
# print(soup.title)
# print(soup.title.text)
# print(soup.get_text())

divtag = soup.find("div", {"class":"C_left_box"})
spanList = divtag.find_all("span")
title = ""
for span in spanList[:3]:
    title += span.text
    title += " "
print(title + ": " + f"{spanList[3].text}") #CORONAVIRUS PAKISTAN CONFIRMED CASES

params = ""
spantagParams = soup.find_all("span", {"class":"C_right_number"})
for spantagParam in spantagParams:
    params += spantagParam.text
    params += " "

values = ""
spantagValues = soup.find_all("span", {"class":"B_right_text"})
for spantagValue in spantagValues:
    values += spantagValue.text
    values += " "
    
# print(params)
# print(values)

mywishlist = ["Islamabad", "KP"]

paramsList = params.split(" ")
valuesList = values.split(" ")
zipped = zip(paramsList, valuesList)
spans = tuple(zipped)
for item in spans[0:9]:
    if item[0] in mywishlist:
        # print(item[0] + " : " + item[1])
        notifyMe("Pakistan Corona Stats", item[0] + " : " + item[1])
