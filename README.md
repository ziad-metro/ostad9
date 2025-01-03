abstract class Role {
  void displayRole();
}

class Person implements Role {
  String name;
  int age;
  String address;

  Person(this.name, this.age, this.address);

  @override
  void displayRole() {
    print("Role: Person");
  }

  String get personInfo => 'Name: $name\nAge: $age\nAddress: $address';
}

class Student extends Person {
  String studentID;
  String grade;
  List<double> courseScores;

  Student(String name, int age, String address, this.studentID, this.grade, this.courseScores)
      : super(name, age, address);

  @override
  void displayRole() {
    print("Role: Student");
  }

  double calculateAverageScore() {
    if (courseScores.isEmpty) return 0.0;
    return courseScores.reduce((a, b) => a + b) / courseScores.length;
  }

  void displayStudentInfo() {
    displayRole();
    print(personInfo);
    print('Average Score: ${calculateAverageScore().toStringAsFixed(1)}');
  }
}

class Teacher extends Person {
  String teacherID;
  List<String> coursesTaught;

  Teacher(String name, int age, String address, this.teacherID, this.coursesTaught)
      : super(name, age, address);

  @override
  void displayRole() {
    print("Role: Teacher");
  }

  void displayTeacherInfo() {
    displayRole();
    print(personInfo);
    print('Courses Taught:');
    for (var course in coursesTaught) {
      print('- $course');
    }
  }
}

void main() {
  Student student = Student(
    'John Doe',
    20,
    '123 Main St',
    'S12345',
    'A',
    [90, 85, 82],
  );

  Teacher teacher = Teacher(
    'Mrs. Smith',
    35,
    '456 Oak St',
    'T98765',
    ['Math', 'English', 'Bangla'],
  );

  print('Student Information:\n');
  student.displayStudentInfo();

  print('\n');

  print('Teacher Information:\n');
  teacher.displayTeacherInfo();
}
