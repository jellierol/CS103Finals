#1.
print("1.")
class Vehicle:
	def __init__(self, name):
		self.name = name

	def test(self):
		print(self.name, 'is a Vehicle.')

class Impostor:
	def __init__(self, name):
		self.name = name

	def test(self):
		print(self.name, 'is an Impostor.')
		
class SchoolBus(Vehicle):
	pass

SB1 = SchoolBus('School Bus 1')
SB2 = Impostor('School Bus 2')

SB1.test()
SB2.test()
print()

#2.
print("2.")
class Employee:
	def __init__(self, name, department):
		self.name = name
		self.department = department

	@classmethod
	def from_dict(cls, emp_dict):
		return cls(emp_dict["name"], emp_dict["department"])

	def display(self):
		print(f"Name: {self.name}")
		print(f"Department: {self.department}")

	@classmethod
	def from_string(cls, emp_string):
		name, department = emp_string.split(" - ")
		return cls(name, department)

e1 = Employee("Anya", "Human Resources")
e2 = Employee.from_string("Swansea - Operations")
e3 = Employee.from_string("Daisuke - Operations")
e4_info = {"name": "Curly", "department": "Executive"}
e4 = Employee.from_dict(e4_info)
e5_info = {"name": "Jimmy", "department": "Executive"}
e5 = Employee.from_dict(e5_info)

e1.display()
print()
e2.display()
print()
e3.display()
print()
e4.display()
print()
e5.display()
print()

#3. 
print("3.")
class School:
	def __init__(self, name):
		self.name = name
		self.students = []

	def add_details(self, StudentName, GPA):
		self.students.append((StudentName, GPA))

	def display(self):
		print(self.name, "Students:")
		for student in self.students:
			name, GPA = student
			print(f"- {name} (GPA: {GPA})")
		print()

class SchoolOne(School):
	pass

class SchoolTwo(School):
	pass

S1 = SchoolOne('Westurburg High')
S2 = SchoolTwo('Northshore High')

S1.add_details("Veronica", "4.00")
S1.add_details("Jason", "2.30")
S1.add_details("Heather", "2.70")

S2.add_details("Cady", "4.00")
S2.add_details("Aaron", "3.30")
S2.add_details("Regina", "3.00")

S1.display()
S2.display()

#4.
print("4.")
class Vector:
	def __init__(self, x, y):
		self.x = x
		self.y = y

	def __add__(self, other):
		if isinstance(other, Vector):
			return Vector(self.x + other.x, self.y + other.y)
		return NotImplemented

	def __str__(self):
        	return f"Vector({self.x}, {self.y})"

V1 = Vector(4, -12)
V2 = Vector(6, 7)

VSum = V1 + V2

print(VSum)
print()

#5.
print("5.")
class Book:
	def __init__(self, title, author):
		self.title = title
		self.author = author

	def book_details(self):
		print(f"Title: {self.title}")
		print(f"Author: {self.author.get_info()}")
		print()

class Author:
	def __init__(self, name, nationality):
		self.name = name
		self.nationality = nationality

	def get_info(self):
		return f"{self.name} ({self.nationality})"

a1 = Author("Soman Chainani", "American")
a2 = Author("Craig Russel", "British")
a3 = Author("Lisa Wingate", "American")

b1 = Book("The School for Good and Evil", a1)
b2 = Book("The Story Keeper", a3)
b3 = Book("Brother Grimm", a2)
b4 = Book("The School for Good and Evil: A World Without Princes", a1)

b1.book_details()
b2.book_details()
b3.book_details()
b4.book_details()