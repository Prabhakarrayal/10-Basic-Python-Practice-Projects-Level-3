# 🚀 10 Advanced Python Programs (Level 3)
This collection moves into professional programming concepts, including Object-Oriented Programming (OOP), interacting with web APIs, and using advanced Python features to write cleaner, more efficient code. These examples showcase the ability to build structured, real-world applications.

## 1. Basic Object-Oriented Programming (OOP): A Dog Class
OOP allows us to model real-world things. A class is a blueprint for creating objects. This is a cornerstone of modern software development.
```python
# A class is a blueprint. We define the properties and behaviors of a 'Dog'.
class Dog:
    # The __init__ method is the constructor. It runs when a new Dog object is created.
    # `self` refers to the specific instance of the object being created.
    def __init__(self, name, age):
        self.name = name  # Attribute for the dog's name
        self.age = age    # Attribute for the dog's age
        print(f"A new dog named {self.name} has been created!")

    # This is a 'method' (a function that belongs to a class).
    def bark(self):
        return "Woof! Woof!"

    # Another method that uses the object's attributes.
    def get_details(self):
        return f"Name: {self.name}, Age: {self.age}"

# Create two 'instances' of the Dog class.
my_dog = Dog("Buddy", 4)
another_dog = Dog("Lucy", 2)

# Call methods on our new dog objects.
print(my_dog.get_details())
print(f"{another_dog.name} says: {another_dog.bark()}")
```

