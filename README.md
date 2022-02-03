
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

output:<br>
![image](https://user-images.githubusercontent.com/98145574/152285918-683d3d1b-cd3a-4e67-8710-97e6aac8a157.png)<br><br>
![image](https://user-images.githubusercontent.com/98145574/152286153-52704dc5-4af8-4968-9373-c52995162fe2.png)

3.C# program to illustrate multilevel inheritance with virtual methods(displaying student details.)
using System;<br>
namespace Exercises<br>
{<br>
    class PersonalDetails<br>
    {<br>
        string name;<br>
        int age;<br>
        string gender;<br>

        public PersonalDetails(string name, int age, string gender)<br>
        {<br>
            this.name = name;<br>
            this.age = age;<br>
            this.gender = gender;<br>

        }<br>

        public virtual void Display()<br>
        {<br>
            Console.WriteLine("\n-----PERSONEL DETAILS-------\n");<br>
            Console.WriteLine("Name   :" + name);<br>
            Console.WriteLine("Age    :" + age);<br>
            Console.WriteLine("Gender  :" + gender);<br>
            }<br>
            
    }<br>

    class CourseDetails : PersonalDetails<br>
    {<br>
    
        int regno;<br>
        string course;<br>
        int semester;<br>


        public CourseDetails(string name, int age, string gender, int regno, string course, int semester) : base(name, age, gender)<br>
        {<br>
            this.regno = regno;<br>
            this.course = course;<br>
            this.semester = semester;<br>

        }<br>

        public override void Display()<br>
        {<br>
            base.Display();<br>
            Console.WriteLine("\n----COURSE DETAILS----\n");<br>
            Console.WriteLine("Register number:" + regno);<br>
            Console.WriteLine("course    :" + course);<br>
            Console.WriteLine("semeaster     :" + semester);<br>


        }<br>
    }<br>
    class MarksDetails : CourseDetails<br>
    {<br>
        int[] marks = new int[5];<br>
        int total;<br>
        float average;<br>
        string grade;<br>
        int flagFail;<br>

        public MarksDetails(string name, int age, string gender, int regno, string Course, int semester, int[] marks) : base(name, age, gender, regno, Course, semester)<br>

        {<br>
            total = 0;<br>
            for (int i = 0; i < 5; i++)<br>
            {<br>
                this.marks[i] = marks[i];<br>
                total += marks[i];<br>

                if (marks[i] < 35)<br>
                {<br>
                    flagFail = 1;<br>
                }<br>
            }<br>

            Calculate();<br>

        }<br>
        private void Calculate()<br>
        {<br>
            average = total / 5;<br>

            if (flagFail == 1 || average < 40)<br>
                grade = "Fail";<br>
            else if (average >= 70)<br>
                grade = "Distinction";<br>
            else if (average >= 60)<br>
                grade = "First class";<br>
            else if (average >= 50)<br>
                grade = "second class";<br>
            else<br>
                grade = "pass Class";<br>
        }<br>

        public override void Display()<br>
        {<br>
            base.Display();<br>
            Console.WriteLine("\n------MARKS DETAILS--------\n");<br>
            Console.Write("Marks in 5 subjects:");<br>
            for (int i = 0; i < 5; i++)<br>
                Console.Write(marks[i] + "  ");<br>
            Console.WriteLine();<br>
            Console.WriteLine("Total   :" + total);<br>
            Console.WriteLine("Average    :" + average);<br>
            Console.WriteLine("Grade    :" + grade);<br>
        }<br>

    }<br>

    class Multilevel<br>
    {<br>
        public static void Main(string[] args)<br>
        {<br>
            MarksDetails Student1 = new MarksDetails("neha", 22, "female", 20190001, "MCA", 5, new int[] { 77, 80, 98, 95, 90 });<br>
            Student1.Display();<br>
        }<br>
    }<br>
}<br>

  output:
        ![image](https://user-images.githubusercontent.com/98145574/152293757-b4027bd8-1812-404b-9bb9-8d9b5d4e3b0a.png)



