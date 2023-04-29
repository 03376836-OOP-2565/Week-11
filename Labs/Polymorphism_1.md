# Polymorphism

# Method Overloading

```cs
namespace PolymorphismExample
{
    public static class Calaulator
    {
        public static int AddValues(int a, int b) { return a + b; }
        public static int AddValues(int a, int b, int c) { return a + b + c; }
        public static double AddValues(int a, double b) { return a + b; }
        public static double AddValues(int a, float b) { return a + b; }
        public static double AddValues(double a, double b) { return a + b; }

    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Calaulator.AddValues(7, 8d));
            Console.WriteLine(Calaulator.AddValues(1, 2));
            Console.WriteLine(Calaulator.AddValues(1, 2, 3));
            Console.WriteLine(Calaulator.AddValues(5f, 6f));
            Console.WriteLine(Calaulator.AddValues(9f, 4));
        }
    }
}
```
## คำถาม
1. โปรแกรมด้านบนสามารถทำงานได้ทุกบรรทัดหรือไม่
2. จงระบุว่าคำสั่งใดใน Main() เรียก method ใดในคลาส Calculator 
---

## Runtime polymorphism (virtual-override)

```cs
namespace PolymorphismExample
{
    class Animal
    { 
        public int Id { get { return this.GetHashCode(); } }
        public virtual void Move()
        {
            Console.WriteLine("I'm an animal but don't know  exactly how to move.");
        }
        public Animal()
        {
            Console.WriteLine($"Type = {this.GetType().Name}, ID: {Id}");
        }
    }
    class Dog : Animal 
    {
        public override void Move()
        {
            Console.WriteLine("I'm a dog, I move by running on the ground.");
        }
    }
    class Fish: Animal
    {
        public override void Move()
        {
            Console.WriteLine("I'm a fish, I move by swimming in the water.");
        }
    }
    class Bird : Animal
    {
        public override void Move()
        {
            Console.WriteLine("I'm a bird, I move by flying in the sky.");
        }
    }

    internal class Program
    {
        static void Main()
        {
            var a = new Animal();
            a.Move();
            Dog d = new Dog();
            d.Move();
            Bird b = new Bird();
            b.Move();
            Fish f = new Fish();
            f.Move();
            Dog d2 = new Dog();
            d2.Move();
        }
    }
}
```

# Seal - ป้องกันการสืบทอด virtual (ห้าม override) 


```cs
namespace PolymorphismExample
{
    class Animal
    { 
        public int Id { get { return this.GetHashCode(); } }
        public virtual void Move()
        {
            Console.WriteLine("I'm an animal but don't know  exactly how to move.");
        }
        public Animal()
        {
            Console.WriteLine($"Type = {this.GetType().Name}, ID: {Id}");
        }
    }
    class Dog : Animal 
    {
        public override void Move()
        {
            Console.WriteLine("I'm a dog, I move by running on the ground.");
        }
    }
    class Bird : Animal
    {
        public override sealed void Move()
        {
            Console.WriteLine("I'm a bird, I move by flying in the sky.");
        }
    }
    class Duck : Bird 
    {
        public override void Move()
        {
            Console.WriteLine("I'm a bird, I move by flying in the sky.");
        }
    }

    internal class Program
    {
        static void Main()
        {
            var a = new Animal();
            a.Move();
            Dog d = new Dog();
            d.Move();
            Bird b = new Bird();
            b.Move();
            Duck donal = new Duck();
            donal.Move();
        }
    }
}
```

