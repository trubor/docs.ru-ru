---
description: Дополнительные сведения о инструкции DECLARE
title: Declare Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Declare
- vb.Lib
- vb.Any
helpviewer_keywords:
- Lib keyword [Visual Basic]
- declaring procedures [Visual Basic], Declare statement
- functions [Visual Basic], function procedures
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- procedures [Visual Basic], external
- Alias keyword [Visual Basic]
- external references [Visual Basic], Visual Basic
- DLLs, declaring procedures
- Declare statement [Visual Basic]
- declarations [Visual Basic], external
- Visual Basic code, Function procedures
- As keyword [Visual Basic], in Declare statement
- resources [Visual Basic], declaring
- Public keyword [Visual Basic], Declare statement
- platform invoke, Visual Basic external references
- Sub procedures [Visual Basic], declarations
- APIs, declaring API functions
- Visual Basic code, Sub procedures
- Function procedures [Visual Basic], declaring
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
ms.openlocfilehash: 4ceca6b1095e34a437f9363d95e4133e77809e83
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494562"
---
# <a name="declare-statement"></a>Declare Statement

Объявляет ссылку на процедуру, реализованную во внешнем файле.

## <a name="syntax"></a>Синтаксис

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ]
' -or-
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]
```

## <a name="parts"></a>Компоненты

|Термин|Определение|
|---|---|
|`attributelist`|Необязательный элемент. См. [список атрибутов](attribute-list.md).|
|`accessmodifier`|Необязательный параметр. Может принимать следующие значения:<br /><br /> -   [Закрытый](../modifiers/public.md)<br />-   [От](../modifiers/protected.md)<br />-   [Объявление](../modifiers/friend.md)<br />-   [Личному](../modifiers/private.md)<br />- [Защищенный дружественный](../modifiers/protected-friend.md)<br />- [Частный защищенный](../modifiers/private-protected.md)<br /><br /> См. раздел [уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Необязательный параметр. См. раздел [Shadows](../modifiers/shadows.md).|
|`charsetmodifier`|Необязательный параметр. Указывает набор символов и сведения для поиска файлов. Может принимать следующие значения:<br /><br /> -   [ANSI](../modifiers/ansi.md) (по умолчанию)<br />-   [Юникод](../modifiers/unicode.md)<br />-   [Авто](../modifiers/auto.md)|
|`Sub`|Необязательный, `Sub` но `Function` должен быть либо. Указывает, что внешняя процедура не возвращает значение.|
|`Function`|Необязательный, `Sub` но `Function` должен быть либо. Указывает, что внешняя процедура возвращает значение.|
|`name`|Обязательный. Имя этой внешней ссылки. Дополнительные сведения см. в разделе [Имена объявленных элементов](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Обязательный. Вводит `Lib` предложение, которое определяет внешний файл (DLL или ресурс кода), содержащий внешнюю процедуру.|
|`libname`|Обязательный. Имя файла, содержащего объявленную процедуру.|
|`Alias`|Необязательный параметр. Указывает, что объявляемая процедура не может быть идентифицирована в файле по имени, указанному в параметре `name` . Его идентификация указывается в `aliasname` .|
|`aliasname`|Требуется, если используется `Alias` ключевое слово. Строка, идентифицирующая процедуру одним из двух способов:<br /><br /> Имя точки входа для процедуры внутри ее файла в кавычках (). `""`<br /><br /> -или-<br /><br /> Знак решетки ( `#` ), за которым следует целое число, указывающее порядковый номер точки входа процедуры в пределах файла|
|`parameterlist`|Требуется, если процедура принимает параметры. См. [список параметров](parameter-list.md).|
|`returntype`|Обязательный, если `Function` указан, а `Option Strict` имеет значение `On` . Тип данных значения, возвращаемого процедурой.|

## <a name="remarks"></a>Комментарии

Иногда требуется вызвать процедуру, определенную в файле (например, в библиотеке DLL или ресурсе кода) за пределами проекта. При этом компилятор Visual Basic не имеет доступа к информации, которая необходима для корректного вызова процедуры, например, где находится процедура, как она идентифицируется, ее вызывающая последовательность и возвращаемый тип, а также используемая Кодировка строки. `Declare`Инструкция создает ссылку на внешнюю процедуру и предоставляет эту необходимую информацию.

