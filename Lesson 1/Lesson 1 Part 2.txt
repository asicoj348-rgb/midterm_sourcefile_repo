class Student {
    constructor(name, scores) {
        this.name = name;
        this.scores = scores;
    }

    getAverage() {
        let sum = 0;
        for (let i = 0; i < this.scores.length; i++) {
            sum += this.scores[i];
        }
        return sum / this.scores.length;
    }

    getLetterGrade() {
        const average = this.getAverage();
        if (average >= 90) {
            return 'A';
        } else if (average >= 80) {
            return 'B';
        } else if (average >= 70) {
            return 'C';
        } else if (average >= 60) {
            return 'D';
        } else {
            return 'F';
        }
    }
}

function analyzeClass(students) {
    console.log("------- STUDENT REPORT -------");
    
    let totalClassSum = 0;
    let highestAverage = -1;
    let topStudentName = "";

    for (let i = 0; i < students.length; i++) {
        const student = students[i];
        const avg = student.getAverage();
        const letterGrade = student.getLetterGrade();
        
        console.log(`${student.name} - Average: ${avg.toFixed(1)} | Grade: ${letterGrade}`);
        
        totalClassSum += avg;
        
        if (avg > highestAverage) {
            highestAverage = avg;
            topStudentName = student.name;
        }
    }

    const classAverage = totalClassSum / students.length;

    console.log("------------------------------");
    console.log(`Class Average: ${classAverage.toFixed(1)}`);
    console.log(`Top Student: ${topStudentName} with ${highestAverage.toFixed(1)}`);
}

const studentData = [
    { name: "Lany", scores: [85, 90, 92] },
    { name: "Bongbung", scores: [70, 75, 68] },
    { name: "Dutherthe", scores: [95, 98, 92] },
    { name: "Pico", scores: [55, 60, 58] }
];

const studentInstances = studentData.map(data => new Student(data.name, data.scores));

analyzeClass(studentInstances);