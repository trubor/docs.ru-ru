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
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="7a1b9-104">Использование вариативности в интерфейсах для универсальных коллекций (C#)</span><span class="sxs-lookup"><span data-stu-id="7a1b9-104">Using Variance in Interfaces for Generic Collections (C#)</span></span>

<span data-ttu-id="7a1b9-105">Ковариантный интерфейс позволяет его методам возвращать более производные типы, чем указанные в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-105">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="7a1b9-106">Контравариантный интерфейс позволяет его методам принимать параметры менее производных типов, чем указанные в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-106">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="7a1b9-107">В .NET Framework 4 несколько имеющихся интерфейсов стали ковариантными и контравариантными.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-107">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="7a1b9-108">В их числе <xref:System.Collections.Generic.IEnumerable%601> и <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-108">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="7a1b9-109">Это позволяет повторно использовать методы, оперирующие универсальными коллекциями базовых типов, для коллекций производных типов.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-109">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="7a1b9-110">Список вариативных интерфейсов в .NET см. в статье [Вариативность в универсальных интерфейсах (C#)](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="7a1b9-110">For a list of variant interfaces in .NET, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="7a1b9-111">Преобразование универсальных коллекций</span><span class="sxs-lookup"><span data-stu-id="7a1b9-111">Converting Generic Collections</span></span>  

 <span data-ttu-id="7a1b9-112">Следующий пример иллюстрирует преимущества поддержки ковариантности в интерфейсе <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-112">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="7a1b9-113">Метод `PrintFullName` принимает коллекцию типа `IEnumerable<Person>` в качестве параметра.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-113">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="7a1b9-114">При этом его можно повторно использовать для коллекции типа `IEnumerable<Employee>`, так как `Employee` наследует `Person`.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-114">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="7a1b9-115">Сравнение универсальных коллекций</span><span class="sxs-lookup"><span data-stu-id="7a1b9-115">Comparing Generic Collections</span></span>  

 <span data-ttu-id="7a1b9-116">Следующий пример иллюстрирует преимущества поддержки контрвариантности в интерфейсе <xref:System.Collections.Generic.IEqualityComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-116">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IEqualityComparer%601> interface.</span></span> <span data-ttu-id="7a1b9-117">Класс `PersonComparer` реализует интерфейс `IEqualityComparer<Person>`.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-117">The `PersonComparer` class implements the `IEqualityComparer<Person>` interface.</span></span> <span data-ttu-id="7a1b9-118">Тем не менее этот класс можно повторно использовать для сравнения последовательности объектов типа `Employee`, так как `Employee` наследует `Person`.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-118">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a1b9-119">См. также</span><span class="sxs-lookup"><span data-stu-id="7a1b9-119">See also</span></span>

- [<span data-ttu-id="7a1b9-120">Вариативность в универсальных интерфейсах (C#)</span><span class="sxs-lookup"><span data-stu-id="7a1b9-120">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
