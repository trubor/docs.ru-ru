---
title: Критическое изменение. Изменения в заметках ссылочного типа, допускающих значения NULL
description: Ознакомьтесь с критическим изменением .NET 6 в основных библиотеках .NET, в которых изменились некоторые заметки ссылочного типа, допускающие значения NULL.
ms.date: 02/11/2021
ms.openlocfilehash: fe56fd3006528238713bd08f353b5044092043a2
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256937"
---
# <a name="changes-to-nullable-reference-type-annotations"></a>Изменения в заметках ссылочного типа, допускающих значения NULL

В .NET 6 некоторые заметки о допустимости значений NULL в библиотеках .NET были изменены.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET некоторые заметки ссылочного типа, допускающие значения NULL, не верны, а предупреждения сборки либо отсутствуют, либо неверны. Начиная с .NET 6, были обновлены некоторые заметки, которые применялись ранее. Будут созданы новые предупреждения сборки, а неправильные предупреждения сборки для затронутых API больше не будут создаваться.

Некоторые из этих изменений считаются *критическими*, поскольку они могут привести к появлению новых предупреждений во время сборки. При переходе на .NET 6 необходимо обновить код, который ссылается на такие API.

Другие изменения, которые не считаются критическими, также описаны на этой странице. Любой код, ссылающийся на обновленные API, может стать эффективнее за счет удаления операторов или прагм, которые больше не нужны.

## <a name="version-introduced"></a>Представленная версия

6,0

## <a name="reason-for-change"></a>Причина изменения

Начиная с .NET Core 3.0, к библиотекам .NET были применены заметки о допустимости значений NULL. С самого начала ожидались ошибки в этих заметках. Благодаря отзывам и дальнейшему тестированию заметки, допускающие значение NULL для затрагиваемых API, были определены как неточные. В обновленных заметках правильно представлены контракты допустимости значений NULL для API.

## <a name="recommended-action"></a>Рекомендованное действие

Обновите код, в результате выполнения которого API отражают изменения в контрактах, допускающих значения NULL.

## <a name="affected-apis"></a>Затронутые API

Затронутые API перечислены в следующей таблице:

