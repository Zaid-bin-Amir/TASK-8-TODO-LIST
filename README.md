# TASK-8-TODO-LIST
tasks = []

def add_task():
    """Add a new task to the list."""
    task = input("Enter the task description: ").strip()
    if task == "":
        print("Task cannot be empty. Nothing was added.\n")
        return
    tasks.append(task)
    print(f'Task added: "{task}"\n')


def view_tasks():
    """Display all current tasks with their position numbers."""
    if not tasks:
        print("Your to-do list is empty.\n")
        return

    print("\n--- YOUR TASKS ---")
    for index, task in enumerate(tasks, start=1):
        print(f"{index}. {task}")
    print("------------------\n")


def update_task():
    """Update an existing task by its number."""
    if not tasks:
        print("There are no tasks to update.\n")
        return

    view_tasks()
    choice = input("Enter the task number to update: ").strip()

    if not choice.isdigit():
        print("Invalid input. Please enter a valid task number.\n")
        return

    index = int(choice) - 1

    if 0 <= index < len(tasks):
        new_task = input(f'Enter new text for "{tasks[index]}": ').strip()
        if new_task == "":
            print("Task cannot be empty. Update cancelled.\n")
            return
        old_task = tasks[index]
        tasks[index] = new_task
        print(f'Task {choice} updated: "{old_task}" -> "{new_task}"\n')
    else:
        print("Invalid task number.\n")


def remove_task():
    """Remove a task by its number."""
    if not tasks:
        print("There are no tasks to remove.\n")
        return

    view_tasks()
    choice = input("Enter the task number to remove: ").strip()

    if not choice.isdigit():
        print("Invalid input. Please enter a valid task number.\n")
        return

    index = int(choice) - 1

    if 0 <= index < len(tasks):
        removed = tasks.pop(index)
        print(f'Task removed: "{removed}"\n')
    else:
        print("Invalid task number.\n")


def show_menu():
    """Display the main menu options."""
    print("===== TO-DO LIST MENU =====")
    print("1. Add Task")
    print("2. View Tasks")
    print("3. Update Task")
    print("4. Remove Task")
    print("5. Exit")
    print("============================")


def main():
    """Main program loop - handles menu-driven interaction."""
    while True:
        show_menu()
        choice = input("Choose an option (1-5): ").strip()

        if choice == "1":
            add_task()
        elif choice == "2":
            view_tasks()
        elif choice == "3":
            update_task()
        elif choice == "4":
            remove_task()
        elif choice == "5":
            print("Goodbye! Your tasks were not saved after closing.")
            break
        else:
            print("Invalid menu choice. Please enter a number between 1 and 5.\n")
