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
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a><span data-ttu-id="018bf-103">Создайте определяемые пользователем функции (UDF) в .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="018bf-103">Create user-defined functions (UDF) in .NET for Apache Spark</span></span>

<span data-ttu-id="018bf-104">Из этой статьи вы узнаете, как использовать определяемые пользователем функции (UDF) в .NET для Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="018bf-104">In this article, you learn how to use user-defined functions (UDF) in .NET for Apache Spark.</span></span> <span data-ttu-id="018bf-105">[Определяемые пользователем функции (UDF)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) — это функция Spark, которая позволяет использовать пользовательские функции для расширения встроенных функций системы.</span><span class="sxs-lookup"><span data-stu-id="018bf-105">[UDFs)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) are a Spark feature that allow you to use custom functions to extend the system's built-in functionality.</span></span> <span data-ttu-id="018bf-106">Определяемые пользователем функции преобразуют значения из одной строки в таблице, получая одно соответствующее выходное значение для каждой строки на основе логики, определенной в UDF.</span><span class="sxs-lookup"><span data-stu-id="018bf-106">UDFs transform values from a single row within a table to produce a single corresponding output value per row based on the logic defined in the UDF.</span></span>

## <a name="define-udfs"></a><span data-ttu-id="018bf-107">Указание определяемых пользователем функций</span><span class="sxs-lookup"><span data-stu-id="018bf-107">Define UDFs</span></span>

<span data-ttu-id="018bf-108">Проверьте следующее определение определяемой пользователем функции:</span><span class="sxs-lookup"><span data-stu-id="018bf-108">Review the following UDF definition:</span></span>

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

<span data-ttu-id="018bf-109">Определяемая пользователем функция принимает `string` в качестве входных данных в виде [столбца](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) в [кадре данных](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) и возвращает `string` с присоединением `hello` перед входными данными.</span><span class="sxs-lookup"><span data-stu-id="018bf-109">The UDF takes a `string` as an input in the form of a [Column](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) of a [Dataframe](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) and returns a `string` with `hello` appended in front of the input.</span></span>

<span data-ttu-id="018bf-110">Следующий кадр данных `df` содержит список имен:</span><span class="sxs-lookup"><span data-stu-id="018bf-110">The following DataFrame `df` contains a list of names:</span></span>

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

<span data-ttu-id="018bf-111">Теперь давайте применим определенные выше данные `udf` к кадру данных`df`:</span><span class="sxs-lookup"><span data-stu-id="018bf-111">Now let's apply the above defined `udf` to the DataFrame `df`:</span></span>

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

<span data-ttu-id="018bf-112">Следующий кадр данных `udfResult` является результатом исполнения определяемой пользователем функции:</span><span class="sxs-lookup"><span data-stu-id="018bf-112">The following DataFrame `udfResult` is the result of the UDF:</span></span>

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

<span data-ttu-id="018bf-113">Подробные инструкции по реализации определяемой пользователем функции см. в описании [вспомогательных определяемых пользователем функций](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) и [примерах](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) на GitHub.</span><span class="sxs-lookup"><span data-stu-id="018bf-113">To better understand how to implement UDFs, review the [UDF helper functions](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) and [examples](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) on GitHub.</span></span>

## <a name="udf-serialization"></a><span data-ttu-id="018bf-114">Сериализация определяемых пользователем функций</span><span class="sxs-lookup"><span data-stu-id="018bf-114">UDF serialization</span></span>

<span data-ttu-id="018bf-115">Поскольку определяемые пользователем функции представляют собой функции, которые должны выполняться в рабочих ролях, их необходимо сериализовать и отправить рабочим ролям как часть полезных данных из драйвера.</span><span class="sxs-lookup"><span data-stu-id="018bf-115">Because UDFs are functions that need to be executed on workers, they have to be serialized and sent to the workers as part of the payload from the driver.</span></span> <span data-ttu-id="018bf-116">[Делегат](../../csharp/programming-guide/delegates/index.md), который является ссылкой на метод, должен быть сериализован, как и его [целевой объект](xref:System.Delegate.Target%2A), который является экземпляром класса, где текущий делегат вызывает метод экземпляра.</span><span class="sxs-lookup"><span data-stu-id="018bf-116">The [delegate](../../csharp/programming-guide/delegates/index.md), which is a reference to the method, needs to be serialized as well as its [target](xref:System.Delegate.Target%2A), which is the class instance on which the current delegate invokes the instance method.</span></span> <span data-ttu-id="018bf-117">Ознакомьтесь с этим [примером кода на сайте GitHub](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149), чтобы получить более полное представление о том, как выполняется сериализация определяемой пользователем функции.</span><span class="sxs-lookup"><span data-stu-id="018bf-117">Review this [code example in GitHub](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) to get a better understanding of how UDF serialization is being done.</span></span>

