# steam

import json
import xmltodict
import requests


def save_to_file(data, file_name):
    with open(file_name, 'w') as write_file:
        json.dump(data, write_file, indent=4)
        print("The file {0} was successfully created.".format(file_name))


def read_from_file(file_name):
    with open(file_name, 'r') as read_file:
        file = json.load(read_file)
        print("You successfully read from {0}.".format(file_name))
        return file


api_key = read_from_file("steam_key.json")
my_steam_api_key = api_key["steam_api_key"]

print(type(my_steam_api_key))

url = "http://api.steampowered.com/ISteamNews/GetNewsForApp/v0002/?appid=440&count=3&maxlength=300&format=json"
url_steam = url

steam_json = requests.get(url_steam).json()

save_to_file(steam_json, "steam.json")

steam_json_file_name = "steam.json"

