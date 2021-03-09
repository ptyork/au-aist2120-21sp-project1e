# Project 1e: Average Grade Calculator

You have been asked to write a script that pulls in student grades from multiple assignments and provides an average for each student. Each file will contain the student ID and a grade representing a single assignment. The output should simply show a single report of each student and their average grade.

The script, `gradebook.py`, should: 

0. Create an empty dictionary, which WILL hold a student id as key and an (initially empty) list of ints as grades (again, it's just EMPTY {} to start with)
1. Ask the user for a file name (if the user presses enter, break to step 6)
2. Open the requested file 
3. Iterate over each line in the file (each line will contain a student id and a grade) 
4. For each line:
    - split the line to get separate values for the id and the grade
    - if the grade appears to be a NUMBER, then just convert it to an int
    - if the grade appearst to be a LETTER, then change it to an int as follows:
        - A becomes 100
        - B becomes 85
        - C becomes 75
        - D becomes 65
        - F becomes 50
    - check to see if the dictionary contains the student id
    - if the id IS NOT there, use the student id as key and store a NEW LIST in the dictionary with the grade (int) as its only value (this will usually happen only for the first file)
    - if the id IS there, append the grade (int) to the existing list of grades for that student (this will usually happen after the first file is processed)
5. Repeat from step 1
6. When done, iterate over each of the keys in your dictionary
7. For each key, retrieve the list of grades, average them, and then print out a line of the final report

Each line in any grades input file will be in the format `student_id,grade`.

When outputing the final report (i.e., line 7), you should print the id left-aligned within 27 spaces followed by the average right-aligned within 8 spaces with 1 decimal point. Total for each line should be 35 characters. Here's an example run with partial results: 
```
Enter file (blank to stop): grades-1.txt
Enter file (blank to stop): grades-2.txt
Enter file (blank to stop): grades-3.txt
Enter file (blank to stop):

alan.alda                      76.7
benny.barker                   82.7
chloe.carter                  100.0
...
```

## REQUIRED IMPLEMENTATION NOTES 

1.  More hints on step 4: you will want to "ask" the grades dictionary if the student id is `in` the dictionary. If so, you want to `append()` the grade and if not, you want to create a new list with that grade as the first item. Remember that if your student id is stored in a variable called `student_id` and the list is in the dictionary, it can be accessed using standard dictionary syntax like `grades[student_id]`. So assuming you have a new grade to add, you can append to the list of grades directly like this: `grades[student_id].append(newgrade)`. And remember that it is easy to create a list with a single value like this: `[123]`. SOOOOO initializing the value with its first grade is likewise straightforward: `grades[student_id] = [newgrade]`

    In the end, you will have a dictionary of grades that will look similar to this if printed:

    ```
    {
        'alan.alda': [75, 82, 73, 65],
        'benny.barker': [85, 75, 88, 85],
        'chloe.carter': [100, 100, 100, 100],
        ...
    }
    ```

2.  You MUST modify __all four__ of the grades files to add YOU and provide yourself with a grade for each assignment. __JUST edit and save the files using VS code or another text editor. No Python code required here.__

3.  You MUST use either the format() function or an f-string to format your lines of text. In other words, you __cannot__ use the center(), ljust() and rjust() methods. Those methods are okay, but don't use them here.

4.  Be sure to test this using grades-4.txt to insure that you've properly processed the letter grades.

When done, be sure to test the heck out of this and then submit the __project1 directory__ in Mimir.

## OPTIONAL CHALLENGES 

1.  Create a second version of the script, `gradebook2.py`. Import the os module, and instead of asking for file names, use the `os.listdir()` method to iterate over ALL of the files in the current folder. If the filename begins with "grades" and ends with ".txt", then you should automatically process it. In other words, the script will have no user input and will simply output the averages report. Way easier than it sounds...basically just replace the while loop and user input with a for/in loop.

2.  Improve the logic so that a grades file can contain one __OR MORE__ grades per student per line. For example, you might have a line with `alan.alda,100,77,94`. If so, add all three grades to the list.