| API | Изменения | Критическое или некритическое | Добавлено в версии |
| - | - | - |
| <xref:System.ComponentModel.ISite.Container?displayProperty=nameWithType> | Тип свойства допускает значение NULL | Критическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XContainer.Add(System.Object[])?displayProperty=nameWithType> | Тип параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XContainer.AddFirst(System.Object[])?displayProperty=nameWithType> | Тип параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XContainer.ReplaceNodes(System.Object[])?displayProperty=nameWithType> | Тип параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XDocument.%23ctor(System.Object[])> | Тип параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XDocument.%23ctor(System.Xml.Linq.XDeclaration,System.Object[])> | Тип параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XElement.%23ctor(System.Xml.Linq.XName,System.Object[])> | Тип второго параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XElement.ReplaceAll(System.Object[])?displayProperty=nameWithType> | Тип параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XElement.ReplaceAttributes(System.Object[])?displayProperty=nameWithType> | Тип параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XNode.AddAfterSelf(System.Object[])?displayProperty=nameWithType> | Тип параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XNode.AddBeforeSelf(System.Object[])?displayProperty=nameWithType> | Тип параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XNode.ReplaceWith(System.Object[])?displayProperty=nameWithType> | Тип параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XStreamingElement.%23ctor(System.Xml.Linq.XName,System.Object)> | Тип второго параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XStreamingElement.%23ctor(System.Xml.Linq.XName,System.Object[])> | Тип второго параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Xml.Linq.XStreamingElement.Add(System.Object[])?displayProperty=nameWithType> | Тип параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Net.Http.HttpClient.PatchAsync%2A?displayProperty=nameWithType> | Тип параметра `content` допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Net.Http.HttpClient.PostAsync%2A?displayProperty=nameWithType> | Тип параметра `content` допускает значение NULL  | Некритическое | Предварительная версия 1 |
| <xref:System.Net.Http.HttpClient.PutAsync%2A?displayProperty=nameWithType> | Тип параметра `content` допускает значение NULL  | Некритическое | Предварительная версия 1 |
| <xref:System.Linq.Expressions.MethodCallExpression.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.Expression})?displayProperty=nameWithType> | Тип первого параметра допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Linq.Expressions.Expression%601.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.ParameterExpression})?displayProperty=nameWithType> | Тип возвращаемого значения не допускает значение NULL | Некритическое | Предварительная версия 1 |
| <xref:System.Data.IDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> | Тип параметра `buffer` допускает значение NULL | Критическое | Предварительная версия 1 |
| <xref:System.Data.IDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType> | Тип параметра `buffer` допускает значение NULL | Критическое | Предварительная версия 1 |
| <xref:System.Data.Common.DbDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> | Тип параметра `buffer` допускает значение NULL | Критическое | Предварительная версия 1 |
| <xref:System.Data.Common.DbDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType> | Тип параметра `buffer` допускает значение NULL | Критическое | Предварительная версия 1 |
| <xref:System.Net.HttpListenerContext.AcceptWebSocketAsync%2A?displayProperty=fullName> | Тип параметра `subProtocol` допускает значение NULL | Некритическое | Предварительная версия 2 |
| Методы, переопределяющие <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType>, и [многие другие , возвращающие`bool`](https://github.com/dotnet/runtime/pull/47598/files) | `[NotNullWhen(true)]` добавлено к первому параметру, допускающему значение NULL | Критическое | Предварительная версия 2 |

## <a name="see-also"></a>См. также раздел

- [Изменения в заметках ссылочного типа, допускающих значения NULL в ASP.NET Core](../../aspnet-core/6.0/nullable-reference-type-annotations-changed.md)

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.ComponentModel.ISite.Container`
- `M:System.Xml.Linq.XContainer.Add(System.Object[])`
- `M:System.Xml.Linq.XContainer.AddFirst(System.Object[])`
- `M:System.Xml.Linq.XContainer.ReplaceNodes(System.Object[])`
- `M:System.Xml.Linq.XDocument.#ctor(System.Object[])`
- `M:System.Xml.Linq.XDocument.#ctor(System.Xml.Linq.XDeclaration,System.Object[])`
- `M:System.Xml.Linq.XElement.#ctor(System.Xml.Linq.XName,System.Object[])`
- `M:System.Xml.Linq.XElement.ReplaceAll(System.Object[])`
- `M:System.Xml.Linq.XElement.ReplaceAttributes(System.Object[])`
- `M:System.Xml.Linq.XNode.AddAfterSelf(System.Object[])`
- `M:System.Xml.Linq.XNode.AddBeforeSelf(System.Object[])`
- `M:System.Xml.Linq.XNode.ReplaceWith(System.Object[])`
- `M:System.Xml.Linq.XStreamingElement.#ctor(System.Xml.Linq.XName,System.Object)`
- `M:System.Xml.Linq.XStreamingElement.#ctor(System.Xml.Linq.XName,System.Object[])`
- `M:System.Xml.Linq.XStreamingElement.Add(System.Object[])`
- `O:System.Net.Http.HttpClient.PatchAsync`
- `O:System.Net.Http.HttpClient.PostAsync`
- `O:System.Net.Http.HttpClient.PutAsync`
- `M:System.Linq.Expressions.MethodCallExpression.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.Expression})`
- `M:System.Linq.Expressions.Expression%601.Update(System.Linq.Expressions.Expression,System.Collections.Generic.IEnumerable{System.Linq.Expressions.ParameterExpression})`
- `M:System.Data.IDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)`
- `M:System.Data.IDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)`
- `M:System.Data.Common.DbDataRecord.GetBytes(System.Int32,System.Int64,System.Byte[],System.Int32,System.Int32)`
- `M:System.Data.Common.DbDataRecord.GetChars(System.Int32,System.Int64,System.Char[],System.Int32,System.Int32)`

-->
