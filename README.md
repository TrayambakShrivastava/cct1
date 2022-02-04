# cct1
import requests
import csv
resp=requests.get('http://api.football-data.org/v2/competitions/',headers={'X-Auth-Token':'25430cfa5b62420d9ddfac468c97e9ff'})
Tier = input('Enter the tier: ')
data = resp.json()
to_be_appended = []
csvheader = ['ID','Name','Area/Country','Available Seasons','Tier']
for a in range(156):
    if data['competitions'][a]['plan'] == Tier:
        id = f"{data['competitions'][a]['id'],data['competitions'][a]['name'],data['competitions'][a]['numberOfAvailableSeasons'],data['competitions'][a]['plan']}"
        to_be_appended.append(id)
        a += 1


        with open('football3.csv','w',encoding='UTF8',newline='') as f:
              writer = csv.writer(f)

              writer.writerow(csvheader)
              writer.writerows(to_be_appended)
