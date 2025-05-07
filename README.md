Here is a complete Student Performance Tracker in Python, ideal for uploading to your GitHub repository. This project includes:

Adding student records

Recording marks for subjects

Calculating total, average, and grade

Viewing student performance



---

Student Performance Tracker – Python Code

# student_tracker.py

class Student:
    def __init__(self, student_id, name):
        self.student_id = student_id
        self.name = name
        self.marks = {}

    def add_marks(self, subject, mark):
        self.marks[subject] = mark

    def calculate_total(self):
        return sum(self.marks.values())

    def calculate_average(self):
        if not self.marks:
            return 0
        return self.calculate_total() / len(self.marks)

    def get_grade(self):
        avg = self.calculate_average()
        if avg >= 90:
            return "A+"
        elif avg >= 80:
            return "A"
        elif avg >= 70:
            return "B"
        elif avg >= 60:
            return "C"
        elif avg >= 50:
            return "D"
        else:
            return "F"

    def display(self):
        print(f"\nStudent ID: {self.student_id}")
        print(f"Name: {self.name}")
        for subject, mark in self.marks.items():
            print(f"{subject}: {mark}")
        print(f"Total: {self.calculate_total()}")
        print(f"Average: {self.calculate_average():.2f}")
        print(f"Grade: {self.get_grade()}")


class PerformanceTracker:
    def __init__(self):
        self.students = {}

    def add_student(self):
        student_id = input("Enter Student ID: ")
        name = input("Enter Student Name: ")
        self.students[student_id] = Student(student_id, name)
        print("Student added successfully.")

    def add_marks(self):
        student_id = input("Enter Student ID: ")
        student = self.students.get(student_id)
        if not student:
            print("Student not found.")
            return
        subject = input("Enter Subject Name: ")
        mark = float(input("Enter Marks: "))
        student.add_marks(subject, mark)
        print("Marks added.")

    def view_student(self):
        student_id = input("Enter Student ID: ")
        student = self.students.get(student_id)
        if student:
            student.display()
        else:
            print("Student not found.")

    def run(self):
        while True:
            print("\n--- Student Performance Tracker ---")
            print("1. Add Student")
            print("2. Add Marks")
            print("3. View Student Report")
            print("4. Exit")
            choice = input("Choose an option: ")

            if choice == '1':
                self.add_student()
            elif choice == '2':
                self.add_marks()
            elif choice == '3':
                self.view_student()
            elif choice == '4':
                print("Exiting tracker.")
                break
            else:
                print("Invalid option. Try again.")


if __name__ == "__main__":
    tracker = PerformanceTracker()
    tracker.run()
