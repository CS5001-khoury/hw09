# Homework 09 - Dictionaries 

For this assignment you will explore reading in file data for *large* files, and then adding unique data to a dictionary counting various entries.

## Provided Files
The following files have been provided for you.

* [flight_counter.py](../flight_counter.py) - This is the main file you will be working on. It contains the functions you will be writing, along with already built docstrings. 
* [airlines.dat](../airlines.dat) - This file contains 14 different airlines, in the format of CODE::NAME.
* [flights.dat](../flights.dat) - This is a very large file of flights from 2015. It 1,048,574 different flights! 
* [flights10.dat](../flights10.dat) - This a much smaller file of flights from 2015. It contains 10 different flights. It was built by running the following command in linux/mac: `shuf -n 10 flights.dat > flights10.dat`. The `shuf` command randomly samples lines from a file. 
* [flights100.dat](../flights100.dat) - This is another file you can use for testing counting your flights. 


### flight_counter.py
Take a moment to look through flight counter, and evaluate what the provided code does. In its current state, you can run it from the command line, but it doesn't do much. However, we encourage you to do that, and add the -h program argument to see what it does.



```console
$ python3 flight_counter.py -h
```
(on windows, you can run `python flight_counter.py -h`). 


👉🏽 **TASK** - Run the program with the -h argument, and copy the output into your README.md file. In your own words, explain what it is showing you.  

Further details: `argparse` is a python library that allows you to easily create command line interfaces. It is very useful for creating programs that can be run from the command line, and we wanted to provide an example of what it does in this assignment.  You do not have to know in full detail how to use `argparse`, but if you dive more into python development beyond this course it is a valuable tool to know.

## Required Functions

👉🏽 **TASK** - Implement the following functions in flight_counter.py.

You will implement the following functions in flight_counter.py.
* `load_airlines(filename)` - This function will load the airlines.dat file into a dictionary. The key will be the airline code, and the value will be the airline name.
* `build_counters(filename, airlines)` - This function will build a dictionary of counters for each airline. The key will be the airline code, and the value will be the number of flights for that airline. 
* `print_flight_info(airlines, counters)` - This function will print out the flight information for each airline. It will print out the the airline name and the number of flights for that airline.

Here is an example of the printed output:

```text
Delta Air Lines Inc.:                1
US Airways Inc.:                     2
Atlantic Southeast Airlines:         1
Southwest Airlines Co.:              2
```

or with the full dataset (but half the airlines)

```text
Alaska Airlines Inc.:           29,614
American Airlines Inc.:         97,549
US Airways Inc.:                73,942
Delta Air Lines Inc.:          147,486
Spirit Air Lines:               19,612
United Air Lines Inc.:          87,606
Hawaiian Airlines Inc.:         14,133
```

Here are some specific constraints:
* When loading the flight information, if the airline code is not in the airlines dictionary, you should skip that flight.
* Flights always start with the two digit airline code. 
* Both `load_airlines` and `build_counters` will be reading in from the provided .dat files, building the required dictionaries as the file is being read (don't try to load an entire file, and then build - because the 1,000,000+ lines would waste a lot of memory doing that).
* The spacing is exact! You will need to use string format to get it.  The Airlines name should be *30* characters wide, and the number of flights should be *7* characters wide, with a space between them. See below for some hints on how to do this.


### test_flight_counter.py
👉🏽 **TASK** - Make sure to write tests in a `test_flight_counter.py` file. 

This can be done by building very specific test files, and then making sure the built dictionaries match with what is expected. For example, an airline file that only has three lines. 

You can make ".dat" files using a text editor/your IDE such as Pycharm or VS Code. They are just text files. 

You can also run from the command line the tests built into the docstrings. For example, you can use the following command line to test all the docstrings in flight_counter.py:

```console
$ python3 -m doctest flight_counter.py
```

If everything runs correctly, you actually get 0 output. If there is an error, it will show you what the error is. If you want to force full details for output, you add the `-v` flag.

```console
$ python3 -m doctest flight_counter.py -v
```

---

Start early, and ask questions!

##  README.md
In your READme.md file, answer the following questions:

1. Which Airlines have the most flights in 2015? How many flights did they have?
2. Which Airlines have the least flights in 2015? How many flights did they have?
3. What part of the assignment challenged you the most?
4. What part did you enjoy the most?
5. Data is an important aspect of our society, and it is important to understand how to work with it. What are some ways you can see data being used in your future career?
6. You should start thinking about larger applications, list some applications /  projects you would like to work on? Narrow it down to projects that you can accomplish within a couple weeks within this class?
7. Provide output of you running `doctest` with the `-v` flag enabled (i.e. the output generated on your screen)
8. Output of running `python3 flight_counter.py -h`, and what it means in your own words.



## 📝 Grading Rubric


1. Learning (AG)
   * load_airlines works correctly with a small airlines file
   * load_airlines works correctly with a larger sized file
2. Approaching  (AG)
   * Build counters works correctly with a small airlines file 
   * Build counters works correct with medium sized files
   * prints out flight info for a small data set, spacing is not counted
3. Meets  (AG)
   * Passes standard pycodestyle check
   * Prints out flight info for a large dataset including commas and spacing correct
   * Prints out flight info for a small data set including proper spacing
4. Exceeds  (MG)
   * Code has comments, well written, and easy to read
   * Student provides a test_flight_counter.py file, along with any test.dat files they made.
   * Student answers questions in the README.md file


AG - Auto-graded  
MG - Manually graded


## 📚 Additional Resources
* [Python Dictionaries](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)
* [Python File Reading](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)
* [Format String Syntax](https://docs.python.org/3/library/string.html#format-string-syntax)
* [argparse](https://docs.python.org/3/library/argparse.html) - Python library for creating command line interfaces
* [Kaggle - Explore: Flights](https://www.kaggle.com/code/miquar/explore-flights-csv-airports-csv-airlines-csv/notebook) - This is a notebook that uses the flights dataset to explore flights. It provided the basis for the .dat files we provided.


### String Formatting for Numbers

If you want to format a number to have commas, you can use the following code:

```python
>>> num = 123456789
>>> print(f'{num:,}')
123,456,789
```

If you want to have a number that is 12 characters wide, and right justified, you can use the following code:

```python

>>> num = 123456789
>>> print(f'|{num:12,}|')
|   123,456,789|
```

### String Padding to the Right

If you want to pad a string to the right, you can use the following code:

```python
>>> name = "Delta Air Lines Inc."
>>> print(f'|{name:30}|')
|Delta Air Lines Inc.         |
```
But what if you wanted to add an extra character? Then make sure to modify `name` *before* using the string formatting.  The bars are added just so you can see the spaces easier. 



### Combining String Formatting and Padding

```python
>>> name = "Delta Air Lines Inc."
>>> num = 123456789
>>> print(f'|{name:30} {num:12,}|')
|Delta Air Lines Inc.         123,456,789|
```
