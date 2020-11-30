---
title: Практическое руководство. Отображение миллисекунд в значениях даты и времени
description: В этой статье показано, как включить компонент миллисекунд даты и времени в форматированные строки даты и времени в .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime.ToString method
- displaying date and time data
- time [.NET], milliseconds
- dates [.NET], milliseconds
- milliseconds [.NET]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
ms.openlocfilehash: 722334c324f663ba46a3c861885d4221fc566b8d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681266"
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a><span data-ttu-id="608f7-103">Практическое руководство. Отображение миллисекунд в значениях даты и времени</span><span class="sxs-lookup"><span data-stu-id="608f7-103">How to: Display Milliseconds in Date and Time Values</span></span>

<span data-ttu-id="608f7-104">Стандартные методы форматирования даты и времени, например <xref:System.DateTime.ToString?displayProperty=nameWithType>, поддерживают часы, минуты и секунды, но не миллисекунды.</span><span class="sxs-lookup"><span data-stu-id="608f7-104">The default date and time formatting methods, such as <xref:System.DateTime.ToString?displayProperty=nameWithType>, include the hours, minutes, and seconds of a time value but exclude its milliseconds component.</span></span> <span data-ttu-id="608f7-105">В этом разделе показано, как включить компонент миллисекунд даты и времени в форматированные строки даты и времени.</span><span class="sxs-lookup"><span data-stu-id="608f7-105">This topic shows how to include a date and time's millisecond component in formatted date and time strings.</span></span>  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a><span data-ttu-id="608f7-106">Отображение компонента миллисекунд для значения DateTime</span><span class="sxs-lookup"><span data-stu-id="608f7-106">To display the millisecond component of a DateTime value</span></span>  
  
