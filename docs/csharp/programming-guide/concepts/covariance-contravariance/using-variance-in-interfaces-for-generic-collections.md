---
title: Использование вариативности в интерфейсах для универсальных коллекций (C#)
description: Узнайте, как использовать ковариантные и контрвариантные интерфейсы для универсальных коллекций. См. примеры преобразования и сравнения универсальных коллекций.
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: 39da866be3d1ead357485be31fee1c19f2b1ae27
ms.sourcegitcommit: 985c603cb21a085f8a8105f34ff5b87a44b76ab4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107564861"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a>Использование вариативности в интерфейсах для универсальных коллекций (C#)

Ковариантный интерфейс позволяет его методам возвращать более производные типы, чем указанные в интерфейсе. Контравариантный интерфейс позволяет его методам принимать параметры менее производных типов, чем указанные в интерфейсе.  
  
 В .NET Framework 4 несколько имеющихся интерфейсов стали ковариантными и контравариантными. В их числе <xref:System.Collections.Generic.IEnumerable%601> и <xref:System.IComparable%601>. Это позволяет повторно использовать методы, оперирующие универсальными коллекциями базовых типов, для коллекций производных типов.  
  
 Список вариативных интерфейсов в .NET см. в статье [Вариативность в универсальных интерфейсах (C#)](./variance-in-generic-interfaces.md).  
  
## <a name="converting-generic-collections"></a>Преобразование универсальных коллекций  

 Следующий пример иллюстрирует преимущества поддержки ковариантности в интерфейсе <xref:System.Collections.Generic.IEnumerable%601>. Метод `PrintFullName` принимает коллекцию типа `IEnumerable<Person>` в качестве параметра. При этом его можно повторно использовать для коллекции типа `IEnumerable<Employee>`, так как `Employee` наследует `Person`.  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
class Program  
{  
    // The method has a parameter of the IEnumerable<Person> type.  
    public static void PrintFullName(IEnumerable<Person> persons)  
    {  
        foreach (Person person in persons)  
        {  
            Console.WriteLine("Name: {0} {1}",  
            person.FirstName, person.LastName);  
        }  
    }  
  
    public static void Test()  
    {  
        IEnumerable<Employee> employees = new List<Employee>();  
  
        // You can pass IEnumerable<Employee>,
        // although the method expects IEnumerable<Person>.  
  
        PrintFullName(employees);  
  
    }  
}  
```  
  
## <a name="comparing-generic-collections"></a>Сравнение универсальных коллекций  

 Следующий пример иллюстрирует преимущества поддержки контрвариантности в интерфейсе <xref:System.Collections.Generic.IEqualityComparer%601>. Класс `PersonComparer` реализует интерфейс `IEqualityComparer<Person>`. Тем не менее этот класс можно повторно использовать для сравнения последовательности объектов типа `Employee`, так как `Employee` наследует `Person`.  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
// The custom comparer for the Person type  
// with standard implementations of Equals()  
// and GetHashCode() methods.  
class PersonComparer : IEqualityComparer<Person>  
{  
    public bool Equals(Person x, Person y)  
    {
        if (Object.ReferenceEquals(x, y)) return true;  
        if (Object.ReferenceEquals(x, null) ||  
            Object.ReferenceEquals(y, null))  
            return false;
        return x.FirstName == y.FirstName && x.LastName == y.LastName;  
    }  
    public int GetHashCode(Person person)  
    {  
        if (Object.ReferenceEquals(person, null)) return 0;  
        int hashFirstName = person.FirstName == null  
            ? 0 : person.FirstName.GetHashCode();  
        int hashLastName = person.LastName.GetHashCode();  
        return hashFirstName ^ hashLastName;  
    }  
}  
  
class Program  
{  
  
    public static void Test()  
    {  
        List<Employee> employees = new List<Employee> {  
               new Employee() {FirstName = "Michael", LastName = "Alexander"},  
               new Employee() {FirstName = "Jeff", LastName = "Price"}  
            };  
  
        // You can pass PersonComparer,
        // which implements IEqualityComparer<Person>,  
        // although the method expects IEqualityComparer<Employee>.  
  
        IEnumerable<Employee> noduplicates =  
            employees.Distinct<Employee>(new PersonComparer());  
  
        foreach (var employee in noduplicates)  
            Console.WriteLine(employee.FirstName + " " + employee.LastName);  
    }  
}  
```  
  
## <a name="see-also"></a>См. также

- [Вариативность в универсальных интерфейсах (C#)](./variance-in-generic-interfaces.md)
