# Eligibility for Engineering Admission
```cs
using System;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Enter marks obtained in Maths:");
        int mathsMarks = Convert.ToInt32(Console.ReadLine());

        Console.WriteLine("Enter marks obtained in Physics:");
        int physicsMarks = Convert.ToInt32(Console.ReadLine());

        Console.WriteLine("Enter marks obtained in Chemistry:");
        int chemistryMarks = Convert.ToInt32(Console.ReadLine());

        int totalMarks = mathsMarks + physicsMarks + chemistryMarks;

        if (mathsMarks >= 65 && physicsMarks >= 55 && chemistryMarks >= 50 && (totalMarks >= 180 || (mathsMarks + physicsMarks) >= 140))
        {
            Console.WriteLine("Congratulations! You are eligible for admission to the engineering course.");
        }
        else
        {
            Console.WriteLine("You are not eligible for admission to the engineering course.");
        }
    }
}
```

# CSharp Pattern
```cs
using System;
public class Pattern
{
    public static void Main()
    {
        int rows, c = 1, a, i, j, n;
        Console.Write("Enter the no of rows: ");
        rows = Convert.ToInt32(Console.ReadLine());
        for (i = 0; i < rows; i++)
        {
            for (n = 1; n <= rows - i; n++)
            {
                Console.Write(" ");
            }
            for (j = 0; j <= i; j++)
            {
                if (i == 0 || j == 0)
                {
                    c = 1;
                }
                else
                {
                    c = c * (i - j + 1) / j;
                }
                Console.Write("{0} ", c);
            }
            Console.Write("\n");
        }
        Console.ReadLine();
    }
}
```

# Constructor
```cs
using System;

namespace Exp3
{
    public class Employee
    {
        public string name, designation;
        public int bsalary, noofexp, insurance;
        public float hra, ta, grosspay;
        public Employee(string name, string designation, int bsalary, int noofexp, int insurance)
        {
            this.name = name;
            this.designation = designation;
            this.bsalary = bsalary;
            this.noofexp = noofexp;
            this.insurance = insurance;
        }
        public void salary()
        {
            hra = (20 / 100) * bsalary;
            ta = (10 / 100) * bsalary;
            grosspay = bsalary + hra + ta - insurance;
        }
        public void display()
        {
            Console.WriteLine("{0} having {1} yrs of experience, working as {2}", this.name, this.noofexp, this.designation);
            Console.WriteLine("Receives {0} as his/her salary", this.grosspay);
        }
    }
    class Program
    {
        public static void Main(string[] args)
        {
            Employee emp1 = new Employee("Ronick", "ML Engineer", 120000, 5, 20000);
            emp1.salary();
            Employee emp2 = new Employee("Ashwin", "Data Scientist", 90000, 2, 10000);
            emp2.salary();
            emp1.display();
            emp2.display();
            Console.ReadLine();
        }
    }
}
```

# Jagged Array
```cs
using System;
public class Pattern
{
    public static void Main()
    {
      int[][] jaggedArray = new int[4][];
      jaggedArray[0] = new int[3];
      jaggedArray[1] = new int[5];
      jaggedArray[2] = new int[6];
      jaggedArray[3] = new int[4];
      for (int i = 0; i < jaggedArray.Length; i++)
      {
        for (int j = 0; j < jaggedArray[i].Length; j++)
        {
          jaggedArray[i][j] = i * j + 60;
          Console.WriteLine("CPU usage of {0} node is {1}%", i + 1, jaggedArray[i][j]);

        }
      }
    }
}
```

# Operator Overloading
```cs
using System;
namespace OperatorOverloading
{
   class program
   {
       public int p1, p2;
       public program()
       {
           p1 = 10;
           p2 = 15;
       }
       public program(int p3, int p4)
       {
           p1 = p3;
           p2 = p4;
       }
       public static bool operator == (program p1, program p2)
       {
           return p1.Equals(p2);
       }
       public static bool operator != (program p1, program p2)
       {
           return !(p1 == p2);
       }
       public static void Main()
       {
           program o1 = new program();
           program o2 = new program(15,30);
           Console.WriteLine("Object P1: {0} {1}", o1.p1, o1.p2);
           Console.WriteLine("Object P2: {0} {1}", o2.p1, o2.p2);
           if (o1 == o2)
               Console.WriteLine("Objects are equal");
           else if (o1 != o2)
               Console.WriteLine("Objects are not equal");
       }
   }
}
```

