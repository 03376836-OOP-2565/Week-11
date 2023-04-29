# Abstract member

```cs
namespace PolymorphismExample
{
    abstract class Animal
    { 
        public int Id { get { return this.GetHashCode(); } }
        abstract public void Move();
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
        }
    }
}
```




