
# vb.net
**1. c# program to print a Binary Triangle.**<br>

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

**output:**
![image](https://user-images.githubusercontent.com/98145574/150483817-c9a65b1b-f1c5-4c82-b3ec-7983df9c8c39.png)<br><br><br>

**2.c#program to check whether the entered number is an  amicable number r not.**<br>

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

**output:**<br>

![image](https://user-images.githubusercontent.com/98145574/152285918-683d3d1b-cd3a-4e67-8710-97e6aac8a157.png)<br><br>
![image](https://user-images.githubusercontent.com/98145574/152286153-52704dc5-4af8-4968-9373-c52995162fe2.png)

**3.C# program to illustrate multilevel inheritance with virtual methods(displaying student details.)**<br>

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

  **output:**
  
   ![image](https://user-images.githubusercontent.com/98145574/152293757-b4027bd8-1812-404b-9bb9-8d9b5d4e3b0a.png)<br><br>
        *
 **4.C# program to create a Gray code**.<br>
 
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

**output:**
![image](https://user-images.githubusercontent.com/98145574/152296526-cce86ec1-013b-4d8e-a2b1-76ecbd81a18d.png)<br><br>

**5.C# program to calculate volume of two boxes and find the resultant volume after addition og two boxes by implementing  operator overloading.**<br>

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

**output:**

![image](https://user-images.githubusercontent.com/98145574/152300079-0074c081-3cfd-42d2-9108-5f473d07879c.png)


**6.C# Program to Implement Principles of Delegates(Converting input string toUpercase first,last and entire string).**<br>

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




**output:**

![image](https://user-images.githubusercontent.com/98145574/152475297-3268c380-fa5c-41fc-b037-2ad96d379f7f.png)

**7.C# Program to generate Register number automatically for 100 students using satic constructor.**<br>

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


**output:**

![image](https://user-images.githubusercontent.com/98145574/152477061-fef3c19f-d953-42c0-b9ab-7264873d7f29.png)<br>
![image](https://user-images.githubusercontent.com/98145574/152477565-2290d2ca-aced-4ad1-b40f-d94987de1b71.png)<br>
![image](https://user-images.githubusercontent.com/98145574/152477668-527576b6-027e-492f-864c-624b3b02c2dc.png)

**8.C# program to find the frequency of the word "is" in a given sentence.**<br>

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

**output:**

![image](https://user-images.githubusercontent.com/98145574/152479984-c893eb27-34c5-455d-b66b-175db2c7bd2f.png)

**9.C# program that benchmarks 2D,jagged array allocation.**<br>

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
**output:**

![image](https://user-images.githubusercontent.com/98145574/152484081-28adfd48-b3a4-4663-8a40-8d651498b554.png)


**10.C# program to find the sum of the values on diagonal of the matrix.**<br>
using System;<br>

namespace Exercises<br>
{<br>
    class SumOfDiagonals<br>
    {<br>
        static void Main(string[] args)<br>
        {<br>
            int MaxRow, MaxCol, Sum = 0;<br>
            int[,] Matrix;<br>

            Console.WriteLine("\n------SUM OF DIAGONAL OF A MATRIX-----\n");<br>
            Console.Write("\nenter the number f rows:");<br>
            MaxRow = Convert.ToInt32(Console.ReadLine());<br>
            Console.Write("\nenter the number f columns:");<br>
            MaxCol = Convert.ToInt32(Console.ReadLine());<br>

            if (MaxRow != MaxCol)<br>
            {<br>
                Console.WriteLine("\nThe Dimensions entered are not not of square matrix.");<br>
                Console.WriteLine("\nExiting the program..");<br>
                return;<br>
            }<br>
            Matrix = new int[MaxRow, MaxCol];<br>
            for (int i = 0; i < MaxRow; i++)<br>
            {<br>
                for (int j = 0; j < MaxCol; j++)<br>
                {<br>
                    Console.Write("\nEnter the ({0},{1})th element of matrix:", (i + 1), (j + 1));<br>
                    Matrix[i,j] = Convert.ToInt32(Console.ReadLine());<br>
                }<br>
            }<br>
            Console.WriteLine("\nThe enterd Matrix is:");<br>
            for (int i = 0; i < MaxRow; i++)<br>
            {<br>
                for (int j = 0; j < MaxCol; j++)<br>
                {<br>
                    Console.Write(" " + Matrix[i, j]);<br>

                    if (i == j)<br>
                    {<br>
                        Sum += Matrix[i, j];<br>
                    }<br>
                }<br>
                    Console.WriteLine();<br>
                }<br>
                Console.WriteLine("\nthe sum of Diagonal is" + Sum);<br>
            }<br>
        }<br>
    }<br>

**output:**

![image](https://user-images.githubusercontent.com/98145574/152489439-cc34906e-8248-4bcd-a3cb-50d00f5ffe5a.png)


**11.C# program to create a file,check the existence of the file and read the contents of the file**.<br><br>

using System;<br>
using System.IO;<br>

namespace Exercises<br>
{<br>
    class FileRead<br>
    {<br>
        public static void Main()<br>
        {<br>
            string fileName;<br>
            while (true)<br>
            {<br>
                Console.WriteLine("\n------MENU---------\n");<br>
                Console.WriteLine("\n1 .create a file");<br>
                Console.WriteLine("\n2 .existence of the file");<br>
                Console.WriteLine("\n3 .read the contenets of the file");<br>
                Console.WriteLine("\n4.Exit");<br>
                Console.Write("\nEnter your choice:");<br>
                int ch = int.Parse(Console.ReadLine());<br>
                switch (ch)<br>

                {<br>
                    case 1:<br>
                        Console.Write("\nEnter the file name create:");<br>
                        fileName = Console.ReadLine();<br>
                        Console.WriteLine("\nwrite the contents to the file:\n");<br>
                        string r = Console.ReadLine();<br>
                        using (StreamWriter fileStr = File.CreateText(fileName))<br>
                        {<br>
                            fileStr.WriteLine(r);<br>
                        }<br>
                        Console.WriteLine("File is creasted...");<br>
                        break;<br>

                    case 2:<br>
                        Console.Write("\nEnter the file name:");<br>
                        fileName = Console.ReadLine();<br>
                        if (File.Exists(fileName))<br>
                        {<br>
                            Console.WriteLine("File exists..");<br>
                        }<br>
                        else<br>
                        {<br>
                            Console.WriteLine("File does not exists in the current directory!");<br>
                        }<br>
                        break;<br>

                    case 3:<br>
                        Console.Write("Enter the file name to read the contents:\n");<br>
                        fileName = Console.ReadLine();<br>
                        if (File.Exists(fileName))<br>
                        {<br>
                            using (StreamReader sr = File.OpenText(fileName))<br>
                            {<br>
                                string s = "";<br>
                                Console.WriteLine("Here is the contents of the file:");<br>
                                while ((s = sr.ReadLine()) != null)<br>
                                {<br>
                                    Console.WriteLine(s);<br>
                                }<br>
                                Console.WriteLine("");<br>
                            }<br>
                        }<br>
                        else<br>
                        {<br>
                            Console.WriteLine("File does not exists");<br>
                        }<br>
                        break;<br>

                    case 4:<br>
                        Console.WriteLine("\nExiting...");<br>
                        return;<br>

                    default:<br>
                        Console.WriteLine("\ninvalied choice");<br>
                        break;<br>


                }<br>
            }<br>
        }<br>
    }<br>
}<br>

**output:**

![image](https://user-images.githubusercontent.com/98145574/154414125-01cf4fa3-685d-46f3-b872-b84143bf3d2a.png)<br>

![image](https://user-images.githubusercontent.com/98145574/154413784-935c5b25-9c0d-4602-9606-72c9b2c72da0.png)<br>
![image](https://user-images.githubusercontent.com/98145574/154413960-de4e56f6-23d4-4872-aac7-aff586d4efe9.png)<br>


**12.C# program to perform File comparision**.<br>

using System;<br>
using System.IO;<br>

namespace Exercises<br>
{<br>
    class FileRead<br>
    {<br>
        public static void Main()<br>
        {<br>
            string file1;<br>
            string file2;<br>

            Console.Write("Enter the first fule path:");<br>
            file1 = Console.ReadLine();<br>

            Console.WriteLine("Enter the second file path:");<br>
            file2 = Console.ReadLine();<br>

            if (!File.Exists(file1))<br>
            {<br>
                Console.WriteLine("First file does not exists!");<br>
            }<br>
            else if (!File.Exists(file2))<br>
            {<br>
                Console.WriteLine("Second file does not exists!");<br>
            }<br>
            else if (File.ReadAllText(file1) == (File.ReadAllText(file2)))<br>
            {<br>
                Console.WriteLine("both file contain the same content");<br>
            }<br>
            else<br>
            {
                Console.WriteLine("Contents of file are not same");<br>
            }<br>

        }<br>
    }   <br>
}<br>


**output:**

file1:<br>
![image](https://user-images.githubusercontent.com/98145574/154418845-62253bb9-8117-486d-9399-1a189e7dc2c4.png)<br>
file2:<br>
![image](https://user-images.githubusercontent.com/98145574/154419114-4f050be0-3d19-478f-b2eb-8be7a27d46a6.png)<br>
file3:<br>
![image](https://user-images.githubusercontent.com/98145574/154419243-32bf4b76-f545-4fd8-a428-7b51ff7eaf31.png)

![image](https://user-images.githubusercontent.com/98145574/154417472-850aad84-27af-466d-9060-45f4ac0da859.png)<br>
![image](https://user-images.githubusercontent.com/98145574/154417824-9964d48a-824e-49bf-a7a1-e13f9a33e817.png)<br>


**13.C# program to Impement IComparableInterface.**<br>

using System;<br>

namespace Exercises<br>
{<br>
    class Fraction:IComparable<br>
    {<br>
        int z, n;<br>
        public Fraction(int z, int n)<br>
        {<br>
            this.z = z;<br>
            this.n = n;<br>
        }<br>
        public static Fraction operator +(Fraction a, Fraction b)<br>
        {<br>
            return new Fraction(a.z * b.n + a.n * b.z, a.n * b.n);<br>
        }<br>
      public static Fraction operator *(Fraction a, Fraction b)<br>
        {<br>
        return new Fraction(a.z* b.z, a.z* b.n);<br>
        }<br>
      public int CompareTo(object obj)<br>
      {<br>
    Fraction f = (Fraction)obj;<br>
        if ((float)z/n<(float)f.z/f.n)<br>
        return-1;<br>
        else if((float)z/n>(float)f.z/f.n)<br>
        return 1;<br>
        else<br>
        return 0;   <br>
       }<br>

public override string ToString()<br>
{<br>
    return z + "/" + n;<br>
}<br>
}<br>
class ICompInterface<br>
{<br>
    public static void Main()<br>
    {<br>
        Fraction[] a =<br>
        {<br>
            new Fraction(5,2),<br>
            new Fraction(29,6),<br>
            new Fraction(4,5),<br>
            new Fraction(10,8),<br>
            new Fraction(34,7)<br>
        };<br>
        Array.Sort(a);  <br>
        Console.WriteLine("Implementing the IComparable Interface in "+" Displaying Fraction:");<br>
            foreach (Fraction f in a)<br>
            {<br>
            Console.WriteLine(f + "");<br>
        }<br>
        Console.WriteLine();<br>
        Console.ReadLine();<br>
 } <br>
}<br>
}<br>

**output:**

![image](https://user-images.githubusercontent.com/98145574/154624572-15cac980-0b1a-4d5d-bbe4-6f8a4107ca03.png)<br><br>

**14.C# program to create thread pools.**<br>

using System;<br>
using System.Threading;<br>


namespace Exercises<br>
{<br>
    class ThreadpoolProg<br>
    {<br>
        public void ThreadFun1(object obj)<br>
        {<br>
            int loop = 0;<br>
            for (loop = 0; loop <= 4; loop++)<br>
            {<br>
                Console.WriteLine("Thread1 is executing");<br>
            }<br>
        }<br>
        public void ThreadFun2(object obj)<br>
        {<br>
            int loop = 0;<br>
            for (loop = 0; loop <= 4; loop++)<br>
            {<br>
                Console.WriteLine("Thread2 is Executing");<br>
            }<br>
        }<br>
        public static void Main()<br>
        {<br>
            ThreadpoolProg TP = new ThreadpoolProg();<br>
            for (int i = 0; i < 2; i++)<br>
            {<br>
                ThreadPool.QueueUserWorkItem(new WaitCallback(TP.ThreadFun1));<br>
                ThreadPool.QueueUserWorkItem(new WaitCallback(TP.ThreadFun2));<br>
            }<br>
            Console.ReadKey();<br>
        }<br>
} <br>
}<br>
**output:**

![image](https://user-images.githubusercontent.com/98145574/154627433-bbd64b0a-4c18-4296-a723-c389936943a3.png)<br>


**15.C#program to demonstrate error handling using Try,catch and finnally bock.**<br>

using System;<br>
  namespace Exercises<br>
    {<br>
    class ExceptionHandling<br>
    {<br>
        static void Main(string[]args)<br>
        {<br>
            Age a = new Age();<br>
            try<br>
            {<br>
                a.displayAge();<br><br>
            }<br>
            catch (AgeIsNegativeException e)<br>
            {<br>
                Console.WriteLine("AgeIsNegativeExcepion:{0}", e.Message);<br>
            }<br>
            finally<br>
            {<br>
                Console.WriteLine("Execuion of Finally block is done.");<br>
            }<br>
        }<br>
    }<br>
}<br>
public class AgeIsNegativeException : Exception<br>
{<br>
    public AgeIsNegativeException(string message):base(message)<br>
    {<br>
    }<br>
}<br>
public class Age<br>
{<br>
    int age = -5;<br>
    public void displayAge()<br>
    {<br>
        if(age<0)<br>
        {<br>
            throw (new AgeIsNegativeException("Age cannot be negative")); <br>
        }<br>
        else<br>
        {<br>
            Console.WriteLine("Age is:{0}",age);<br>
        }<br>
    }<br>
}<br>

**output:**

![image](https://user-images.githubusercontent.com/98145574/154629257-a966556d-8546-422c-8c1c-92774a0274cd.png)<br><br>

**16.write a program on fibonacci series.**<br>

using System;<br>

public class FibonacciExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int n1=0,n2 = 1,n3,i,number;<br>
        Console.Write("enter the number of elements:");<br>
        number = int.Parse(Console.ReadLine());<br>
        Console.Write(n1+ " "+n2+" ");<br>
        for (i = 2; i < number; ++i)<br>
        {<br>
            n3 = n1 + n2;<br>
            Console.Write(n3 + " ");<br>
            n1 = n2;<br>
            n2 = n3;<br>
        }<br>
    }<br>
}<br>

**output:**

![image](https://user-images.githubusercontent.com/98145574/155658246-a3b87433-e28d-4927-959f-de4b75ab3166.png)<br>

**17.write a c# program to check prime number.**<br>
using System;<br>

public class PrimeNumberExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int n, i, m = 0, flag = 0;<br>
        Console.Write("Enter the number to check Prime:");<br>
        n=int.Parse(Console.ReadLine());<br>
        m = n / 2;<br>
        for(i=2;i<=m;i++)<br>
        {<br>
            if(n%i==0)<br>
            {<br>
                Console.Write("Number is not Prime.");<br>
                flag = 1;<br>
                break;<br>
           } <br>
        }<br>
        if (flag == 0)<br>
            Console.Write("number is prime.");<br>
    }<br>
}<br>

**output:**

![image](https://user-images.githubusercontent.com/98145574/155659683-0dd76953-bf0b-442c-9749-a6ea32e3dabd.png)<br>
![image](https://user-images.githubusercontent.com/98145574/155659785-03fccd36-b48b-4ff5-8f17-e2589b4cfec1.png)<br>

**18.write a C# program to check palindrome number.**<br>
using System;<br>

public class PalindromeExample<br>

{<br>
    public static void Main(string[] args)<br>
    { <br>
    int n, r, sum = 0, temp;<br>
    Console.Write("enter the number:");<br>
        n=int.Parse(Console.ReadLine());<br>
        temp=n;<br>
        while(n>0)<br>
        {<br>
        r=n%10;<br>
        sum=(sum*10)+r;<br>
        n=n/10;<br>
}<br><br>
   if(temp == sum)<br>
    Console.Write("Number is Palindrome");<br>
        else<br>
    Console.Write("Number is not a Palindrome");<br>
}<br>
}<br>

**output:**

![image](https://user-images.githubusercontent.com/98145574/155661732-5c9c7a97-676f-4558-9abb-4f96da91c3c3.png)<br>
![image](https://user-images.githubusercontent.com/98145574/155661885-376b92c5-8fd1-4062-acbe-e3787a028c8d.png)<br>

**19.Write a C# program to print factorial of a number.**<br>

using System;<br>

public class FactorialExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int i, fact = 1, number;<br>
        Console.Write("Enter any number:");<br>
        number = int.Parse(Console.ReadLine());<br>
        for (i = 1; i <= number; i++)<br>
        { <br>
            fact = fact * i;<br>
        }<br>
       Console.Write("Factorial of" +number+" is: "+fact);<br>
    } <br>
}<br>
**output:**

![image](https://user-images.githubusercontent.com/98145574/155662818-0668f3f9-18f1-4622-8bde-1d7f322149b8.png)<br><br>

**20.Write a C# program to check amstrong number.**<br>


using System;<br>

public class AmstrongExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int n, r, sum = 0, temp;<br>
        Console.Write("enter the number=");<br>
        n = int.Parse(Console.ReadLine());<br>
        temp = n;<br>
        while(n>0)<br>
        {<br>
            r = n % 10;<br>
            sum=sum+(r*r*r);<br>
            n = n / 10;<br>
        }<br>
        if (temp == sum)<br>
            Console.Write("Amstrong Number.");<br>
        else<br>
            Console.Write("Not Amstrong number.");<br>
    }<br>
}<br>

**output:**


![image](https://user-images.githubusercontent.com/98145574/155663703-eea3a24c-9e0e-4232-8270-8dd4281c7c61.png)<br>
![image](https://user-images.githubusercontent.com/98145574/155663894-038f8d8d-c1f8-447d-9376-c26e474282bb.png)<br>

**21.Write a C# program to print sum of digits.**<br>

using System;<br>

public class SumExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int n, r, sum = 0, m;<br>
        Console.Write("enetr the number:");<br>
        n=int.Parse(Console.ReadLine());<br>
        while(n>0)<br>
        {<br>
            m = n % 10;<br>
            sum = sum + m;<br>
            n = n / 10;<br>
        }<br>
        Console.Write("Sum is=" + sum);<br>
    }<br>
}<br>

**output:**

![image](https://user-images.githubusercontent.com/98145574/155665943-845b02f0-4258-49ad-8e92-b027f28b0d44.png)<br><br>


**22.Write a C# program to reverse a given number.**<br>

using System;<br>

public class ReverseExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int n,reverse=0,rem;<br>
        Console.Write("enter the number:");<br>
        n = int.Parse(Console.ReadLine());<br>
        while (n != 0)<br>
        {<br>
            rem = n % 10;<br>
            reverse = reverse * 10 + rem;<br>
            n /= 10;<br>
        }<br>
        Console.Write("Reversed number:" + reverse);<br>
    }<br>
}<br>

**output:**

![image](https://user-images.githubusercontent.com/98145574/155667241-a3ce4a59-e138-49f6-aab4-6c29c6e427d5.png)<br>

**23.Write a c# program to swap two numbers without using third variable.**<br>

using System;<br>
public class SwapExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int a = 5, b = 10;<br>
        Console.WriteLine("Before swap a= " + a + " b= " + b);<br>
        a = a * b; //a=50 (5*10)<br>      
        b = a / b; //b=5 (50/10)<br>      
        a = a / b; //a=10 (50/5)<br>    
        Console.Write("After swap a= " + a + " b= " + b);<br>
    }<br>
}<br>
**output:**<br>

![image](https://user-images.githubusercontent.com/98145574/156503996-2f96ad72-1386-4c98-81fd-165fe2049e8e.png)<br>

**24.Write a c# program to generate fibonacci triangle.**<br>

using System;<br>
public class PrintExample<br>
{<br>
    public static void Main(string[] args)<br>
    {<br>
        int a = 0, b = 1, i, c, n, j;<br>
        Console.Write("Enter the limit: ");<br>
        n = int.Parse(Console.ReadLine());<br>
        for (i = 1; i <= n; i++)<br>
        {<br>
            a = 0;<br>
            b = 1;<br>
            Console.Write(b + "\t");<br>
            for (j = 1; j < i; j++)<br>
            {<br>
                c = a + b;<br>
                Console.Write(c + "\t");<br>
                a = b;<br>
                b = c;<br>
            }<br>
            Console.Write("\n");<br>
        }<br>
    }<br>
}<br>

**output:**<br>

![image](https://user-images.githubusercontent.com/98145574/156508485-f7e48059-4386-42e1-b02f-362eb0ca4f76.png)<br>

                                                <br>part B<br>
                                                
<br>**25.C# program to convert digits to words.**<br>
using System;<br>
using System.Collections.Generic;<br>
using System.ComponentModel;<br>
using System.Data;<br>
using System.Drawing;<br>
using System.Linq;<br>
using System.Text;<br>
using System.Threading.Tasks;<br>
using System.Windows.Forms;<br>
namespace n2<br>
{<br>
    public partial class Form1 : Form<br>
    {<br>
        public Form1()<br>
        {<br>
            InitializeComponent();<br>
        }<br>
        private void button1_Click(object sender, EventArgs e)<br>
        {<br>
            label1.Text = NumToWord(long.Parse(textBox1.Text));<br>
        }<br>
        public string NumToWord(long number)<br>
        {<br>
            string word = "";<br>
            if (number == 0)<br>
            {<br>
                return "Zero";<br>
            }<br>
            if (number < 0)<br>
            {<br>
                return "minus" + Math.Abs(number);<br>
            }<br>
            if (number / 10000000 > 0)<br>
            {<br>
                word += NumToWord(number / 10000000) + "Corner";<br>
                number %= 10000000;<br>
            }<br>
            if (number / 100000 > 0)<br>
            {<br>
                word += NumToWord(number / 100000) + "Lacs";<br>
                number %= 100000;<br>
            }<br>
            if (number / 1000 > 0)<br>
            {<br>
                word += NumToWord(number / 1000) + "Thousand";<br>
                number %= 1000;<br>
            }<br>
            if (number / 100 > 0)<br>
            {<br>
                word += NumToWord(number / 100) + "Hundred";<br>
                number %= 100;<br>
            }<br>
            if (number > 0)<br>
            {<br>
                string[] units = new string[] { "Zero", "one", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine", "Ten", "eleven", "Twelve", "Thirteen", "Fouteen", "Fifteen", "Sixteen", "Seventeen", "Eighteen", "Ninteen" };<br>
                string[] Tens = new string[] { "zero", "Ten", "Twenty", "Fourty", "Fifty", "sixty", "Seventy", "Eighty", "Nighty" };<br>
                if (number < 20)<br>
                {<br>
                    word += units[number];<br>
                }<br>
                else<br>
                {<br>
                    word += Tens[number / 10];<br>
                    if (number % 10 > 0)<br>
                    {<br>
                        word += Tens[number / 10];<br>
                    }<br>
                }<br>
            }<br>
            return word;<br>
        }<br>
    }<br>
}<br>

**output:**<br>
![image](https://user-images.githubusercontent.com/98145574/158753401-a145d739-baf6-4e1a-b912-26d77a9e3c90.png)<br>
![image](https://user-images.githubusercontent.com/98145574/158756262-37a624f1-101b-44b3-8862-b285085f011e.png)<br>

**26.c# program to create Progress bar control.**<br>
using System;<br>
using System.ComponentModel;<br>
using System.Threading;<br>
using System.Windows.Forms;<br>

namespace n4<br>
{<br>
    public partial class Form1 : Form<br>
    {<br>
        public Form1()<br>
        {<br>
            InitializeComponent();<br>
        }<br>

        private void Form1_Load(object sender, EventArgs e)<br>
        {<br>
            backgroundWorker1.WorkerReportsProgress = true;<br>
            backgroundWorker1.RunWorkerAsync();<br>

        }<br>

        private void backgroundWorker1_DoWork(object sender, DoWorkEventArgs e)<br>
        {<br>
            for(int i=0;i<=100;i++)<br>
            {<br>
                Thread.Sleep(50);<br>
                backgroundWorker1.ReportProgress(i);<br>

            }<br>

        }<br>
        private void backgroundWorker1_ProgressChanged(object sender, ProgressChangedEventArgs e)<br>
        {<br>
            progressBar2.Value = e.ProgressPercentage;<br>
            this.Text = "Progress:" + e.ProgressPercentage.ToString() + "%";<br>
        }<br>
    }<br>
}<br>
**Output:**<br>
![image](https://user-images.githubusercontent.com/98145574/158941946-7597ba3e-0138-4b32-8388-f2727ad43af5.png)<br>

**27.C# program to perform reversal,Padding and Trimming operations on string.**<br>
using System;<br>
using System.Windows.Forms;<br>
namespace n1<br>
{<br>
    public partial class Form1 : Form<br>
    {<br>
        public Form1()<br>
        {<br>
            InitializeComponent();<br>
        }<br>
        private void button1_Click(object sender, EventArgs e)<br>
        {<br>
            string inputString, revstr = "";<br>
            int Length;<br>
            inputString = textBox1.Text;<br>
            Length = inputString.Length - 1;<br>
            while (Length >= 0)<br>
            {<br>
                revstr = revstr + inputString[Length];<br>
                Length--;<br>
            }<br>
            MessageBox.Show("Reverse String is:" + revstr, "Result");<br>
        }<br>
        private void button2_Click(object sender, EventArgs e)<br>
        {<br>
            string inputString;<br>
            inputString = textBox1.Text;<br>
            MessageBox.Show("The string after trimming:" + inputString.Trim(), "Result");<br>
        }<br>
        private void button3_Click(object sender, EventArgs e)<br>
        {<br>
            string inputString;<br>
            inputString = textBox1.Text;<br>
            inputString = inputString.PadLeft(10, '*');<br>
            inputString = inputString.PadRight(15, '*');<br>
            MessageBox.Show("String After Padding:" + inputString, "Result");<br>
        }<br>
    }<br>
  }<br>
  
 ** output:**<br>
 ![image](https://user-images.githubusercontent.com/98145574/158944778-ff3f7560-96b8-4ff6-8e43-76ec049b8c07.png)<br>






