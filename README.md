
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
![image](https://user-images.githubusercontent.com/98145574/150483817-c9a65b1b-f1c5-4c82-b3ec-7983df9c8c39.png)
