# Interview-Question

Shallow Copy
----------------

A shallow copy creates a new object, but it only copies references for reference-type fields instead of duplicating them. This means that if the original object has a reference to another object, both the original and copied objects will point to the same reference.

class Person
{
    public string Name { get; set; }
    public Address Address { get; set; }  // Reference type
}

class Address
{
    public string City { get; set; }
}

class Program
{
    static void Main()
    {
        Person p1 = new Person { Name = "John", Address = new Address { City = "New York" } };

        // Shallow Copy using MemberwiseClone
        Person p2 = (Person)p1.MemberwiseClone();

        p2.Name = "Doe"; // This will not affect p1
        p2.Address.City = "Los Angeles"; // This will affect p1 too!

        Console.WriteLine(p1.Name);  // Output: John (unchanged)
        Console.WriteLine(p1.Address.City); // Output: Los Angeles (changed!)
    }
}
