---
title: Руководство по программированию на C#. Отображение аргументов командной строки
description: Узнайте, как отобразить аргументы командной строки. Изучите пример кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 03/08/2021
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 7c3e8d7f6ad2a599308057e996808509e70b7508
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480272"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Руководство по программированию на C#. Отображение аргументов командной строки

Аргументы, предоставляемые исполняемому файлу в командной строке, доступны через [инструкции верхнего уровня](top-level-statements.md) или через необязательный параметр для метода `Main`. Аргументы предоставляются в форме массива строк. Каждый элемент массива содержит один аргумент. Пробелы между аргументами удаляются. Например, рассмотрим следующие вызовы из командной строки вымышленного исполняемого файла:  
  
|Входные данные в командной строке|Массив строк, передаваемых в метод Main|  
|----------------------------|-------------------------------------|  
|**executable.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe one two**|"one"<br /><br /> "two"|  
|**executable.exe "one two" three**|"один два"<br /><br /> "три"|  
  
> [!NOTE]
> При выполнении приложения в Visual Studio аргументы командной строки можно указать на [странице "Отладка" в конструкторе проектов](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Пример  

 Этот пример отображает аргументы командной строки, передаваемые в приложение командной строки. Показанные выходные данные — первая запись в таблице выше.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Main() и аргументы командной строки](./index.md)
- [Значения, возвращаемые методом main()](./main-return-values.md)
