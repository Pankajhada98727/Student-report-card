# Student-report-card

// Constructor function for Student
function Student(name, roll_no, className, section, marks_of_5_subjects) {
    this.name = name;
    this.roll_no = roll_no;
    this.className = className;
    this.section = section;
    this.marks_of_5_subjects = marks_of_5_subjects;

    // Method to print top three subjects based on marks
    this.printTop3Subjects = function () {
        // Sorting the subjects based on marks in descending order
        const subjects = Object.keys(this.marks_of_5_subjects);
        subjects.sort((a, b) => this.marks_of_5_subjects[b] - this.marks_of_5_subjects[a]);

        // Printing the top three subjects
        console.log("Top 3 Subjects:");
        for (let i = 0; i < 3; i++) {
            console.log(`${i + 1}. ${subjects[i]}`);
        }
    };

    // Method to print the report card
    this.printReportCard = function () {
        // Calculate total marks and percentage (assuming 500 total marks for 5 subjects)
        const totalMarks = Object.values(this.marks_of_5_subjects).reduce((sum, mark) => sum + mark, 0);
        const percentage = (totalMarks / 500) * 100;

        // Printing the report card
        console.log("+--------------------+");
        console.log("|     REPORT CARD    |");
        console.log("+--------------------+");
        console.log(`| Name     - ${this.name}`);
        console.log(`| Roll no. - ${this.roll_no}`);
        console.log(`| Class    - ${this.className}`);
        console.log(`| Section  - ${this.section}`);
        for (const subject in this.marks_of_5_subjects) {
            console.log(`| ${subject}  - ${this.marks_of_5_subjects[subject]}`);
        }
        console.log(`| Percentage - ${percentage.toFixed(2)} %`);
        console.log("+--------------------+");
    };
}

// Example usage:
const student1 = new Student("Huzaifa", 16, "X", "A", {
    science: 73,
    maths: 75,
    social_science: 79,
    english: 80,
    hindi: 67
});

// Calling methods
student1.printTop3Subjects();
student1.printReportCard();
