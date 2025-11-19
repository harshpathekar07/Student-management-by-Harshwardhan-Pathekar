# Student-management-by-Harshwardhan-Pathekar
Student Record Management System allows adding, searching, and displaying student records using a simple Python CLI menu and in-memory list for efficient management and easy access to student data.
class StudentRecordSystem:
    def __init__(self):
       
        self.students = []

    def add_student(self):
        print("Add New Student")
        student_id = input("Enter student ID: ").strip()
        # Check if student ID already exists
        if any(s['id'] == student_id for s in self.students):
            print("Student ID already exists. Try again.")
            return
        name = input("Enter student name: ").strip()
        try:
            cgpa = float(input("Enter CGPA: ").strip())
        except ValueError:
            print("Invalid CGPA. Must be a number.")
            return
        student = {'id': student_id, 'name': name, 'cgpa': cgpa}
        self.students.append(student)
        print(f"Student {name} added successfully.")

    def search_student(self):
        student_id = input("Enter student ID to search: ").strip()
        for s in self.students:
            if s['id'] == student_id:
                print(f"Student found: ID={s['id']}, Name={s['name']}, CGPA={s['cgpa']}")
                return
        print("Student not found.")

    def display_all(self):
        if not self.students:
            print("No student records found.")
            return
        print("All Student Records:")
        print("-" * 40)
        for s in self.students:
            print(f"ID: {s['id']}, Name: {s['name']}, CGPA: {s['cgpa']}")
        print("-" * 40)

    def run(self):
        while True:
            print("\n--- Student Record Management System ---")
            print("1. Add Student")
            print("2. Search Student")
            print("3. Display All Students")
            print("4. Exit")
            choice = input("Enter your choice: ").strip()

            if choice == '1':
                self.add_student()
            elif choice == '2':
                self.search_student()
            elif choice == '3':
                self.display_all()
            elif choice == '4':
                print("Exiting. Goodbye!")
                break
            else:
                print("Invalid choice. Please enter 1-4.")

if __name__ == "__main__":
    system = StudentRecordSystem()
    system.run()
