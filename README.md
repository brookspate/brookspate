import requests
import random

digits = ["1", "2", "3", "4", "5", "6", "7", "8", "9", "0"]

def is_code_valid(code):
  request = requests.get("https://kahoot.it/reserve/session/" + code)
  return request

while True:
	code = ""
	for i in range(6):
		code += random.choice(digits)
	result = is_code_valid(code)
	if result.status_code == 200:
		with open("games.txt", "a") as file:
			file.write(code + "\n")
		print(code)
