# Python

## Best Practises

* Create Virtual environment
* `.gitignore`
* `setup.py` - for packaging
* store `requirements.txt` by `pip install -r requirements.txt`
* test files
* `LICENSE` file - if it's not included - you are not sharing your code legally
* `README.md` file

## Terms

Module - a *.py file

## Some important parts

``` 
# Some code examples as memory keys

full_name = "{} {}".format(first_name, last_name)
print(f"Adding {requested_topping}")
someString.title() # capitalize first letter

3 ** 2 = 9

x, y, z = 0, 0, 0

MAX_CONNECTIONS = 5000

# LIST
bicycles = ['trek', 'cannondale', 'redline']
bicycles[-1]           # access last
bicycles.append('ducati')
bicycles.insert(0, 'bmw')
del bicycles[2]
bicycles.sort()        # permanent
bicycles.reverse()
bicycles.remove('cat') # removes all cats

sorted(bicycles) # returns sorted, no change to indexing
len(bicycles)

# in works even as sequence of members
if 'trek' in bicycles:
	print('trek in list')

if bicycles:
	print('list is not empty')

bicycles[0:3] # 0, 1, 2 elements. 3 is index after last member
bicycles[:3]  # same as 0:3
bicycles[2:]  # all indexes from i2
bicycles[-3:] # 3 last members
copyOfBicycles = bicycles[:] # makes full slice

dimensions = (200, 50) # readonly tuple
print(dimensions[0])
print(dimensions[1])

for bicycle in bicycles:
	print(bicycle)

digits = [1, 2, 3, 4, 5, 6]
min(digits)
max(digits)
sum(digits)

list(range(1, 6))

# DICTIONARY
alien = {'color': 'green', 'points': 5}
print(alien['color'])
print(alien.get('points', 'default value if not set')

alien['position'] = (20, 50)
alien['position'] = (30, 50)
del alien['points']

for key, value in someDict.items():
	print(f"Key: {key}, Value: {value}")

for key in sorted(someDict.keys()):
	print(key)

# set removes duplicate items
for value in set(someDict.values()):
	print(value)

# Loops

for value in range(1, 5):
	print(value)

while current_number <= 5:
	print(current_number)
	if current_number % 2 == 0:
		break

squares = [value**2 for value in range(1, 11)]

# USER INPUT
msg = input("Tell me something")
print(msg)

# Functions
def greet_user(username='Anonymous'):
	print(f"Hello, {username.title()}!")

greet_user('jesse')
greet_user(username='jesse')

def returnSth():
	return "Sth"

print(f{ReturnSth()})

def passList(*multiple_args_become_list)
	print(multiple_args_become_list)

passList("one", "two", "etc")

# various
True
False

int("some string int")


if car == 'bmw':
	print('bmw')
elif car == 'audi':
	print('audi')
else:
	print('doubtful car')

# importing
import moduleName
import moduleName as someAlias
from moduleName import fnOrClass, fnOrClass
from moduleName import fnOrClass as someAlias
from moduleName import *

# classes

class Dog:
	def __init__(self, name, age):
		self.name = name
		self.age = age

class SuperDog:
	def __init__(self, name, age, power):
		self.power = power
		super().__init__(name, age)

willie = Dog('Willie', 5)

# override - just same name

# READ FILE

with open('pi_digits.txt') as file_object:
	contents = file_object.read()
print(contents)

with open(filename) as file_object:
	for line in file_object:
		print(line)

with open(filename) as file_object:
	lines = file_object.readlines()
	
# 'w' override all previous data
# 'a' appends to previous data
with open(filename, 'w') as file_object:
	file_object.write("Very important data")

try:
	print(5/0)
except ZeroDivisionError:
	print("U can't divide by zero")
else:
	print("answer")
	
# JSON
import json

numbers = [2, 3, 5]

filename = 'numbers.json'
with open(filename, 'w') as f:
	json.dump(numbers, f)

with open(filename) as f:
	numbers = json.load(f)
```

