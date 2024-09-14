# Introduction
# In this project, you will apply your Python programming skills to create a functional To-Do List Application 
# from scratch. The objective of this project is to reinforce your understanding of Python syntax, 
# data types, control structures, functions, and error handling while building a practical and interactive application.

# Project Requirements
# User Interface (UI):
# Create a command-line interface (CLI) for the To-Do List Application.
# Display a welcoming message and a menu with the following options:
#        Welcome to the To-Do List App!

#       Menu:
#       1. Add a task
#       2. View tasks
#       3. Mark a task as complete
#       4. Delete a task
#       5. Quit

def display_menu():
    print("Welcome to the To-Do List App!")
    print("Menu: ")
    print("1. Add a task")
    print("2. View tasks")
    print("3. Mark a task as complete")
    print("4. Delete a task")
    print("5. Quit")

# To-Do List Features:
# Implement the following features for the To-Do List:
# Adding a task with a title (by default “Incomplete”).
# Viewing the list of tasks with their titles and statuses (e.g., "Incomplete" or "Complete").
# Marking a task as complete.
# Deleting a task.
# Quitting the application.

tasks = []  # List to store tasks

def add_task():
    title = input("Enter task title: ")
    task = {"title": title, "status": "Incomplete"}
    tasks.append(task)
    print(f"Task '{title}' added.")

def view_tasks():
    if not tasks:
        print("No tasks available.")
    else:
        for index, task in enumerate(tasks):
            print(f"{index + 1}. {task['title']} - {task['status']}")

def mark_task_complete():
    view_tasks()
    try:
        task_number = int(input("Enter the number of the task to mark as complete: ")) - 1
        if 0 <= task_number < len(tasks):
            tasks[task_number]['status'] = "Complete"
            print(f"Task '{tasks[task_number]['title']}' marked as complete.")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Invalid input. Please enter a number.")

def delete_task():
    view_tasks()
    try:
        task_number = int(input("Enter the number of the task to delete: ")) - 1
        if 0 <= task_number < len(tasks):
            removed_task = tasks.pop(task_number)
            print(f"Task '{removed_task['title']}' deleted.")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Invalid input. Please enter a number.")

# User Interaction:
# Allow users to interact with the application by selecting menu options using input().
# Implement input validation to handle unexpected user input gracefully.

def main():
    while True:
        display_menu()
        choice = input("Enter your choice (1-5): ")
        
        if choice == '1':
            add_task()
        elif choice == '2':
            view_tasks()
        elif choice == '3':
            mark_task_complete()
        elif choice == '4':
            delete_task()
        elif choice == '5':
            print("Quitting the application. Goodbye!")
            break
        else:
            print("Invalid choice. Please select a valid option.")

if __name__ == "__main__":
    main()

# Error Handling:
# Implement error handling using try, except, else, and finally blocks to handle potential issues.

try:
    main()
except Exception as e:
    print(f"An error occurred: {e}")
finally:
    print("Thank you for using the To-Do List App.")

# Code Organization:
# Organize your code into functions to promote modularity and readability.
# Use meaningful function names with appropriate comments and docstrings for clarity.

# Testing and Debugging:
# Thoroughly test your application to identify and fix any bugs.
# Consider edge cases, such as empty task lists or incorrect user input.

# Documentation:
# Include a README file that explains how to run the application and provides a brief overview of its features.
# Optional Features (Bonus):
# If you feel adventurous, you can add extra features like task priorities, due dates, or color-coding tasks based on their status.