## 2. Working with a Public API: Fetching Jokes
APIs (Application Programming Interfaces) let our programs talk to other programs over the internet. This is how you get data for weather apps, stock tickers, and more.
```python
# 'requests' is a popular library for making HTTP requests in Python.
# You might need to install it first: pip install requests
import requests
import json # json is a standard library for working with JSON data.

try:
    # The URL of the API endpoint we want to get data from.
    api_url = "[https://official-joke-api.appspot.com/random_joke](https://official-joke-api.appspot.com/random_joke)"

    # Make a GET request to the API.
    response = requests.get(api_url)

    # Raise an error if the request was unsuccessful (e.g., 404 Not Found).
    response.raise_for_status()

    # The API returns data in JSON format. We parse it into a Python dictionary.
    joke_data = response.json()

    # Extract the setup and punchline from the dictionary.
    setup = joke_data['setup']
    punchline = joke_data['punchline']

    print("Here's a random joke for you:")
    print(f"Q: {setup}")
    print(f"A: {punchline}")

except requests.exceptions.RequestException as e:
    print(f"Error fetching data from the API: {e}")
```
## 3. List Comprehensions: The Pythonic Way
List comprehensions provide a concise, elegant, and efficient way to create lists. Using them is a sign of a fluent Python programmer.
```python
# -- The traditional way with a for loop --
squares = []
for i in range(1, 11):
    squares.append(i * i)
print(f"Traditional way: {squares}")


# -- The Pythonic way with a list comprehension --
# The syntax is: [expression for item in iterable]
squares_comp = [i * i for i in range(1, 11)]
print(f"List comprehension: {squares_comp}")


# -- List comprehension with a condition --
# The syntax is: [expression for item in iterable if condition]
even_numbers = [num for num in range(1, 21) if num % 2 == 0]
print(f"Even numbers from 1-20: {even_numbers}")
```
4. Working with JSON Files
JSON (JavaScript Object Notation) is the standard format for data exchange on the web. This script shows how to read from and write to a .json file.
```python
import json

# A Python dictionary that we want to save.
user_data = {
    "username": "coder123",
    "email": "coder@example.com",
    "level": 3,
    "projects": ["Project A", "Project B"]
}

# --- Writing to a JSON file ---
# 'w' for write mode.
with open('user_data.json', 'w') as json_file:
    # `json.dump()` writes the Python dictionary to the file in JSON format.
    # `indent=4` makes the file human-readable.
    json.dump(user_data, json_file, indent=4)
print("Successfully wrote data to user_data.json")


# --- Reading from a JSON file ---
# 'r' for read mode.
with open('user_data.json', 'r') as json_file:
    # `json.load()` reads the JSON file and parses it into a Python dictionary.
    loaded_data = json.load(json_file)
print("\nSuccessfully loaded data from file:")
print(loaded_data)
print(f"Username: {loaded_data['username']}")
```
5. Simple Web Scraper
Web scraping is the process of extracting data from websites. This example uses the requests library to get the HTML content of a webpage.
```python
import requests

# The URL of the website we want to scrape.
url = '[http://example.com](http://example.com)'

try:
    # Send an HTTP GET request to the URL.
    response = requests.get(url)
    
    # Check if the request was successful (status code 200).
    response.raise_for_status() 

    # The `.text` attribute contains the full HTML content of the page.
    html_content = response.text
    
    print(f"Successfully fetched HTML from {url}")
    print("\n--- First 250 characters of HTML ---")
    print(html_content[:250])
    
except requests.exceptions.RequestException as e:
    print(f"An error occurred: {e}")
```
6. Command-Line Argument Parser
This script shows how to use the argparse module to create a professional command-line tool that accepts arguments, just like git or ls.
```python
import argparse

# Create a parser object.
parser = argparse.ArgumentParser(description="A simple program that greets the user.")

# Add an argument. `name` is positional. `help` provides a description.
parser.add_argument("name", help="The name of the person to greet.")

# Add an optional argument. `--repeat` is a flag. `type=int` ensures it's a number.
parser.add_argument("-r", "--repeat", type=int, default=1, help="Number of times to repeat the greeting.")

# Parse the arguments provided by the user from the command line.
args = parser.parse_args()

# Use the parsed arguments in the program logic.
for _ in range(args.repeat):
    print(f"Hello, {args.name}!")

# To run this from your terminal:
# python your_script_name.py Alice
# python your_script_name.py Bob --repeat 5
```
7. Lambda Functions (Anonymous Functions)
A lambda function is a small, one-line anonymous function defined with the lambda keyword. They are useful for short, simple operations.
```python
# A normal function definition.
def double(x):
    return x * 2
print(f"Normal function: {double(5)}")


# The equivalent lambda function.
# The syntax is: lambda arguments: expression
double_lambda = lambda x: x * 2
print(f"Lambda function: {double_lambda(5)}")


# Lambdas are often used with functions like `map()` and `filter()`.
numbers = [1, 2, 3, 4, 5, 6]
# `map()` applies a function to every item in an iterable.
squared_numbers = list(map(lambda x: x**2, numbers))
print(f"Squared numbers using map and lambda: {squared_numbers}")
```
8. Simple Decorator
A decorator is a function that takes another function as an argument, adds some functionality, and returns the modified function. This is an advanced concept.
```python
# This is our decorator. It takes a function `func` as input.
def my_decorator(func):
    # The wrapper function contains the new functionality.
    def wrapper():
        print("Something is happening before the function is called.")
        func() # Call the original function.
        print("Something is happening after the function is called.")
    return wrapper

# The '@' syntax is how we apply a decorator.
@my_decorator
def say_hello():
    print("Hello!")

# Now, when we call say_hello, the decorator's wrapper function runs.
say_hello()
```
9. Working with CSV Files
CSV (Comma-Separated Values) is a common format for storing tabular data. Python's csv module makes it easy to work with these files.
```python
import csv

# --- Writing to a CSV file ---
# Data to be written (list of lists).
header = ['name', 'department', 'role']
data = [
    ['Alice', 'Engineering', 'Software Engineer'],
    ['Bob', 'Marketing', 'Content Creator'],
    ['Charlie', 'Engineering', 'DevOps Engineer']
]

with open('employees.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerow(header) # Write the header row.
    writer.writerows(data)  # Write all the data rows.
print("employees.csv written successfully.")

# --- Reading from a CSV file ---
print("\nReading from employees.csv:")
with open('employees.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(', '.join(row))
```
10. Recursion: Factorial Revisited
Recursion is a technique where a function calls itself to solve a problem. It's an alternative to loops for repetitive tasks and is a fundamental concept in computer science.
```python
# This function calculates factorial using recursion.
def recursive_factorial(n):
    # The 'base case': The condition that stops the recursion.
    # The factorial of 0 is 1.
    if n == 0:
        return 1
    # The 'recursive step': The function calls itself with a modified argument.
    # It breaks the problem down into smaller pieces.
    else:
        return n * recursive_factorial(n - 1)

num = 5
print(f"The factorial of {num} (using recursion) is {recursive_factorial(num)}")
# How it works for n=4:
# 4 * recursive_factorial(3)
# 4 * (3 * recursive_factorial(2))
# 4 * (3 * (2 * recursive_factorial(1)))
# 4 * (3 * (2 * (1 * recursive_factorial(0))))
# 4 * (3 * (2 * (1 * 1))) = 24
```
# 📚 What You’ll Learn
• Implementing Object-Oriented Programming (OOP) with classes and methods.

• Interacting with web APIs to fetch and parse external data.

• Handling data formats like JSON and CSV for file I/O.

• Using advanced Python features like decorators, lambda functions, and list comprehensions.

• Building professional command-line tools with argument parsing.

• Understanding foundational computer science concepts like recursion.

# 🤝 Contributing
Feel free to fork this repo, add more advanced Python programs, and submit a pull request.

# ⭐ Support
If you found this helpful, please star ⭐ the repository to support more projects like this.
