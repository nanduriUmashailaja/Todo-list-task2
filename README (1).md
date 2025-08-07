# Todo-list-task2
#Create a To-Do List Application
def show_menu():
    print("\nTo-Do List Menu")
    print("1. View Tasks")
    print("2. Add Task")
    print("3. Remove Task")
    print("4. Exit")

def load_tasks():
    try:
        with open("tasks.txt", "r") as f:
            return [line.strip() for line in f]
    except:
        return []

def save_tasks(tasks):
    with open("tasks.txt", "w") as f:
        for task in tasks:
            f.write(task + "\n")

tasks = load_tasks()

while True:
    show_menu()
    choice = input("Choose: ")

    if choice == "1":
        if not tasks:
            print("No tasks.")
        else:
            for i, task in enumerate(tasks, 1):
                print(f"{i}. {task}")

    elif choice == "2":
        new_task = input("Enter new task: ")
        tasks.append(new_task)
        save_tasks(tasks)
        print("Task added.")

    elif choice == "3":
        for i, task in enumerate(tasks, 1):
            print(f"{i}. {task}")
        try:
            num = int(input("Enter task number to remove: "))
            tasks.pop(num - 1)
            save_tasks(tasks)
            print("Task removed.")
        except:
            print("Invalid number.")

    elif choice == "4":
        print("Goodbye!")
        break

    else:
        print("Invalid choice. Try again.")
