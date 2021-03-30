---
title: Создайте определяемые пользователем функции (UDF) в .NET для Apache Spark
description: Узнайте, как реализовать определяемые пользователем функции (UDF) в .NET для приложений Apache Spark.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 13898bdbd9522730c8f0cd19bd13d4e6f3a6a10e
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874073"
---
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a>Создайте определяемые пользователем функции (UDF) в .NET для Apache Spark

Из этой статьи вы узнаете, как использовать определяемые пользователем функции (UDF) в .NET для Apache Spark. [Определяемые пользователем функции (UDF)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) — это функция Spark, которая позволяет использовать пользовательские функции для расширения встроенных функций системы. Определяемые пользователем функции преобразуют значения из одной строки в таблице, получая одно соответствующее выходное значение для каждой строки на основе логики, определенной в UDF.

## <a name="define-udfs"></a>Указание определяемых пользователем функций

Проверьте следующее определение определяемой пользователем функции:

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

Определяемая пользователем функция принимает `string` в качестве входных данных в виде [столбца](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) в [кадре данных](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) и возвращает `string` с присоединением `hello` перед входными данными.

Следующий кадр данных `df` содержит список имен:

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

Теперь давайте применим определенные выше данные `udf` к кадру данных`df`:

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

Следующий кадр данных `udfResult` является результатом исполнения определяемой пользователем функции:

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

Подробные инструкции по реализации определяемой пользователем функции см. в описании [вспомогательных определяемых пользователем функций](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) и [примерах](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) на GitHub.

## <a name="udf-serialization"></a>Сериализация определяемых пользователем функций

Поскольку определяемые пользователем функции представляют собой функции, которые должны выполняться в рабочих ролях, их необходимо сериализовать и отправить рабочим ролям как часть полезных данных из драйвера. [Делегат](../../csharp/programming-guide/delegates/index.md), который является ссылкой на метод, должен быть сериализован, как и его [целевой объект](xref:System.Delegate.Target%2A), который является экземпляром класса, где текущий делегат вызывает метод экземпляра. Ознакомьтесь с этим [примером кода на сайте GitHub](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149), чтобы получить более полное представление о том, как выполняется сериализация определяемой пользователем функции.

.NET для Apache Spark использует .NET Core, где сериализация делегатов не поддерживается. Вместо этого для сериализации целевого объекта, в котором определен делегат, используется отражение. Если в общей области определено несколько делегатов, они имеют общее замыкание, которое становится целевым объектом отражения для сериализации.

### <a name="serialization-example"></a>Пример сериализации

В следующем фрагменте кода определяются две строковые переменные, на которые существуют ссылки в двух делегатах функции, возвращающих соответствующие строки:

```csharp
using System;

public class C {
    public void M() {
        string s1 = "s1";
        string s2 = "s2";
        Func<string, string> a = str => s1;
        Func<string, string> b = str => s2;
    }
}
```

Приведенный выше код C# создает следующий код дизассемблирования C# (источник данных: [sharplab.io](https://sharplab.io)) из компилятора:

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        public string s2;

        internal string <M>b__0(string str)
        {
            return s1;
        }

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        <>c__DisplayClass0_.s2 = "s2";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_.<M>b__1);
    }
}
```

Как `func`, так и `func2` используют одно и то же замыкание `<>c__DisplayClass0_0`, которое представляет собой целевой объект, сериализуемые в процессе сериализации делегатов `func` и `func2`. Хотя `Func<string, string> a` ссылается только на `s1`, `s2` также сериализуется при отправке байтов рабочим ролям.

Это может привести к непредвиденному поведению во время выполнения (например, в случае использования [широковещательных переменных](broadcast-guide.md)), поэтому рекомендуется ограничить видимость переменных, используемых в функции, областью действия этой функции.

Следующий фрагмент кода представляет собой рекомендуемый способ реализации поведения, требуемого при сериализации:

```csharp
using System;

public class C {
    public void M() {
        {
            string s1 = "s1";
            Func<string, string> a = str => s1;
        }
        {
            string s2 = "s2";
            Func<string, string> b = str => s2;
        }
    }
}
```

Приведенный выше код C# создает следующий код дизассемблирования C# (источник данных: [sharplab.io](https://sharplab.io)) из компилятора:

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        internal string <M>b__0(string str)
        {
            return s1;
        }
    }

    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_1
    {
        public string s2;

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        <>c__DisplayClass0_1 <>c__DisplayClass0_2 = new <>c__DisplayClass0_1();
        <>c__DisplayClass0_2.s2 = "s2";
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_2.<M>b__1);
    }
}
```

Обратите внимание, что `func` и `func2` больше не используют общее замыкание, а вместо этого используют собственные замыкания — `<>c__DisplayClass0_0` и `<>c__DisplayClass0_1`, соответственно. При использовании в качестве целевого объекта для сериализации для делегата сериализуются только переменные, на которые существуют ссылки. Об этом важно помнить при реализации нескольких определяемых пользователем функций в общей области.

## <a name="some-spark-udf-caveats"></a>Меры предосторожности при использовании определяемых пользователем функций в Spark

* Значения NULL в определяемых пользователем функциях могут вызывать исключения. За их обработку отвечает разработчик.
* Функции UDF не используют оптимизации, предоставляемые встроенными функциями Spark, поэтому рекомендуется по возможности использовать встроенные функции.

## <a name="faqs"></a>Частые вопросы

**Почему возникает ошибка `System.NotImplementedException: The method or operation is not implemented.` или `System.InvalidCastException: Unable to cast object of type 'System.Collections.Hashtable' to type 'System.Collections.Generic.IDictionary` при попытке вызвать определяемую пользователем функцию с использованием типа `ArrayType`, `MapType`, `ArrayList` или `HashTable` в качестве аргумента или типа возвращаемого значения?**  
`ArrayType` и `MapType` поддерживаются только в [версии 1.0 и более поздних](https://github.com/dotnet/spark/releases/tag/v1.0.0), поэтому в .NET для Apache Spark при попытке передать эти типы в определяемую пользователем функцию в качестве аргументов или в качестве типа возвращаемого значения возникает эта ошибка.
Типы `ArrayList` и `HashTable` не поддерживаются в качестве типов возвращаемых значений для определяемой пользователем функции, поскольку они не являются универсальными коллекциями и, соответственно, в Spark нельзя передать определения типов их элементов.

## <a name="next-steps"></a>Следующие шаги

* [Начало работы с .NET для Apache Spark](../tutorials/get-started.md)
* [Отладка приложения .NET для Apache Spark в Windows](debug.md)
