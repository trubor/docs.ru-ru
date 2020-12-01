---
title: Устранение рисков. Проверки двоеточий в путях
description: Узнайте об изменениях, внесенных в .NET Framework 4.6.2, для поддержки проверки правильности синтаксиса разделителя дисков (двоеточия).
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: 03f1c7249549aae7e3bef986c97fb5f320fbeb2f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283462"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="0b953-103">Устранение рисков. Проверки двоеточий в путях</span><span class="sxs-lookup"><span data-stu-id="0b953-103">Mitigation: Path Colon Checks</span></span>

<span data-ttu-id="0b953-104">Начиная с приложений, ориентированных на .NET Framework 4.6.2, выполнен ряд изменений для поддержки ранее не поддерживаемых путей (с точки зрения и длины, и формата).</span><span class="sxs-lookup"><span data-stu-id="0b953-104">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="0b953-105">В частности, усовершенствованы проверки правильности синтаксиса разделителя диска (двоеточия).</span><span class="sxs-lookup"><span data-stu-id="0b953-105">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="0b953-106">Последствия</span><span class="sxs-lookup"><span data-stu-id="0b953-106">Impact</span></span>  

 <span data-ttu-id="0b953-107">Эти изменения блокируют некоторые пути URI, которые ранее поддерживались методами <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> и <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0b953-107">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="0b953-108">Устранение рисков</span><span class="sxs-lookup"><span data-stu-id="0b953-108">Mitigation</span></span>  

 <span data-ttu-id="0b953-109">Чтобы обойти проблему с ранее допустимым путем, который больше не поддерживается методами <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> и <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>, можно сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="0b953-109">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="0b953-110">Вручную удалить схему из URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="0b953-110">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="0b953-111">Например, удалить `file://` из URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="0b953-111">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="0b953-112">передать код URI в конструктор <xref:System.Uri> и получить значение свойства <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>;</span><span class="sxs-lookup"><span data-stu-id="0b953-112">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="0b953-113">отказаться от новой нормализации путей, установив для параметра `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="0b953-113">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0b953-114">См. также</span><span class="sxs-lookup"><span data-stu-id="0b953-114">See also</span></span>

- [<span data-ttu-id="0b953-115">Совместимость приложений</span><span class="sxs-lookup"><span data-stu-id="0b953-115">Application compatibility</span></span>](application-compatibility.md)
