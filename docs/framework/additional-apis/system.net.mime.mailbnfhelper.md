---
description: 'Дополнительные сведения о: Маилбнфхелпер Class'
title: Класс Маилбнфхелпер (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mime.MailBnfHelper
- System.Net.Mime.MailBnfHelper.Ascii7bitMaxValue
- System.Net.Mime.MailBnfHelper.Atext
- System.Net.Mime.MailBnfHelper.CR
- System.Net.Mime.MailBnfHelper.Ctext
- System.Net.Mime.MailBnfHelper.Dot
- System.Net.Mime.MailBnfHelper.EndComment
- System.Net.Mime.MailBnfHelper.LF
- System.Net.Mime.MailBnfHelper.Space
- System.Net.Mime.MailBnfHelper.StartComment
- System.Net.Mime.MailBnfHelper.Tab
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 942b5c423d2f63985a8f7840f69d956bbade7582
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699653"
---
# <a name="mailbnfhelper-class"></a><span data-ttu-id="bb97a-103">Класс MailBnfHelper</span><span class="sxs-lookup"><span data-stu-id="bb97a-103">MailBnfHelper class</span></span>

<span data-ttu-id="bb97a-104">Содержит служебные методы для синтаксического анализа строк в формате сообщений Интернета.</span><span class="sxs-lookup"><span data-stu-id="bb97a-104">Contains utility methods for parsing internet message-formatted strings.</span></span> <span data-ttu-id="bb97a-105">Этот класс не наследуется.</span><span class="sxs-lookup"><span data-stu-id="bb97a-105">This class cannot be inherited.</span></span>

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> <span data-ttu-id="bb97a-106">Этот класс является внутренним и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="bb97a-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="bb97a-107">Корпорация Майкрософт не поддерживает использование этого класса в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="bb97a-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="ascii7bitmaxvalue-field"></a><span data-ttu-id="bb97a-108">Поле Ascii7bitMaxValue</span><span class="sxs-lookup"><span data-stu-id="bb97a-108">Ascii7bitMaxValue field</span></span>

<span data-ttu-id="bb97a-109">Представляет максимальное 7-разрядное значение ASCII.</span><span class="sxs-lookup"><span data-stu-id="bb97a-109">Represents the maximum 7-bit Ascii value.</span></span>

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a><span data-ttu-id="bb97a-110">Поле аТекст</span><span class="sxs-lookup"><span data-stu-id="bb97a-110">Atext field</span></span>

<span data-ttu-id="bb97a-111">Представляет символы, разрешенные в атомах.</span><span class="sxs-lookup"><span data-stu-id="bb97a-111">Represents the characters allowed in atoms.</span></span>

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a><span data-ttu-id="bb97a-112">Поле CR</span><span class="sxs-lookup"><span data-stu-id="bb97a-112">CR field</span></span>

<span data-ttu-id="bb97a-113">Представляет символ возврата каретки.</span><span class="sxs-lookup"><span data-stu-id="bb97a-113">Represents the carriage-return character.</span></span>

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a><span data-ttu-id="bb97a-114">Поле столбец ctext</span><span class="sxs-lookup"><span data-stu-id="bb97a-114">Ctext field</span></span>

<span data-ttu-id="bb97a-115">Представляет символы, разрешенные внутри комментариев.</span><span class="sxs-lookup"><span data-stu-id="bb97a-115">Represents the characters allowed inside of comments.</span></span>

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a><span data-ttu-id="bb97a-116">Поле точки</span><span class="sxs-lookup"><span data-stu-id="bb97a-116">Dot field</span></span>

<span data-ttu-id="bb97a-117">Представляет символ полной позиции ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="bb97a-117">Represents the full-stop character (`.`).</span></span>

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a><span data-ttu-id="bb97a-118">Поле Ендкоммент</span><span class="sxs-lookup"><span data-stu-id="bb97a-118">EndComment field</span></span>

<span data-ttu-id="bb97a-119">Представляет символ, указывающий конец комментария.</span><span class="sxs-lookup"><span data-stu-id="bb97a-119">Represents the character that specifies the end of a comment.</span></span>

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a><span data-ttu-id="bb97a-120">Поле LF</span><span class="sxs-lookup"><span data-stu-id="bb97a-120">LF field</span></span>

<span data-ttu-id="bb97a-121">Представляет символ перевода строки.</span><span class="sxs-lookup"><span data-stu-id="bb97a-121">Represents the line-feed character.</span></span>

```csharp
internal static readonly char LF
```

## <a name="space-field"></a><span data-ttu-id="bb97a-122">Поле пробела</span><span class="sxs-lookup"><span data-stu-id="bb97a-122">Space field</span></span>

<span data-ttu-id="bb97a-123">Представляет символ пробела.</span><span class="sxs-lookup"><span data-stu-id="bb97a-123">Represents the space character.</span></span>

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a><span data-ttu-id="bb97a-124">Поле Старткоммент</span><span class="sxs-lookup"><span data-stu-id="bb97a-124">StartComment field</span></span>

<span data-ttu-id="bb97a-125">Представляет символ, указывающий начало комментария.</span><span class="sxs-lookup"><span data-stu-id="bb97a-125">Represents the character that specifies the start of a comment.</span></span>

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a><span data-ttu-id="bb97a-126">Поле вкладки</span><span class="sxs-lookup"><span data-stu-id="bb97a-126">Tab field</span></span>

<span data-ttu-id="bb97a-127">Представляет символ табуляции.</span><span class="sxs-lookup"><span data-stu-id="bb97a-127">Represents the tab character.</span></span>

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a><span data-ttu-id="bb97a-128">Требования</span><span class="sxs-lookup"><span data-stu-id="bb97a-128">Requirements</span></span>

<span data-ttu-id="bb97a-129">**Пространство имен:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="bb97a-129">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="bb97a-130">**Сборка:** Система (в System.dll)</span><span class="sxs-lookup"><span data-stu-id="bb97a-130">**Assembly:** System (in System.dll)</span></span>
