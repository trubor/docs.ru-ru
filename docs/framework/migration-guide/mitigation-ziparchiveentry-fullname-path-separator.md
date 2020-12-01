---
title: Устранение рисков. Разделитель пути ZipArchiveEntry.FullName
description: Узнайте, какие изменения претерпел разделитель пути для свойства ZipArchiveEntry.FullName, начиная с приложений, предназначенных для .NET Framework 4.6.1.
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 6e2c0908098f8487f7d429274fe7ad797bedfda1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283449"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="72839-103">Устранение рисков. Разделитель пути ZipArchiveEntry.FullName</span><span class="sxs-lookup"><span data-stu-id="72839-103">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="72839-104">Начиная с приложений, предназначенных для .NET Framework 4.6.1, изменен разделитель пути для свойства <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType>: вместо обратной косой черты ("\\"), используемой в предыдущих версиях платформы .NET Framework, теперь используется прямая косая черта ("/").</span><span class="sxs-lookup"><span data-stu-id="72839-104">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="72839-105">Объекты <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> создаются путем вызова одной из перегрузок метода <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="72839-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="72839-106">Последствия</span><span class="sxs-lookup"><span data-stu-id="72839-106">Impact</span></span>  

 <span data-ttu-id="72839-107">Изменение обеспечивает соответствие реализации .NET разделу 4.4.17.1 [спецификации формата ZIP-файла](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) и позволяет распаковывать ZIP-архивы в системах, отличных от Windows.</span><span class="sxs-lookup"><span data-stu-id="72839-107">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="72839-108">При распаковке ZIP-файла, созданного приложением, предназначенным для предыдущей версии платформы .NET Framework, в операционных системах, отличающихся от Windows, таких как MacOS, не удается сохранить структуру каталогов.</span><span class="sxs-lookup"><span data-stu-id="72839-108">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="72839-109">Например, на компьютерах MacOS создается набор файлов, имена которых содержат путь к каталогу вместе со всеми символами обратной косой черты ("\\") и именами файлов.</span><span class="sxs-lookup"><span data-stu-id="72839-109">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="72839-110">В результате структура каталогов распакованных файлов не сохраняется.</span><span class="sxs-lookup"><span data-stu-id="72839-110">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="72839-111">Влияние этого изменения на ZIP-файлы, которые распаковываются в операционной системе Windows API-интерфейсами из пространства имен .NET Framework <xref:System.IO>, должно быть минимальным, поскольку эти API принимают в качестве знака разделения в пути как косую черту ("/"), так и обратную косую черту ("\\") .</span><span class="sxs-lookup"><span data-stu-id="72839-111">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="72839-112">Устранение рисков</span><span class="sxs-lookup"><span data-stu-id="72839-112">Mitigation</span></span>  

 <span data-ttu-id="72839-113">Если такое поведение нежелательно, от него можно отказаться, добавив параметр конфигурации в раздел [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="72839-113">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="72839-114">Ниже показаны как раздел `<runtime>`, так и параметр отключения функции.</span><span class="sxs-lookup"><span data-stu-id="72839-114">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="72839-115">Кроме того, в приложениях, предназначенных для предыдущих версий .NET Framework, но выполняемых в .NET Framework 4.6.1 и более поздних версиях, можно включить такое поведение, добавив параметр конфигурации в раздел [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="72839-115">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="72839-116">Ниже показаны как раздел `<runtime>`, так и параметр включения функции.</span><span class="sxs-lookup"><span data-stu-id="72839-116">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72839-117">См. также</span><span class="sxs-lookup"><span data-stu-id="72839-117">See also</span></span>

- [<span data-ttu-id="72839-118">Совместимость приложений</span><span class="sxs-lookup"><span data-stu-id="72839-118">Application compatibility</span></span>](application-compatibility.md)
