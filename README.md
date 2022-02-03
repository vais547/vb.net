
# vb.net
1. c# program to print a Binary Triangle.

using System;<br>

namespace Exercises<br>
{<br>
    class BinaryTriangle<br>
    {<br>
        static void Main(String[] args)<br>
        {<br>
            int number, digit = 1;<br>
            Console.Write("\nEnter the number of lines:");<br>
            number = Convert.ToInt32(Console.ReadLine());<br>


            for (int i = 1; i <= number; i++)<br>
            {<br>
                for (int space = number - i;space > 0;space--)<br>
                {<br>
                    Console.Write(" ");<br>
                }<br>
                for (int j = 0; j < i; j++)<br>
                {<br>
                    Console.Write(digit + " ");<br>
                    digit = (digit == 1) ? 0 : 1;<br>
                }<br>
                Console.Write("\n");<br>
            }<br>
        }<br>
    }<br>
}<br>

output:
![image](https://user-images.githubusercontent.com/98145574/150483817-c9a65b1b-f1c5-4c82-b3ec-7983df9c8c39.png)<br><br><br>

2.c#program to check whether the entered number is an  amicable number r not.
using System;<br>

namespace Exercises<br>
{<br>
    class AmicableNumber<br>
    {<br>
        static void Main(string[] args)<br>
        {<br>
            int num1, num2, sum1 = 0, sum2 = 0;<br>
            Console.WriteLine("\n------AMICABLE NUMBERS-----\n");<br>
            Console.Write("\nenter the first number:");<br>
            num1 = Convert.ToInt32(Console.ReadLine());<br>
            Console.Write("\nenter the second number:");<br>
            num2= Convert.ToInt32(Console.ReadLine());<br>

            for(int i=1;i<num1;i++)<br>
            {<br>
                if(num1%i==0)<br>
                    {<br>
                        sum1 +=i;<br>
                    }<br>
            }<br>
<br>
            for (int i = 1; i < num2; i++)<br>
            {<br>
                if (num2 % i == 0)<br>
                {<br>
                    sum2 += i;<br>
                }<br>
            }<br>

            if (sum1 == num2 && sum2 == num1)<br>
            {<br>
                Console.WriteLine("\nThe numbers {0} and {1} are amicable.", num1, num2);<br>
            }<br>
            else<br>
            {<br>
                Console.WriteLine("\nThe numbers {0} and {1} are  notamicable.", num1, num2);<br>
            }<br>
            
        }<br>
    }<br>
}<br>

![image](https://user-images.githubusercontent.com/98145574/152285918-683d3d1b-cd3a-4e67-8710-97e6aac8a157.png)<br><br>
![image](https://user-images.githubusercontent.com/98145574/152286153-52704dc5-4af8-4968-9373-c52995162fe2.png)

3.C# program to illustrate multilevel inheritance with virtual methods(displaying student details.)
using System;
namespace Exercises
{
    class PersonalDetails
    {
        string name;
        int age;
        string gender;

        public PersonalDetails(string name, int age, string gender)
        {
            this.name = name;
            this.age = age;
            this.gender = gender;

        }

        public virtual void Display()
        {
            Console.WriteLine("\n-----PERSONEL DETAILS-------\n");
            Console.WriteLine("Name   :" + name);
            Console.WriteLine("Age    :" + age);
            Console.WriteLine("Gender  :" + gender);
        }
    }

    class CourseDetails : PersonalDetails
    {
        int regno;
        string course;
        int semester;


        public CourseDetails(string name, int age, string gender, int regno, string course, int semester) : base(name, age, gender)
        {
            this.regno = regno;
            this.course = course;
            this.semester = semester;

        }

        public override void Display()
        {
            base.Display();
            Console.WriteLine("\n----COURSE DETAILS----\n");
            Console.WriteLine("Register number:" + regno);
            Console.WriteLine("course    :" + course);
            Console.WriteLine("semeaster     :" + semester);


        }
    }
    class MarksDetails : CourseDetails
    {
        int[] marks = new int[5];
        int total;
        float average;
        string grade;
        int flagFail;

        public MarksDetails(string name, int age, string gender, int regno, string Course, int semester, int[] marks) : base(name, age, gender, regno, Course, semester)

        {
            total = 0;
            for (int i = 0; i < 5; i++)
            {
                this.marks[i] = marks[i];
                total += marks[i];

                if (marks[i] < 35)
                {
                    flagFail = 1;
                }
            }

            Calculate();

        }
        private void Calculate()
        {
            average = total / 5;

            if (flagFail == 1 || average < 40)
                grade = "Fail";
            else if (average >= 70)
                grade = "Distinction";
            else if (average >= 60)
                grade = "First class";
            else if (average >= 50)
                grade = "second class";
            else
                grade = "pass Class";
        }

        public override void Display()
        {
            base.Display();
            Console.WriteLine("\n------MARKS DETAILS--------\n");
            Console.Write("Marks in 5 subjects:");
            for (int i = 0; i < 5; i++)
                Console.Write(marks[i] + "  ");
            Console.WriteLine();
            Console.WriteLine("Total   :" + total);
            Console.WriteLine("Average    :" + average);
            Console.WriteLine("Grade    :" + grade);
        }


    }

    class Multilevel
    {
        public static void Main(string[] args)
        {
            MarksDetails Student1 = new MarksDetails("neha", 22, "female", 20190001, "MCA", 5, new int[] { 77, 80, 98, 95, 90 });
            Student1.Display();
        }
    }
}