`Declare` можно использовать только на уровне модуля. Это означает, что *контекст объявления* для внешней ссылки должен быть классом, структурой или модулем и не может быть исходным файлом, пространством имен, интерфейсом, процедурой или блоком. Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](declaration-contexts-and-default-access-levels.md).

По умолчанию внешние ссылки имеют [открытый](../modifiers/public.md) доступ. Уровни доступа можно изменить с помощью модификаторов доступа.

## <a name="rules"></a>Правила

- **Атрибута.** К внешней ссылке можно применять атрибуты. Любой применяемый атрибут действует только в проекте, а не во внешнем файле.

- **Модификаторы.** Внешние процедуры являются неявно [общими](../modifiers/shared.md). Нельзя использовать `Shared` ключевое слово при объявлении внешней ссылки, и изменить его общее состояние нельзя.

  Внешняя процедура не может участвовать в переопределении, реализации членов интерфейса или обработке событий. Соответственно, `Overrides` `Overridable` `NotOverridable` `MustOverride` `Implements` `Handles` в операторе нельзя использовать ключевое слово,,,,, или `Declare` .

- **Имя внешней процедуры.** Нет необходимости присваивать этой внешней ссылке то же имя (в), `name` что и имя точки входа процедуры во внешнем файле ( `aliasname` ). `Alias`Для указания имени точки входа можно использовать предложение. Это может быть полезно, если внешняя процедура имеет то же имя, что и зарезервированный модификатор Visual Basic, или переменную, процедуру или любой другой программный элемент в той же области.

  > [!NOTE]
  > В большинстве DLL имена точек входа чувствительны к регистру.

- **Номер внешней процедуры.** Кроме того, можно использовать `Alias` предложение, чтобы указать порядковый номер точки входа в таблице экспорта внешнего файла. Для этого начните `aliasname` со знака решетки ( `#` ). Это может быть полезно, если в Visual Basic не допускается любой символ из имени внешней процедуры или если внешний файл экспортирует процедуру без имени.

## <a name="data-type-rules"></a>Правила типов данных

- **Типы данных параметров.** Если `Option Strict` параметр имеет значение `On` , необходимо указать тип данных каждого параметра в `parameterlist` . Это может быть любой тип данных или имя перечисления, структуры, класса или интерфейса. В `parameterlist` используется `As` предложение для указания типа данных аргумента, который должен быть передан в каждый параметр.

  > [!NOTE]
  > Если внешняя процедура не была написана для платформа .NET Framework, необходимо соблюдать осторожность в соответствии с типами данных. Например, если объявить внешнюю ссылку на процедуру Visual Basic 6,0 с `Integer` параметром (16 бит в Visual Basic 6,0), необходимо определить соответствующий аргумент как `Short` в `Declare` инструкции, так как это 16-разрядный целочисленный тип в Visual Basic. Аналогично, `Long` имеет разную ширину данных в Visual Basic 6,0, и `Date` реализуется по-разному.

- **Тип возвращаемых данных.** Если внешняя процедура является `Function` и `Option Strict` имеет `On` значение, необходимо указать тип данных значения, возвращаемого в вызывающий код. Это может быть любой тип данных или имя перечисления, структуры, класса или интерфейса.

  > [!NOTE]
  > Компилятор Visual Basic не проверяет совместимость типов данных с параметрами внешней процедуры. При несовпадении среда CLR создает <xref:System.Runtime.InteropServices.MarshalDirectiveException> исключение во время выполнения.

- **Типы данных по умолчанию.** Если `Option Strict` параметр имеет значение `Off` и не указан тип данных параметра в `parameterlist` , компилятор Visual Basic преобразует соответствующий аргумент в [тип данных Object](../data-types/object-data-type.md). Аналогично, если не указать `returntype` , компилятор принимает тип возвращаемых данных `Object` .

  > [!NOTE]
  > Поскольку вы работаете с внешней процедурой, которая могла бы быть написана на другой платформе, небезопасно делать какие-либо предположения о типах данных или разрешать их по умолчанию. Намного безопаснее указывать тип данных каждого параметра и возвращаемого значения, если таковые имеются. Это также повышает удобочитаемость кода.

