class ToDoList:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append({"task": task, "completed": False})

    def view_tasks(self):
        for i, task in enumerate(self.tasks, 1):
            status = "✓" if task["completed"] else "✗"
            print(f"{i}. [{status}] {task['task']}")

    def update_task(self, index, new_task):
        if 0 <= index < len(self.tasks):
            self.tasks[index]["task"] = new_task

    def delete_task(self, index):
        if 0 <= index < len(self.tasks):
            self.tasks.pop(index)

    def mark_completed(self, index):
        if 0 <= index < len(self.tasks):
            self.tasks[index]["completed"] = True

def main():
    todo = ToDoList()
    
    while True:
        print("\nTo-Do List:")
        todo.view_tasks()
        print("\nOptions: add, update, delete, complete, exit")
        choice = input("Choose an option: ")

        if choice == "add":
            task = input("Enter the task: ")
            todo.add_task(task)
        elif choice == "update":
            index = int(input("Enter task number to update: ")) - 1
            new_task = input("Enter new task: ")
            todo.update_task(index, new_task)
        elif choice == "delete":
            index = int(input("Enter task number to delete: ")) - 1
            todo.delete_task(index)
        elif choice == "complete":
            index = int(input("Enter task number to mark as complete: ")) - 1
            todo.mark_completed(index)
        elif choice == "exit":
            break
        else:
            print("Invalid option. Please try again.")

if __name__ == "__main__":
    main()