1. <span data-ttu-id="608f7-107">Если вы работаете со строковым представлением даты, преобразуйте ее в значение типа <xref:System.DateTime> или <xref:System.DateTimeOffset>, используя статичный метод <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> или <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="608f7-107">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="608f7-108">Чтобы извлечь строковое представление компонента миллисекунд, вызовите метод <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>или <xref:System.DateTimeOffset.ToString%2A> для значения даты и времени, передав ему в параметре `format` шаблон пользовательского формата `fff` или `FFF`, отдельно или с другим описателем пользовательского формата.</span><span class="sxs-lookup"><span data-stu-id="608f7-108">To extract the string representation of a time's millisecond component, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%2A> method, and pass the `fff` or `FFF` custom format pattern either alone or with other custom format specifiers as the `format` parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="608f7-109">Пример</span><span class="sxs-lookup"><span data-stu-id="608f7-109">Example</span></span>  

 <span data-ttu-id="608f7-110">Этот пример выводит в консоль компонент миллисекунд <xref:System.DateTime> и значение <xref:System.DateTimeOffset>, как отдельно, так и в составе более длинной строки даты и времени.</span><span class="sxs-lookup"><span data-stu-id="608f7-110">The example displays the millisecond component of a <xref:System.DateTime> and a <xref:System.DateTimeOffset> value to the console, both alone and included in a longer date and time string.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 <span data-ttu-id="608f7-111">Шаблон формата `fff` содержит конечные нули в значении миллисекунд.</span><span class="sxs-lookup"><span data-stu-id="608f7-111">The `fff` format pattern includes any trailing zeros in the millisecond value.</span></span> <span data-ttu-id="608f7-112">Шаблон формата `FFF` запрещает их.</span><span class="sxs-lookup"><span data-stu-id="608f7-112">The `FFF` format pattern suppresses them.</span></span> <span data-ttu-id="608f7-113">Эта разница показана в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="608f7-113">The difference is illustrated in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 <span data-ttu-id="608f7-114">Проблема с определением полного описателя пользовательского формата, содержащего компонент миллисекунд, состоит в том, что он жестко задает формат, который может не соответствовать взаимному расположению элементов времени в текущих региональных параметрах приложения.</span><span class="sxs-lookup"><span data-stu-id="608f7-114">A problem with defining a complete custom format specifier that includes the millisecond component of a date and time is that it defines a hard-coded format that may not correspond to the arrangement of time elements in the application's current culture.</span></span> <span data-ttu-id="608f7-115">Вместо этого лучше всего извлечь один из шаблонов отображения даты и времени, определенных текущим объектом языка и региональных параметров <xref:System.Globalization.DateTimeFormatInfo>, а затем изменить его для поддержки миллисекунд.</span><span class="sxs-lookup"><span data-stu-id="608f7-115">A better alternative is to retrieve one of the date and time display patterns defined by the current culture's <xref:System.Globalization.DateTimeFormatInfo> object and modify it to include milliseconds.</span></span> <span data-ttu-id="608f7-116">Этот подход также показан в примере.</span><span class="sxs-lookup"><span data-stu-id="608f7-116">The example also illustrates this approach.</span></span> <span data-ttu-id="608f7-117">Он извлекает шаблон полного отображения даты и времени для текущих языка и региональных параметров, обратившись к свойству <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType>, а затем добавляет в него пользовательский шаблон `.ffff` после шаблона секунд.</span><span class="sxs-lookup"><span data-stu-id="608f7-117">It retrieves the current culture's full date and time pattern from the <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> property, and then inserts the custom pattern `.ffff` after its seconds pattern.</span></span> <span data-ttu-id="608f7-118">Обратите внимание, что в примере используется регулярное выражение для выполнения этой операции в одном методе.</span><span class="sxs-lookup"><span data-stu-id="608f7-118">Note that the example uses a regular expression to perform this operation in a single method call.</span></span>  
  
 <span data-ttu-id="608f7-119">Описатель настраиваемого формата также используется для отображения дробной части секунд, отличной от миллисекунд.</span><span class="sxs-lookup"><span data-stu-id="608f7-119">You can also use a custom format specifier to display a fractional part of seconds other than milliseconds.</span></span> <span data-ttu-id="608f7-120">Например, описатель пользовательского формата `f` или `F` отображает десятые доли секунды, описатель `ff` или `FF` — сотые доли секунды, а описатель `ffff` или `FFFF` — десятитысячные доли секунды.</span><span class="sxs-lookup"><span data-stu-id="608f7-120">For example, the `f` or `F` custom format specifier displays tenths of a second, the `ff` or `FF` custom format specifier displays hundredths of a second, and the `ffff` or `FFFF` custom format specifier displays ten thousandths of a second.</span></span> <span data-ttu-id="608f7-121">Дробные части миллисекунд усекаются, а не округляются в возвращаемой строке.</span><span class="sxs-lookup"><span data-stu-id="608f7-121">Fractional parts of a millisecond are truncated instead of rounded in the returned string.</span></span> <span data-ttu-id="608f7-122">Эти описатели формата используются в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="608f7-122">These format specifiers are used in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
> <span data-ttu-id="608f7-123">Существует возможность отображать малые дробные части секунды, например десятитысячные или стотысячные доли секунды.</span><span class="sxs-lookup"><span data-stu-id="608f7-123">It is possible to display very small fractional units of a second, such as ten thousandths of a second or hundred-thousandths of a second.</span></span> <span data-ttu-id="608f7-124">Однако эти значения могут не иметь смысла.</span><span class="sxs-lookup"><span data-stu-id="608f7-124">However, these values may not be meaningful.</span></span> <span data-ttu-id="608f7-125">Точность значений даты и времени зависит от разрешения системных часов.</span><span class="sxs-lookup"><span data-stu-id="608f7-125">The precision of date and time values depends on the resolution of the system clock.</span></span> <span data-ttu-id="608f7-126">В операционной системе Windows NT 3.5 и более поздних версий, а также Windows Vista разрешение часов приблизительно соответствует 10–15 миллисекундам.</span><span class="sxs-lookup"><span data-stu-id="608f7-126">On Windows NT 3.5 and later, and Windows Vista operating systems, the clock's resolution is approximately 10-15 milliseconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608f7-127">См. также</span><span class="sxs-lookup"><span data-stu-id="608f7-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="608f7-128">Строки настраиваемых форматов даты и времени</span><span class="sxs-lookup"><span data-stu-id="608f7-128">Custom Date and Time Format Strings</span></span>](custom-date-and-time-format-strings.md)
