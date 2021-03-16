---
title: Практическое руководство. Создание конструктора копий (руководство по программированию на C#)
description: Узнайте, как создать конструктор копий в C#, который принимает экземпляр класса и возвращает новый экземпляр со значениями входных данных.
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: c61018444dd600d6f33765b104034355d0301667
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255240"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Практическое руководство. Создание конструктора копий (руководство по программированию на C#)

Для [записей](records.md) C# предоставляет конструктор копирования для объектов, но для классов его необходимо писать самостоятельно.  
  
## <a name="example"></a>Пример  

 В следующем примере [класс](../../language-reference/keywords/class.md)`Person` определяет конструктор копии, который использует экземпляр `Person`в качестве аргумента. Значения свойств аргумента присваиваются свойствам нового экземпляра `Person`. Код содержит дополнительный конструктор копии, который отправляет свойства `Name` и `Age` экземпляра, который необходимо скопировать конструктору экземпляра класса.  
  
 [!code-csharp[CopyConstructor](snippets/how-to-write-a-copy-constructor/Program.cs)]

## <a name="see-also"></a>См. также

- <xref:System.ICloneable>
- [Записи](records.md)
- [Руководство по программированию на C#](../index.md)
- [Классы и структуры](./index.md)
- [Конструкторы](./constructors.md)
- [Методы завершения](./destructors.md)