## <a name="behavior"></a>Поведение

- **Которых.** Внешняя ссылка находится в области действия класса, структуры или модуля.

- **Контролиру.** Внешняя ссылка имеет то же время существования, что и класс, структура или модуль, в котором он объявлен.

- **Вызов внешней процедуры.** Вы вызываете внешнюю процедуру точно так же, как при вызове `Function` процедуры или, `Sub` используя ее в выражении, если она возвращает значение, или путем указания его в [операторе Call](call-statement.md) , если он не возвращает значение.

  Аргументы для внешней процедуры передаются точно так же, как указано `parameterlist` в `Declare` инструкции. Не следует учитывать, как параметры были первоначально объявлены во внешнем файле. Аналогично, если имеется возвращаемое значение, используйте его точно так же, как указано `returntype` в `Declare` инструкции.

- **Кодировки.** Можно указать, `charsetmodifier` как Visual Basic должны маршалировать строки при вызове внешней процедуры. `Ansi`Модификатор направляет Visual Basic для маршалирования всех строк в значения ANSI, а `Unicode` модификатор указывает, что необходимо маршалировать все строки в значения Юникода. `Auto`Модификатор направляет Visual Basic для маршалирования строк в соответствии с правилами платформа .NET Framework, основанными на внешней ссылке `name` , или `aliasname` если они заданы. Значение по умолчанию — `Ansi`.

  `charsetmodifier` также указывает, как Visual Basic должен искать внешнюю процедуру во внешнем файле. `Ansi` и `Unicode` обе прямые Visual Basic, чтобы выполнить поиск без изменения имени во время поиска. `Auto` направляет Visual Basic определить базовый набор символов платформы времени выполнения и, возможно, изменить имя внешней процедуры следующим образом:

  - На платформе Юникода, например Windows, сначала ищите внешнюю процедуру без изменения имени. Если это не удается, добавьте "W" в конец имени внешней процедуры и повторите поиск.

  - На платформе ANSI сначала найдите внешнюю процедуру без изменения имени. Если это не удается, добавьте "A" в конец имени внешней процедуры и повторите поиск.

- **Механизм.** Visual Basic использует механизм *вызова платформы* платформа .NET Framework (PInvoke) для разрешения и доступа к внешним процедурам. `Declare`Оператор и <xref:System.Runtime.InteropServices.DllImportAttribute> класс используют этот механизм автоматически, и вам не требуется знание PInvoke. Дополнительные сведения см. в разделе [Пошаговое руководство. вызов интерфейсов API Windows](../../programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Если внешняя процедура выполняется вне среды CLR, это *неуправляемый код*. При вызове такой процедуры, например, функции Windows API или COM-метода, приложение может представлять угрозу безопасности. Дополнительные сведения см. в разделе [рекомендации по безопасному кодированию для неуправляемого кода](/previous-versions/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code).

## <a name="example"></a>Пример

В следующем примере объявляется внешняя ссылка на `Function` процедуру, которая возвращает имя текущего пользователя. Затем она вызывает внешнюю процедуру `GetUserNameA` как часть `getUser` процедуры.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Пример

<xref:System.Runtime.InteropServices.DllImportAttribute>Предоставляет альтернативный способ использования функций в неуправляемом коде. В следующем примере импортируемая функция объявляется без использования `Declare` инструкции.

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>См. также раздел

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Оператор Imports (пространство имен .NET и тип)](imports-statement-net-namespace-and-type.md)
- [Оператор AddressOf](../operators/addressof-operator.md)
- [Оператор Function](function-statement.md)
- [Оператор Sub](sub-statement.md)
- [Список параметров](parameter-list.md)
- [Оператор Call](call-statement.md)
- [Пошаговое руководство. Вызов API Windows](../../programming-guide/com-interop/walkthrough-calling-windows-apis.md)
