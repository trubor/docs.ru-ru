---
title: Руководство по программированию на C#. Использование типа dynamic
description: Сведения об использовании типа dynamic. Тип dynamic является статическим, но динамические объекты обходят статическую проверку типов.
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: 68e22f9d25b29784f73fefdf80808f9c2ba5e0f1
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478646"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Использование типа dynamic (руководство по программированию на C#)

C# 4 добавляет новый тип `dynamic`. Этот тип является статическим, но объект типа `dynamic` обходит проверку статического типа. В большинстве случаев он работает как тип `object`. Во время компиляции предполагается, что элемент, типизированный как `dynamic`, поддерживает любые операции. Это значит, что вам не придется задумываться о том, получает ли объект значение из API COM, из динамического языка, такого как IronPython, из модели DOM HTML, из отражения или из другой части программы. При этом если код недопустимый, ошибки перехватываются во время выполнения.

Например, если метод экземпляра `exampleMethod1` в следующем коде имеет только один параметр, компилятор определяет, что первый вызов метода `ec.exampleMethod1(10, 4)` недопустим, поскольку содержит два аргумента. Этот вызов приводит к ошибке компилятора. Второй вызов метода `dynamic_ec.exampleMethod1(10, 4)` компилятором не проверяется, поскольку `dynamic_ec` имеет тип `dynamic`. В результате ошибка компилятора не возникает. Тем не менее ошибка не может оставаться незамеченной неограниченное время. Она перехватывается во время выполнения и вызывает исключение времени выполнения.

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

Роль компилятора в этих примерах заключается в том, чтобы объединить информацию о том, какие действия каждый оператор будет выполнять с объектом или выражением, типизированным как `dynamic`. Во время выполнения сохраненная информация проверяется, а все недействительные операторы вызывают исключение времени выполнения.

Результатом большинства динамических операций является сам `dynamic`. Например, при наведении указателя мыши на `testSum` в следующем примере IntelliSense отображает тип **(локальная переменная) dynamic testSum**.

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

Операции, в которых результатом не является `dynamic`:

* Преобразования из `dynamic` в другой тип.
* Вызовы конструктора, которые включают аргументы типа `dynamic`.

Например, `testInstance` в следующих объявлениях имеет тип `ExampleClass`, а не `dynamic`:

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

Примеры преобразований приводятся в следующем разделе — "Преобразования".

## <a name="conversions"></a>Преобразования

Преобразования динамических объектов в другие типы выполнять очень просто. Это позволяет разработчику переключаться между динамическим и нединамическим поведением.

Любой объект можно преобразовать в динамический тип неявно, как показано в следующих примерах.

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

И наоборот, явное преобразование можно динамически применить к любому выражению типа `dynamic`.

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Разрешение перегрузки с аргументами типа dynamic

Разрешение перегрузки возникают во время выполнения, а не компиляции, если один или несколько аргументов в вызове метода имеют тип `dynamic` либо получатель вызова метода имеет тип `dynamic`. В следующем примере, если единственный доступный метод `exampleMethod2` определен как принимающий аргумент строки, отправка `d1` как аргумента не вызывает ошибку компилятора, но создает исключение времени выполнения. Разрешение перегрузки завершается ошибкой во время выполнения, поскольку `d1` имеет тип времени выполнения `int`, а `exampleMethod2` требуется строка.

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a>Среда DLR

Среда DLR (Dynamic Language Runtime) — это новый API в .NET Framework 4. Она предоставляет инфраструктуру, которая поддерживает тип `dynamic` в C#, а также реализацию динамических языков программирования, таких как IronPython и IronRuby. Дополнительные сведения о DLR см. в разделе [Общие сведения о среде DLR](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).

## <a name="com-interop"></a>взаимодействие COM

C# 4 включает несколько функций, улучшающих взаимодействие с интерфейсами API COM, такими как API автоматизации Office. К таким усовершенствованиям относятся применение типа `dynamic` и [ именованных и необязательных аргументов](../classes-and-structs/named-and-optional-arguments.md).

Многие методы COM допускают вариативность в типах аргументов и возвращают тип, назначая типы как `object`. В связи с этим для согласования со строго типизированными переменными в C# необходимо явно приводить значения. При компиляции с использованием параметра [**EmbedInteropTypes** (параметры компилятора C#)](../../language-reference/compiler-options/inputs.md#embedinteroptypes) введение типа `dynamic` позволяет обрабатывать вхождения `object` в сигнатурах COM, как если бы они имели тип `dynamic`, и таким образом избежать большей части приведения. Например, следующие инструкции показывают, как получить доступ к ячейке в электронной таблице Microsoft Office Excel с типом `dynamic` и без типа `dynamic`.

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[dynamic](../../language-reference/builtin-types/reference-types.md)|Описывает применение ключевого слова `dynamic`.|
|[Общие сведения о среде DLR](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Содержит общие сведения о среде DLR — среде выполнения, которая добавляет в общую среду языковой среды исполнения (CLR) набор служб для динамических языков.|
|[Пошаговое руководство: Создание и использование динамических объектов](walkthrough-creating-and-using-dynamic-objects.md)|Содержит пошаговые инструкции по созданию пользовательских динамических объектов и проекта, который обращается к библиотеке `IronPython`.|
|[Практическое руководство. Доступ к объектам взаимодействия Office с помощью функций языка C#](../interop/how-to-access-office-onterop-objects.md)|Содержит сведения о создании проекта с использованием именованных и необязательных аргументов, типа `dynamic` и других усовершенствований, которые упрощают доступ к объектам Office API.|
