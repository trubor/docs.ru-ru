---
title: Предупреждение SYSLIB0011
description: Сведения об устаревших элементах, которые приводят к появлению предупреждения во время компиляции SYSLIB0011.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 85b5e07b1ecd6852d8c8e93cc3e89ced4b021ef9
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189861"
---
# <a name="syslib0011-binaryformatter-serialization-is-obsolete"></a><span data-ttu-id="9e38f-103">SYSLIB0011. Сериализация BinaryFormatter устарела</span><span class="sxs-lookup"><span data-stu-id="9e38f-103">SYSLIB0011: BinaryFormatter serialization is obsolete</span></span>

<span data-ttu-id="9e38f-104">Из-за [уязвимостей системы безопасности](../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) в <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, следующие API являются устаревшими, начиная с версии .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="9e38f-104">Due to [security vulnerabilities](../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="9e38f-105">При их использовании во время компиляции создается предупреждение `SYSLIB0011`.</span><span class="sxs-lookup"><span data-stu-id="9e38f-105">Using them in code generates warning `SYSLIB0011` at compile time.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="9e38f-106">Методы обхода проблемы</span><span class="sxs-lookup"><span data-stu-id="9e38f-106">Workarounds</span></span>

<span data-ttu-id="9e38f-107">Рассмотрите возможность использования <xref:System.Text.Json.JsonSerializer> или <xref:System.Xml.Serialization.XmlSerializer> вместо <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="9e38f-107">Consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer> instead of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span>

<span data-ttu-id="9e38f-108">Дополнительные сведения о рекомендуемых действиях см. в статье [Устранение ошибок, связанных с устареванием и отключением BinaryFormatter](../../../standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="9e38f-108">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="9e38f-109">См. также</span><span class="sxs-lookup"><span data-stu-id="9e38f-109">See also</span></span>

- [<span data-ttu-id="9e38f-110">Устранение ошибок, связанных с устареванием и отключением BinaryFormatter</span><span class="sxs-lookup"><span data-stu-id="9e38f-110">Resolving BinaryFormatter obsoletion and disablement errors</span></span>](../../../standard/serialization/binaryformatter-security-guide.md)
- [<span data-ttu-id="9e38f-111">Методы сериализации BinaryFormatter устарели и запрещены в приложениях ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9e38f-111">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](../core-libraries/5.0/binaryformatter-serialization-obsolete.md)
