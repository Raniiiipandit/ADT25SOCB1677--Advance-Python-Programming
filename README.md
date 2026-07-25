Problem Statement

Design and implement a Python program that generates a dynamic report using Object-Oriented Programming concepts. The program should demonstrate the following features:

Decorators – Create a decorator function that adds extra formatting (a border of asterisks) around the output of a method, without modifying the method's original code.
Class Method – Implement a class-level attribute template that represents the report's template. Provide a class method that allows the template to be changed for all instances of the class at once, rather than for a single object.
Constructor (__init__) – Define a constructor that automatically initializes each report object with a title and content when it is created.
Magic Method (__str__) – Override the __str__ method so that printing a report object displays a clean, readable summary containing its template, title, and content.


def decorator(function):
    def wrapper(*args, **kwargs):
        print("*" * 20)
        function(*args, **kwargs)
        print("*" * 20)
    return wrapper


class Report:
    template = "New Report"

    def __init__(self, title, content):
        self.title = title
        self.content = content

    @classmethod
    def change_template(cls, new_template):
        cls.template = new_template

    def __str__(self):
        return (
            f"Template: {self.template}\n"
            f"Title: {self.title}\n"
            f"Content: {self.content}"
        )

    @decorator
    def show_report(self):
        print(self)


Report.change_template("Student Report")

r1 = Report("The 48 laws of Power", "self help")
r1.show_report()