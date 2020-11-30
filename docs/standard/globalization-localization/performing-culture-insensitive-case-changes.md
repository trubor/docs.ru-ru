---
title: Выполнение смены регистра независимо от языка и региональных параметров
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
ms.openlocfilehash: d4e714e9b81ffc3e495f4ddaa8cf7eeedeb71261
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685998"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="63982-102">Выполнение смены регистра независимо от языка и региональных параметров</span><span class="sxs-lookup"><span data-stu-id="63982-102">Performing Culture-Insensitive Case Changes</span></span>

<span data-ttu-id="63982-103">Методы <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> и <xref:System.Char.ToLower%2A?displayProperty=nameWithType> предоставляют перегрузки, которые не принимают параметры.</span><span class="sxs-lookup"><span data-stu-id="63982-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="63982-104">По умолчанию эти перегрузки без параметров выполняют изменения регистра на основе значения <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="63982-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="63982-105">Результат преобразования чувствителен к регистру и может быть разным для языков и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="63982-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="63982-106">Чтобы четко указать, нужно ли учитывать язык и региональные параметры при изменении регистра, используйте перегрузки этих методов, принимающие параметр `culture` явным образом.</span><span class="sxs-lookup"><span data-stu-id="63982-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="63982-107">Чтобы изменить регистр с учетом языка и региональных параметров, укажите значение `CultureInfo.CurrentCulture` для параметра `culture`.</span><span class="sxs-lookup"><span data-stu-id="63982-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="63982-108">Чтобы изменить регистр без учета языка и региональных параметров, укажите значение `CultureInfo.InvariantCulture` для параметра `culture`.</span><span class="sxs-lookup"><span data-stu-id="63982-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="63982-109">Обычно строки преобразуются в стандартный регистр, чтобы упростить поиск по этим значениям.</span><span class="sxs-lookup"><span data-stu-id="63982-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="63982-110">Если вы намерены применить такой подход, укажите значение `CultureInfo.InvariantCulture` для параметра `culture`, так как значение <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> может быть разным в момент преобразования регистра и в момент поиска.</span><span class="sxs-lookup"><span data-stu-id="63982-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="63982-111">Если регистр важен для работы системы безопасности, такие операции ни в коем случае не должны зависеть от языка и региона, чтобы значение параметра `CultureInfo.CurrentCulture` не влияло на результат.</span><span class="sxs-lookup"><span data-stu-id="63982-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="63982-112">Пример строковых операций с учетом языка и региональных параметров, дающих противоречивые результаты, см. в разделе "Сравнение строк с использованием текущего языка и региональных параметров" статьи [Советы и рекомендации по использованию строк в .NET](../base-types/best-practices-strings.md).</span><span class="sxs-lookup"><span data-stu-id="63982-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="63982-113">Использование методов String.ToUpper и String.ToLower</span><span class="sxs-lookup"><span data-stu-id="63982-113">Using the String.ToUpper and String.ToLower Methods</span></span>  

 <span data-ttu-id="63982-114">Чтобы повысить читаемость кода, мы рекомендуем всегда использовать перегрузки методов `String.ToUpper` и `String.ToLower`, позволяющие явным образом указать параметр `culture`.</span><span class="sxs-lookup"><span data-stu-id="63982-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="63982-115">Например, приведенный ниже код выполняет поиск идентификатора.</span><span class="sxs-lookup"><span data-stu-id="63982-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="63982-116">Операция `key.ToLower` по умолчанию зависит от языка и региональных параметров, но это поведение никак не отражено в коде.</span><span class="sxs-lookup"><span data-stu-id="63982-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="63982-117">Пример</span><span class="sxs-lookup"><span data-stu-id="63982-117">Example</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 <span data-ttu-id="63982-118">Если нужно, чтобы операция `key.ToLower` зависела от языка и региональных параметров, измените приведенный выше пример так, чтобы явно указать `CultureInfo.InvariantCulture` для изменения регистра.</span><span class="sxs-lookup"><span data-stu-id="63982-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="63982-119">Использование методов Char.ToUpper и Char.ToLower</span><span class="sxs-lookup"><span data-stu-id="63982-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  

 <span data-ttu-id="63982-120">Методы `Char.ToUpper` и `Char.ToLower` действуют точно так же, как и методы `String.ToUpper` и `String.ToLower`, за исключением турецкого (Турция) и азербайджанского (латиница, Азербайджан) языков.</span><span class="sxs-lookup"><span data-stu-id="63982-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="63982-121">Только для этих значений языка и региональных параметров изменяется применение регистра для одиночных символов.</span><span class="sxs-lookup"><span data-stu-id="63982-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="63982-122">Дополнительные сведения об этом уникальном сопоставлении регистра см. в разделе "Регистр" описания класса <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="63982-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="63982-123">Чтобы повысить читаемость кода и стабильность результатов, мы рекомендуем всегда использовать перегрузки этих методов, позволяющие явным образом указать параметр `culture`.</span><span class="sxs-lookup"><span data-stu-id="63982-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63982-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="63982-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="63982-125">Выполнение строковых операций, не зависящих от языка и региональных параметров</span><span class="sxs-lookup"><span data-stu-id="63982-125">Performing Culture-Insensitive String Operations</span></span>](performing-culture-insensitive-string-operations.md)
