---
title: Устранение рисков. Кадры PNG в объектах Icon
description: Узнайте, как настроить поведение кадров PNG в объектах значков, если новое поведение, включенное в .NET Framework 4.6 и более поздние версии, нежелательно.
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: a8bb4fca19a09f16c89ce8c5da08ebcae9a037ec
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276585"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="7a744-103">Устранение рисков. Кадры PNG в объектах Icon</span><span class="sxs-lookup"><span data-stu-id="7a744-103">Mitigation: PNG Frames in Icon Objects</span></span>

<span data-ttu-id="7a744-104">начиная с версии .NET Framework 4.6 метод <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> успешно преобразует значки с кадрами PNG в объекты <xref:System.Drawing.Bitmap> .</span><span class="sxs-lookup"><span data-stu-id="7a744-104">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="7a744-105">В приложениях, предназначенных для .NET Framework 4.5.2 и более ранних версий, метод <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> создает исключение <xref:System.ArgumentOutOfRangeException> , если объект <xref:System.Drawing.Icon> содержит кадры PNG.</span><span class="sxs-lookup"><span data-stu-id="7a744-105">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="7a744-106">Последствия</span><span class="sxs-lookup"><span data-stu-id="7a744-106">Impact</span></span>  

 <span data-ttu-id="7a744-107">Это изменение затрагивает приложения, которые компилируются повторно для платформы .NET Framework 4.6 и в которых реализуется специальная обработка исключения <xref:System.ArgumentOutOfRangeException> , создаваемого при наличии кадров PNG в объекте <xref:System.Drawing.Icon> .</span><span class="sxs-lookup"><span data-stu-id="7a744-107">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="7a744-108">При выполнении в .NET Framework 4.6 преобразование проходит успешно, исключение <xref:System.ArgumentOutOfRangeException> больше не создается, и поэтому обработчик исключений больше не вызывается.</span><span class="sxs-lookup"><span data-stu-id="7a744-108">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="7a744-109">Устранение рисков</span><span class="sxs-lookup"><span data-stu-id="7a744-109">Mitigation</span></span>  

 <span data-ttu-id="7a744-110">Если такое поведение нежелательно, можно сохранить прежнее поведение, добавив в раздел [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) файла app.config следующий элемент:</span><span class="sxs-lookup"><span data-stu-id="7a744-110">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="7a744-111">Если файл app.config уже содержит элемент `AppContextSwitchOverrides`, новое значение следует объединить с атрибутом `value` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7a744-111">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a><span data-ttu-id="7a744-112">См. также</span><span class="sxs-lookup"><span data-stu-id="7a744-112">See also</span></span>

- [<span data-ttu-id="7a744-113">Совместимость приложений</span><span class="sxs-lookup"><span data-stu-id="7a744-113">Application compatibility</span></span>](application-compatibility.md)
