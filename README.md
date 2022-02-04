
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
  
   ![image](https://user-images.githubusercontent.com/98145574/152293757-b4027bd8-1812-404b-9bb9-8d9b5d4e3b0a.png)<br><br>
        
 4.C#program to create a Gray code.
 using System;<br>

namespace Exercises<br>
{<br>
    class GrayCode<br>
    {<br>
        static int getGray(int n)<br>
        {<br>
            return n^(n>>1);<br>
        }<br>
        static void Main(string[] args)<br>
        {<br>
            int InputNum, GrayNum;<br>
            Console.Write("\nenter the decinmal number:");<br>
            InputNum = Convert.ToInt32(Console.ReadLine());<br>


            Console.WriteLine("\nBinary equivalent of {0}:   {1}", InputNum, Convert.ToString(InputNum, 2));<br>
            GrayNum = getGray(InputNum);<br>
            Console.WriteLine("\nGray code equivalent of {0}   {1}", InputNum, Convert.ToString(GrayNum, 2));<br>
        }<br>
    }<br>
}<br>

output:
![image](https://user-images.githubusercontent.com/98145574/152296526-cce86ec1-013b-4d8e-a2b1-76ecbd81a18d.png)<br><br>

5.C#program to calculate volume of two boxes and find the resultant volume after addition og two boxes by implementing  operator overloading.

using System;<br>


namespace Exercises<br>
{<br>
    class Box<br>
    {<br>
        float width;<br>
        float height;<br>
        float length;<br>

        public float Volume<br>
        {<br>
            get { return width * height * length; }<br>
        }<br>
        public Box(float width, float height, float length)<br>
        {<br>
            this.width = width;<br>
            this.height = height;<br>
            this.length = length;<br>
        }<br>
        public static float operator +(Box box1, Box box2)<br>
        {<br>
            return box1.Volume + box2.Volume;<br>
        }<br>

        public override String ToString()<br>
        {<br>
            return "box with width" + width + ",height" + height + " and length" + length;<br>
        }<br>
    }<br>

    class OperatorOverloading<br>
    {<br>
        public static void Main()<br>
        {<br>
            Box box1 = new Box(10, 20, 30);<br>
            Box box2 = new Box(25, 32, 15);<br>

            Console.WriteLine("Volume of {0} is:{1}", box1, box1.Volume);<br>
            Console.WriteLine("Volume of {0} is:{1}", box2, box2.Volume);<br>
            Console.WriteLine("Volume after adding boxes:{0}", box1 + box2);<br>
        }<br>
    }<br>
}<br>

output:

![image](https://user-images.githubusercontent.com/98145574/152300079-0074c081-3cfd-42d2-9108-5f473d07879c.png)


6.C#Program to Implement Principles of Delegates(Converting input string toUpercase first,last and entire string).
using System;


namespace Exercises<br>
{<br>
    class Delegates<br>
    {<br>
        delegate string UppercaseDelegate(string input);<br>
        static string UppercaseFirst(string input)<br>
        {<br>
            char[] buffer = input.ToCharArray();<br>
            buffer[0] = char.ToUpper(buffer[0]);<br>
            return new string(buffer);<br>
        }<br>
        static string UppercaseLast(string input)<br>
        {<br>
            char[] buffer = input.ToCharArray();<br>
            buffer[buffer.Length - 1] = char.ToUpper(buffer[buffer.Length - 1]);<br>
            return new string(buffer);<br>

        }<br>
        static string UppercaseAll(string input)<br>
        {<br>
            return input.ToUpper();<br>
        }<br>
        static void WriteOutput(string input, UppercaseDelegate del)<br>
        {<br>
            Console.WriteLine("input string:{0}", input);<br>
            Console.WriteLine("Output String:{0}", del(input));<br>
        }<br>
        static void Main()<br>
        {<br>
            WriteOutput("tom", new UppercaseDelegate(UppercaseFirst));<br>
            WriteOutput("tom", new UppercaseDelegate(UppercaseLast));<br>
            WriteOutput("tom", new UppercaseDelegate(UppercaseAll));<br>

        }<br>
    }<br>
}<br>




output:

![image](https://user-images.githubusercontent.com/98145574/152475297-3268c380-fa5c-41fc-b037-2ad96d379f7f.png)

7.C# Program to generateRegister number automatically for 100 students using satic constructor.<br>

using System;<br>

namespace Exercises<br>
{<br>
    class RegisterNum<br>
    {<br>
        int regno;<br>
        static int startNum;<br>

        static RegisterNum()<br>
        {<br>
            startNum = 20210000;<br>

        }<br>
        RegisterNum()<br>
        {<br>
            regno = ++startNum;<br>
        }<br>
        public static void Main(string[] args)<br>
        {<br>
            for (int i = 0; i < 100; i++)<br>
            {<br>
                RegisterNum Student = new RegisterNum();<br>
                Console.WriteLine("Student {0}:{1}", i+1, Student.regno);<br>
            }<br>
        }<br>
    }<br>
}<br>


output:

![image](https://user-images.githubusercontent.com/98145574/152477061-fef3c19f-d953-42c0-b9ab-7264873d7f29.png)<br>
![image](https://user-images.githubusercontent.com/98145574/152477565-2290d2ca-aced-4ad1-b40f-d94987de1b71.png)<br>
![image](https://user-images.githubusercontent.com/98145574/152477668-527576b6-027e-492f-864c-624b3b02c2dc.png)

8.C# program to find the frequency of the word "is" in a given sentence.

using System;<br>

namespace Exercises<br>
{<br>
    class FrequencyIS<br>
    {<br>
        static void Main(string[] args)<br>
        {<br>
            int count = 0;<br>
            string inputString;<br>
            Console.WriteLine("\n----Frequency of word 'is'-----");<br>
            Console.Write("\nenter the input String:");<br>
            inputString=Console.ReadLine();<br>
            char[] separator = { ',',' ', '.','!','\n'};<br>
            string testString = inputString.ToLower();<br>
            String[] outcomes = testString.Split(separator);<br>

            foreach(String s in outcomes)<br>
            {<br>
                Console.WriteLine(s);<br>
                if (s == "is")<br>
                    count++;<br>

            }<br>
Console.WriteLine("\nNumber of 'is' in'"+inputString+"'is:"+count);<br>
        }<br>
    }<br>
}<br>

output:

![image](https://user-images.githubusercontent.com/98145574/152479984-c893eb27-34c5-455d-b66b-175db2c7bd2f.png)

9.C# program that benchmarks 2D,jagged array allocation.

using System;<br>
using System.Diagnostics;<br>

namespace Exercises<br>
{<br>
    class BenchmarkAllocatin<br>
{<br>
       const int _max=100000;<br>
            static void Main(string[] args)<br>
        {<br>
            var Arr2D = new int[100, 100];<br>
            var ArrJagged = new int[100][];<br>

            for (int i = 0; i < 100; i++)<br>
            {<br>
                ArrJagged[i] = new int[100];<br>
            }<br>

            var Stopwatch2D = Stopwatch.StartNew();<br>
            for (int i = 0; i<_max; i++)<br>
            {<br>
                for (int j = 0; j < 100; j++)<br>
                {<br>
                    for (int k = 0; k < 100; k++)<br>
                    {<br>
                        Arr2D[j, k] = k;<br>
                    }<br>
                }<br>
            }<br>
            Stopwatch2D.Stop();<br>

            var StopwatchJagged=Stopwatch.StartNew();<br>
            for (int i = 0; i < _max; i++)<br>
            {<br>
                for (int j = 0; j < 100; j++)<br>
                {<br>
                    for (int k = 0; k < 100; k++)<br>
                    {<br>
                        ArrJagged[j][k] = k;<br>
                    }<br>
                }<br>
            }<br>

            StopwatchJagged.Stop();<br>
            Console.Write("\nTime taken for allocation in case of 2D array:");<br>
            Console.WriteLine(Stopwatch2D.Elapsed.TotalMilliseconds + "milliseconds");<br>
            Console.Write("\nTime taken for allocation in case  of jagged array:");<br>
            Console.WriteLine(StopwatchJagged.Elapsed.TotalMilliseconds + "milliseconds");<br>

        }<br>
    }<br>
}<br>
output:

![image](https://user-images.githubusercontent.com/98145574/152484081-28adfd48-b3a4-4663-8a40-8d651498b554.png)






