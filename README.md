# Creating a To-Do List class to manage tasks
class ToDoList:
    def __init__(self):
        self.tasks = []

    # Adding a new task
    def add_task(self, task_description):
        task = {"description": task_description, "completed": False}
        self.tasks.append(task)
        print(f"Task '{task_description}' added successfully!")

    # Viewing all tasks
    def view_tasks(self):
        if not self.tasks:
            print("No tasks in the list!")
            return
        for index, task in enumerate(self.tasks, 1):
            status = "Completed" if task["completed"] else "Pending"
            print(f"{index}. {task['description']} - {status}")

    # Updating task status
    def update_task(self, task_index, completed=True):
        if 1 <= task_index <= len(self.tasks):
            self.tasks[task_index - 1]["completed"] = completed
            status = "completed" if completed else "pending"
            print(f"Task {task_index} marked as {status}!")
        else:
            print("Invalid task number!")

    # Deleting a task
    def delete_task(self, task_index):
        if 1 <= task_index <= len(self.tasks):
            task = self.tasks.pop(task_index - 1)
            print(f"Task '{task['description']}' deleted successfully!")
        else:
            print("Invalid task number!")

# Main function to run the application
def main():
    todo_list = ToDoList()
    while True:
        print("\nTo-Do List Application")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Mark Task as Completed")
        print("4. Delete Task")
        print("5. Exit")
        choice = input("Enter your choice (1-5): ")

        if choice == "1":
            task_description = input("Enter task description: ")
            todo_list.add_task(task_description)
        elif choice == "2":
            todo_list.view_tasks()
        elif choice == "3":
            todo_list.view_tasks()
            try:
                task_index = int(input("Enter task number to mark as completed: "))
                todo_list.update_task(task_index)
            except ValueError:
                print("Please enter a valid number!")
        elif choice == "4":
            todo_list.view_tasks()
            try:
                task_index = int(input("Enter task number to delete: "))
                todo_list.delete_task(task_index)
            except ValueError:
                print("Please enter a valid number!")
        elif choice == "5":
            print("Exiting application. Goodbye!")
            break
        else:
            print("Invalid choice! Please try again.")

if __name__ == "__main__":
    main()