# Recursive Function
```cs
using System;

public class reverse
{
    static int RevNum(int n, int rev = 0)
    {
        if (n == 0)
        {
            return rev;
        }
        int digit = n % 10;
        rev = rev * 10 + digit;
        return RevNum(n / 10, rev);
    }

    static void Main(string[] args)
    {
        Console.Write("Enter a number to reverse: ");
        int number = Convert.ToInt32(Console.ReadLine());
        Console.WriteLine("Reversed number: {0}", RevNum(number));
    }
}
```

# Hierarchical Inheritance
```cs
using System;

namespace exp8
{
    public class tyre
    {
        public tyre() {
            Console.WriteLine("Tyre - Vehicle");
        }
        public virtual void display()
        {
            Console.Write("Tyre is attached to ");
        }
    }

    public class car : tyre
    {
        public car() {
            Console.WriteLine("Car Constructor");
        }
        public override void display()
        {
            base.display();
            Console.WriteLine("Car");
        }
    }

    public class scooter : tyre
    {
        public scooter() {
            Console.WriteLine("Scooter Constructor");
        }
        public override void display()
        {
            base.display();
            Console.WriteLine("Scooter");
        }
    }
    public class main
    {
        public static void Main(string[] args)
        {
            car newcar = new car();
            newcar.display();
            Console.WriteLine();
            scooter newscooter = new scooter();
            newscooter.display();
        }
    }
}
```

# Name Hiding with interface inheritance
```cs
using System;

public interface IMario
{
    void Ability();
}

class Mario : IMario
{
    public virtual void Ability()
    {
        Console.WriteLine("Mario's normal ability is Jumping");
    }
}

class SuperMario : Mario
{
    public new void Ability()
    {
        Console.WriteLine("Super Mario's ability is  Flying and shooting fireballs");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Mario mario = new Mario();
        SuperMario superMario = new SuperMario();

        mario.Ability(); 
        superMario.Ability();
    }
}
```

# Interface with abstract methods
```cs
using System;
using System.Transactions;
public interface Bank
{
    void deposit();
    void withdraw();
}
public class Program:Bank
{
    public int amount,balance=5000;
    public Program()
    {
        Console.WriteLine("Enter your Choice:\n1.Deposit\n2.WithDraw");
        int opt;
        opt = Convert.ToInt32(Console.ReadLine());
        if (opt == 1)
            deposit();
        else if (opt == 2)
            withdraw();
        else
        {
            Console.WriteLine("Enter a valid input");
        }
    }
    public void deposit()
    {
        Console.WriteLine("Enter the amount to deposit");
        amount = Convert.ToInt32(Console.ReadLine());
        balance += amount;
        Console.WriteLine("The Balance is " + balance);
    }
    public void withdraw()
    {
        Console.WriteLine("Enter the amount to withdraw");
        amount = Convert.ToInt32(Console.ReadLine());
        balance -= amount;
        Console.WriteLine("The Balance is " + balance);
    }
}
public class Exp9
{
    public static void Main(string[] args)
    {
        Program n = new Program();
    }
}
```

# File Manipulation
```cs
using System;
using System.IO;

struct UserData
{
    public string Name;
    public int Age;
    public string Email;
}

class Program
{
    static void Main(string[] args)

    {
        string filePath = @"C:\Users\SEC\Desktop\exp10.txt";
        UserData[] ud=new UserData[3];
        for(int i=0; i<3;i++)
        {
            Console.WriteLine("Enter your name:");
            ud[i].Name = Console.ReadLine();

            Console.WriteLine("Enter your age:");
            ud[i].Age = int.Parse(Console.ReadLine());

            Console.WriteLine("Enter your email:");
            ud[i].Email = Console.ReadLine();

            WriteUserDataToFile(filePath, ud[i]);
        }  
        Console.WriteLine("User data has been saved to the file.");
    }

    static void WriteUserDataToFile(string filePath, UserData userData)
    {
        //using (FileStream fs = new FileStream(filePath, FileMode.Create))
        using (StreamWriter writer = File.AppendText(filePath))
        {
            
            writer.WriteLine($"Name: {userData.Name}");
            writer.WriteLine($"Age: {userData.Age}");
            writer.WriteLine($"Email: {userData.Email}");
            
        }
    }
}
```
