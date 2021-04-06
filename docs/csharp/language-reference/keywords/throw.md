---
description: Справочник по C#. Оператор throw
title: Справочник по C#. Оператор throw
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: e081bd86e57d69c85ea018d371b3e489145e958d
ms.sourcegitcommit: 872ca41d1c26f39d0aef57cc365d09503bac780d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2021
ms.locfileid: "106288047"
---
# <a name="throw-c-reference"></a>throw (Справочник по C#)

Сообщает о возникновении исключения во время выполнения программы.  
  
## <a name="remarks"></a>Remarks

Синтаксис `throw` выглядит следующим образом:

```csharp
throw [e];
```

где `e` — это экземпляр класса, производного от <xref:System.Exception?displayProperty=nameWithType>. В следующем примере используется оператор `throw` для создания <xref:System.IndexOutOfRangeException>, если аргумент, переданный в метод с именем `GetNumber`, не соответствует допустимому индексу внутреннего массива.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw1/throw-1.cs#1)]

Затем вызывающие объекты метода используют блок `try-catch` или `try-catch-finally` для обработки исключения. В следующем примере показана обработка исключения, созданного методом `GetNumber`.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw1/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a>Повторный вызов исключения

`throw` можно также использовать в блоке `catch` для повторного создания исключения, обрабатываемого в блоке `catch`.  В этом случае оператор `throw` не принимает операнд исключения. Это наиболее полезно, когда метод передает аргумент от вызывающего объекта в другой метод библиотеки, а метод библиотеки создает исключение, которое должно быть передано вызывающему объекту. Например, в следующем примере повторно создается исключение <xref:System.NullReferenceException>, возникающее при попытке получить первый символ неинициализированной строки.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw2/throw-2.cs#3)]

> [!IMPORTANT]
> Можно также использовать синтаксис `throw e` в блоке `catch`, чтобы создать исключение, которое будет передано вызывающему объекту. В этом случае трассировка стека исходного исключения, которое доступно из свойства <xref:System.Exception.StackTrace>, не сохраняется.

## <a name="the-throw-expression"></a>Выражение `throw`

Начиная с C# 7.0 `throw` можно использовать в качестве выражения, а также как оператор. Это позволяет вызывать исключения в контекстах, которые ранее не поддерживались. Сюда входит следующее.

- [Условный оператор](../operators/conditional-operator.md). В следующем примере используется исключение `throw` для создания <xref:System.ArgumentException>, если методу передается массив пустых строк. До выхода C# 7.0 эта логика должна была отображаться в операторе `if`/`else`.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional/conditional.cs#1)]

- [Оператор объединения с NULL](../operators/null-coalescing-operator.md). В следующем примере выражение `throw` используется с оператором, принимающим значение NULL, для создания исключения, если строка, назначенная свойству `Name` является `null`.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing/coalescing.cs#1)]

- Метод или [лямбда](../operators/lambda-expressions.md), воплощающие выражение. В следующем примере показан метод, воплощающий выражение, который создает <xref:System.InvalidCastException>, так как преобразование в значение <xref:System.DateTime> не поддерживается.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied/exp-bodied.cs#1)]

## <a name="c-language-specification"></a>Спецификация языка C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [Ключевые слова в C#](index.md)
- [Практическое руководство. Явное создание исключений](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
