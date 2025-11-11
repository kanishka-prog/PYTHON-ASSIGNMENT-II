# PYTHON-ASSIGNMENT-II
print('''--------------------------------------------------------
Title      : GradeBook Analyzer
Course     : Programming for Problem Solving using Python
Author     : Kanishka Saini
Date       : 11-11-2025
Roll No.   : 2501410047  
Description: CLI-based GradeBook Analyzer that reads student marks
             from manual input, computes statistics, assigns grades,
             and displays summaries.
--------------------------------------------------------''')

#MENU 
def display_menu():
    print("\n===== GRADEBOOK ANALYZER =====")
    print("1. Enter student data manually")
    print("2. Exit")
    choice = input("Enter your choice (1-2): ")
    return choice

# INPUT STUDENT NAMES 
def input_names():
    names = []
    num_students = int(input("Enter number of students: "))
    for i in range(num_students):
        name = input(f"Enter Student {i+1} Name : ")
        names.append(name)
    return names

#  INPUT MARKS
def input_marks(names):
    marks = []
    for n in names:
        mark = float(input(f"Enter marks of {n}: "))
        marks.append(mark)
    return marks

# AVERAGE 
def calculate_average(marks):
    total = 0
    for m in marks:
        total += m
    return total / len(marks)

#  MEDIAN
def calculate_median(marks):
    sorted_marks = sorted(marks)
    n = len(sorted_marks)
    if n % 2 == 1:
        return sorted_marks[n // 2]
    else:
        return (sorted_marks[n // 2 - 1] + sorted_marks[n // 2]) / 2

#  GRADES 
def calculate_grades(marks):
    grade_list = []
    for m in marks:
        if m >= 90:
            grade_list.append('A+')
        elif m >= 80:
            grade_list.append('A')
        elif m >= 70:
            grade_list.append('B')
        elif m >= 60:
            grade_list.append('C')
        elif m >= 50:
            grade_list.append('D')
        else:
            grade_list.append('F')
    return grade_list

#  TOPPER & LOWEST 
def topper_and_lowest(names, marks):
    highest = max(marks)
    lowest = min(marks)
    toppers = []
    lows = []
    for i in range(len(marks)):
        if marks[i] == highest:
            toppers.append(names[i])
        if marks[i] == lowest:
            lows.append(names[i])
    return toppers, lows

#  MAIN FUNCTION 

def main():
    while True:
        choice = display_menu()
        if choice == '1':
            student_names = input_names()
            student_marks = input_marks(student_names)

            avg = calculate_average(student_marks)
            median = calculate_median(student_marks)
            grades = calculate_grades(student_marks)
            toppers, lows = topper_and_lowest(student_names, student_marks)

            print("\n===== RESULT SUMMARY =====")
            for i in range(len(student_names)):
                print(f"{student_names[i]} - Marks: {student_marks[i]} | Grade: {grades[i]}")

            print(f"\nAverage Marks : {avg}")
            print(f"Median Marks  : {median}")
            print(f"Toppers       : {toppers}")
            print(f"Lowest Scorer : {lows}")

        elif choice == '2':
            print("👋 Exiting program. Goodbye!")
            break
        else:
            print("Invalid choice! Try again.")

main()
