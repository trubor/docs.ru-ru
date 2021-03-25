---
title: Руководство по программированию на C#. Использование указателей для копирования массива байтов
description: Сведения об использовании указателей для копирования массива байтов. Изучите пример кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: f0122d29729ac8ad634f39f0643902e9bb78a8a5
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478598"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Руководство по программированию на C#. Использование указателей для копирования массива байтов

В следующем примере указатели используются для копирования байт из одного массива в другой.

В этом примере применяется ключевое слово [unsafe](../../language-reference/keywords/unsafe.md), которое позволяет использовать указатели в методе `Copy`. Оператор [fixed](../../language-reference/keywords/fixed-statement.md) используется для объявления указателей исходного и конечного массивов. Оператор `fixed`*закрепляет* расположение исходного и конечного массивов в памяти, чтобы они не перемещались при сборке мусора. Закрепление этих блоков памяти отменяется, когда завершается обработка блока `fixed`. Поскольку метод `Copy` в этом примере использует ключевое слово `unsafe`, он должен быть скомпилирован с параметром компилятора [**AllowUnsafeBlocks**](../../language-reference/compiler-options/language.md#allowunsafeblocks).

В этом примере доступ к элементам обоих массивов выполняется с помощью индексов, а не второго неуправляемого указателя. Объявление указателей `pSource` и `pTarget` закрепляет массивы. Эта возможность доступна начиная с C# 7.3.

## <a name="example"></a>Пример

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>См. также раздел

- [Руководство по программированию на C#](../index.md)
- [Небезопасный код и указатели](index.md)
- [**AllowUnsafeBlocks** (параметры компилятора C#)](../../language-reference/compiler-options/language.md#allowunsafeblocks)
- [Сборка мусора](../../../standard/garbage-collection/index.md)
