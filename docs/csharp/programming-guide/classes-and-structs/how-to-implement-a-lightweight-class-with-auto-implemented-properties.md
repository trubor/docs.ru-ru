---
title: Практическое руководство. Реализация облегченного класса с автоматически реализуемыми свойствами (руководство по программированию на C#)
description: Узнайте, как создать неизменяемый упрощенный класс в C#, который инкапсулирует автоматически реализуемые свойства. Существует два подхода к реализации.
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 1d80cb2391a94c21360117c8217ecc4514fd666e
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190272"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a>Практическое руководство. Реализация облегченного класса с автоматически реализуемыми свойствами (руководство по программированию на C#)

В этом примере показано, как создать неизменяемый упрощенный класс, служащий исключительно для инкапсуляции набора автоматически реализуемых свойств. Используйте такую конструкцию вместо структуры, когда требуется использовать семантику ссылочного типа.

Неизменяемое свойство можно создать следующими способами:

- Объявить только метод доступа [get](../../language-reference/keywords/get.md), который делает свойство неизменяемым везде, кроме конструктора типа.

- Объявить метод доступа [init](../../language-reference/keywords/init.md) вместо `set`, который делает свойство изменяемым только в конструкторе или с помощью [инициализатора объектов](object-and-collection-initializers.md).

- Объявить метод доступа [set](../../language-reference/keywords/set.md) как [private](../../language-reference/keywords/private.md).  Свойство можно задать в типе, но оно является неизменяемым для потребителей.

  При объявлении закрытого метода доступа `set` для инициализации свойства нельзя использовать инициализатор объекта. Необходимо использовать конструктор или фабричный метод.

В следующем примере показано, как свойство с методом доступа get, отличается от свойства с методами доступа get и private set.

```csharp
class Contact
{
    public string Name { get; }
    public string Address { get; private set; }

    public Contact(string contactName, string contactAddress)
    {
        // Both properties are accessible in the constructor.
        Name = contactName;
        Address = contactAddress;
    }

    // Name isn't assignable here. This will generate a compile error.
    //public void ChangeName(string newName) => Name = newName;

    // Address is assignable here.
    public void ChangeAddress(string newAddress) => Address = newAddress
}
```

## <a name="example"></a>Пример

В следующем примере показаны два способа реализации неизменяемого класса с автоматически реализуемыми свойствами. Каждый способ объявляет одно из свойств с закрытым методом доступа `set` и одно из свойств только с методом доступа `get`.  Первый класс использует конструктор только для инициализации свойства, а второй класс использует статический фабричный метод, вызывающий конструктор.

```csharp
// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// constructor to initialize its properties.
class Contact
{
    // Read-only property.
    public string Name { get; }

    // Read-write property with a private set accessor.
    public string Address { get; private set; }

    // Public constructor.
    public Contact(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }
}

// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// static method and private constructor to initialize its properties.
public class Contact2
{
    // Read-write property with a private set accessor.
    public string Name { get; private set; }

    // Read-only property.
    public string Address { get; }

    // Private constructor.
    private Contact2(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }

    // Public factory method.
    public static Contact2 CreateContact(string name, string address)
    {
        return new Contact2(name, address);
    }
}

public class Program
{
    static void Main()
    {
        // Some simple data sources.
        string[] names = {"Terry Adams","Fadi Fakhouri", "Hanying Feng",
                            "Cesar Garcia", "Debra Garcia"};
        string[] addresses = {"123 Main St.", "345 Cypress Ave.", "678 1st Ave",
                                "12 108th St.", "89 E. 42nd St."};

        // Simple query to demonstrate object creation in select clause.
        // Create Contact objects by using a constructor.
        var query1 = from i in Enumerable.Range(0, 5)
                    select new Contact(names[i], addresses[i]);

        // List elements cannot be modified by client code.
        var list = query1.ToList();
        foreach (var contact in list)
        {
            Console.WriteLine("{0}, {1}", contact.Name, contact.Address);
        }

        // Create Contact2 objects by using a static factory method.
        var query2 = from i in Enumerable.Range(0, 5)
                        select Contact2.CreateContact(names[i], addresses[i]);

        // Console output is identical to query1.
        var list2 = query2.ToList();

        // List elements cannot be modified by client code.
        // CS0272:
        // list2[0].Name = "Eugene Zabokritski";

        // Keep the console open in debug mode.
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}

/* Output:
    Terry Adams, 123 Main St.
    Fadi Fakhouri, 345 Cypress Ave.
    Hanying Feng, 678 1st Ave
    Cesar Garcia, 12 108th St.
    Debra Garcia, 89 E. 42nd St.
*/
```

Компилятор создает резервные поля для каждого автоматически реализуемого свойства. Эти поля недоступны непосредственно из исходного кода.

## <a name="see-also"></a>См. также

- [Свойства](./properties.md)
- [struct](../../language-reference/builtin-types/struct.md)
- [Инициализаторы объектов и коллекций](./object-and-collection-initializers.md)