<span data-ttu-id="018bf-118">.NET для Apache Spark использует .NET Core, где сериализация делегатов не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="018bf-118">.NET for Apache Spark uses .NET Core, which doesn't support serializing delegates.</span></span> <span data-ttu-id="018bf-119">Вместо этого для сериализации целевого объекта, в котором определен делегат, используется отражение.</span><span class="sxs-lookup"><span data-stu-id="018bf-119">Instead, reflection is used to serialize the target where the delegate is defined.</span></span> <span data-ttu-id="018bf-120">Если в общей области определено несколько делегатов, они имеют общее замыкание, которое становится целевым объектом отражения для сериализации.</span><span class="sxs-lookup"><span data-stu-id="018bf-120">When multiple delegates are defined in a common scope, they have a shared closure that becomes the target of reflection for serialization.</span></span>

### <a name="serialization-example"></a><span data-ttu-id="018bf-121">Пример сериализации</span><span class="sxs-lookup"><span data-stu-id="018bf-121">Serialization example</span></span>

<span data-ttu-id="018bf-122">В следующем фрагменте кода определяются две строковые переменные, на которые существуют ссылки в двух делегатах функции, возвращающих соответствующие строки:</span><span class="sxs-lookup"><span data-stu-id="018bf-122">The following code snippet defines two string variables that are being referenced in two function delegates that return the respective strings as a result:</span></span>

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

<span data-ttu-id="018bf-123">Приведенный выше код C# создает следующий код дизассемблирования C# (источник данных: [sharplab.io](https://sharplab.io)) из компилятора:</span><span class="sxs-lookup"><span data-stu-id="018bf-123">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

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

<span data-ttu-id="018bf-124">Как `func`, так и `func2` используют одно и то же замыкание `<>c__DisplayClass0_0`, которое представляет собой целевой объект, сериализуемые в процессе сериализации делегатов `func` и `func2`.</span><span class="sxs-lookup"><span data-stu-id="018bf-124">Both `func` and `func2` share the same closure `<>c__DisplayClass0_0`, which is the target that is serialized when serializing the delegates `func` and `func2`.</span></span> <span data-ttu-id="018bf-125">Хотя `Func<string, string> a` ссылается только на `s1`, `s2` также сериализуется при отправке байтов рабочим ролям.</span><span class="sxs-lookup"><span data-stu-id="018bf-125">Even though `Func<string, string> a` is only referencing `s1`, `s2` is also serialized when the bytes are sent to the workers.</span></span>

<span data-ttu-id="018bf-126">Это может привести к непредвиденному поведению во время выполнения (например, в случае использования [широковещательных переменных](broadcast-guide.md)), поэтому рекомендуется ограничить видимость переменных, используемых в функции, областью действия этой функции.</span><span class="sxs-lookup"><span data-stu-id="018bf-126">This can lead to some unexpected behaviors at runtime (like in the case of using [broadcast variables](broadcast-guide.md)), which is why we recommend that you restrict the visibility of the variables used in a function to that function's scope.</span></span>

<span data-ttu-id="018bf-127">Следующий фрагмент кода представляет собой рекомендуемый способ реализации поведения, требуемого при сериализации:</span><span class="sxs-lookup"><span data-stu-id="018bf-127">The following code snippet is the recommended way to implement the desired serialization behavior:</span></span>

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

<span data-ttu-id="018bf-128">Приведенный выше код C# создает следующий код дизассемблирования C# (источник данных: [sharplab.io](https://sharplab.io)) из компилятора:</span><span class="sxs-lookup"><span data-stu-id="018bf-128">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

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

