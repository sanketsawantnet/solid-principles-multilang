Interface Segregation Principle (ISP)

📌 * Definition (Simple Words):
👉 Clients (classes that use an interface) should not be forced to depend on methods they don’t need.

Think of it like a restaurant menu 🍽️ — if you just want coffee, you shouldn’t be forced to order full breakfast.

🚫 * Bad Example
Problem in real life:

Imagine we have one big IMachine interface that says:

Print

Scan

Fax

Now, what if a basic printer only supports printing? It still has to implement Scan() and Fax() methods, even if they don’t make sense.

C# Example (Bad)
```csharp
public interface IMachine {
    void Print();
    void Scan();
    void Fax();
}

public class BasicPrinter : IMachine {
    public void Print() { Console.WriteLine("Printing..."); }
    public void Scan() { throw new NotImplementedException(); }
    public void Fax() { throw new NotImplementedException(); }
}
```

🔴# Problem: BasicPrinter is forced to implement methods (Scan, Fax) it doesn’t support. This violates ISP.

✅# Good Example
Fix in real life:

Instead of one bloated menu, create separate small menus (interfaces).

C# Example (Good)
```csharp
public interface IPrinter {
    void Print();
}

public interface IScanner {
    void Scan();
}

public class BasicPrinter : IPrinter {
    public void Print() { Console.WriteLine("Printing..."); }
}

public class MultiFunctionPrinter : IPrinter, IScanner {
    public void Print() { Console.WriteLine("Printing..."); }
    public void Scan() { Console.WriteLine("Scanning..."); }
}
```

🟢 Solution:

BasicPrinter implements only what it needs.

MultiFunctionPrinter can use multiple small interfaces.

📂 Full Examples in Multiple Languages

CSharp Code

Python Code

Java Code

PHP Code

🧠 Key Takeaways

Big fat interfaces = ❌

Small focused interfaces = ✅

ISP keeps systems flexible, reusable, and maintainable.
