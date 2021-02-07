---
description: 'Дополнительные сведения о: Маиладдресспарсер Class'
title: Класс Маиладдресспарсер (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.MailAddressParser
- System.Net.Mail.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 5ad534e731e283f5449b3b8cc8e87628716da9b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699770"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="55e0f-103">Класс MailAddressParser</span><span class="sxs-lookup"><span data-stu-id="55e0f-103">MailAddressParser class</span></span>

<span data-ttu-id="55e0f-104">Анализирует адреса электронной почты, как описано в RFC 2822.</span><span class="sxs-lookup"><span data-stu-id="55e0f-104">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="55e0f-105">Этот класс не наследуется.</span><span class="sxs-lookup"><span data-stu-id="55e0f-105">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="55e0f-106">Этот класс является внутренним и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="55e0f-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="55e0f-107">Корпорация Майкрософт не поддерживает использование этого класса в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="55e0f-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="55e0f-108">Метод Парсеаддресс</span><span class="sxs-lookup"><span data-stu-id="55e0f-108">ParseAddress method</span></span>

<span data-ttu-id="55e0f-109">Выполняет синтаксический анализ одного адреса электронной почты из указанной строки.</span><span class="sxs-lookup"><span data-stu-id="55e0f-109">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="55e0f-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="55e0f-110">Parameters</span></span>

<span data-ttu-id="55e0f-111">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="55e0f-111">`data` <xref:System.String></span></span>

<span data-ttu-id="55e0f-112">Строка, содержащая адрес электронной почты для синтаксического анализа.</span><span class="sxs-lookup"><span data-stu-id="55e0f-112">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="55e0f-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="55e0f-113">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="55e0f-114">Допустимый адрес электронной почты.</span><span class="sxs-lookup"><span data-stu-id="55e0f-114">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="55e0f-115">Исключения</span><span class="sxs-lookup"><span data-stu-id="55e0f-115">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="55e0f-116">Недопустимый адрес электронной почты.</span><span class="sxs-lookup"><span data-stu-id="55e0f-116">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="55e0f-117">Требования</span><span class="sxs-lookup"><span data-stu-id="55e0f-117">Requirements</span></span>

<span data-ttu-id="55e0f-118">**Пространство имен:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="55e0f-118">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="55e0f-119">**Сборка:** Система (в System.dll)</span><span class="sxs-lookup"><span data-stu-id="55e0f-119">**Assembly:** System (in System.dll)</span></span>