<span data-ttu-id="018bf-129">Обратите внимание, что `func` и `func2` больше не используют общее замыкание, а вместо этого используют собственные замыкания — `<>c__DisplayClass0_0` и `<>c__DisplayClass0_1`, соответственно.</span><span class="sxs-lookup"><span data-stu-id="018bf-129">Notice that `func` and `func2` no longer share a closure, and they have their own separate closures `<>c__DisplayClass0_0` and `<>c__DisplayClass0_1` respectively.</span></span> <span data-ttu-id="018bf-130">При использовании в качестве целевого объекта для сериализации для делегата сериализуются только переменные, на которые существуют ссылки.</span><span class="sxs-lookup"><span data-stu-id="018bf-130">When used as the target for serialization, nothing other than the referenced variables will get serialized for the delegate.</span></span> <span data-ttu-id="018bf-131">Об этом важно помнить при реализации нескольких определяемых пользователем функций в общей области.</span><span class="sxs-lookup"><span data-stu-id="018bf-131">This behavior is important to keep in mind while implementing multiple UDFs in a common scope.</span></span>

## <a name="some-spark-udf-caveats"></a><span data-ttu-id="018bf-132">Меры предосторожности при использовании определяемых пользователем функций в Spark</span><span class="sxs-lookup"><span data-stu-id="018bf-132">Some Spark UDF caveats</span></span>

* <span data-ttu-id="018bf-133">Значения NULL в определяемых пользователем функциях могут вызывать исключения.</span><span class="sxs-lookup"><span data-stu-id="018bf-133">Null values in UDFs can throw exceptions.</span></span> <span data-ttu-id="018bf-134">За их обработку отвечает разработчик.</span><span class="sxs-lookup"><span data-stu-id="018bf-134">It's the responsibility of the developer to handle them.</span></span>
* <span data-ttu-id="018bf-135">Функции UDF не используют оптимизации, предоставляемые встроенными функциями Spark, поэтому рекомендуется по возможности использовать встроенные функции.</span><span class="sxs-lookup"><span data-stu-id="018bf-135">UDFs don't leverage the optimizations provided by Spark's built-in functions, so it's recommended to use built-in functions where possible.</span></span>

## <a name="faqs"></a><span data-ttu-id="018bf-136">Частые вопросы</span><span class="sxs-lookup"><span data-stu-id="018bf-136">FAQs</span></span>

<span data-ttu-id="018bf-137">**Почему возникает ошибка `System.NotImplementedException: The method or operation is not implemented.` или `System.InvalidCastException: Unable to cast object of type 'System.Collections.Hashtable' to type 'System.Collections.Generic.IDictionary` при попытке вызвать определяемую пользователем функцию с использованием типа `ArrayType`, `MapType`, `ArrayList` или `HashTable` в качестве аргумента или типа возвращаемого значения?**</span><span class="sxs-lookup"><span data-stu-id="018bf-137">**Why do I get the error `System.NotImplementedException: The method or operation is not implemented.` or `System.InvalidCastException: Unable to cast object of type 'System.Collections.Hashtable' to type 'System.Collections.Generic.IDictionary` when trying to call a UDF with `ArrayType`, `MapType`, `ArrayList`, or `HashTable` as argument or return type?**</span></span>  
<span data-ttu-id="018bf-138">`ArrayType` и `MapType` поддерживаются только в [версии 1.0 и более поздних](https://github.com/dotnet/spark/releases/tag/v1.0.0), поэтому в .NET для Apache Spark при попытке передать эти типы в определяемую пользователем функцию в качестве аргументов или в качестве типа возвращаемого значения возникает эта ошибка.</span><span class="sxs-lookup"><span data-stu-id="018bf-138">Support for `ArrayType` and `MapType` is not provided until [v1.0](https://github.com/dotnet/spark/releases/tag/v1.0.0), and so you would get this error if using a .NET for Apache Spark version prior to that, and trying to pass these types either as arguments to the UDF or as a return type.</span></span>
<span data-ttu-id="018bf-139">Типы `ArrayList` и `HashTable` не поддерживаются в качестве типов возвращаемых значений для определяемой пользователем функции, поскольку они не являются универсальными коллекциями и, соответственно, в Spark нельзя передать определения типов их элементов.</span><span class="sxs-lookup"><span data-stu-id="018bf-139">`ArrayList` and `HashTable` types cannot be supported as return types of a UDF as they are non-generic collections and hence their element type definitions cannot be provided to Spark.</span></span>

## <a name="next-steps"></a><span data-ttu-id="018bf-140">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="018bf-140">Next steps</span></span>

* [<span data-ttu-id="018bf-141">Начало работы с .NET для Apache Spark</span><span class="sxs-lookup"><span data-stu-id="018bf-141">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="018bf-142">Отладка приложения .NET для Apache Spark в Windows</span><span class="sxs-lookup"><span data-stu-id="018bf-142">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
