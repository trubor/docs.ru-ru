---
description: 'Дополнительные сведения: создание классов типов данных из XML'
title: Формирование классов типов данных из XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: c79550b1e4804426267aef33860bc49d5d3b5efa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632143"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="3a089-103">Формирование классов типов данных из XML</span><span class="sxs-lookup"><span data-stu-id="3a089-103">Generating Data Type Classes from XML</span></span>

<span data-ttu-id="3a089-104">Платформа .NET Framework 4,5 включает новую функцию для создания классов типов данных из XML.</span><span class="sxs-lookup"><span data-stu-id="3a089-104">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="3a089-105">В этом разделе описывается автоматическое создание типов данных для RSS-канала блога .NET.</span><span class="sxs-lookup"><span data-stu-id="3a089-105">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="3a089-106">Получение XML из RSS-канала блога .NET</span><span class="sxs-lookup"><span data-stu-id="3a089-106">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="3a089-107">В Internet Explorer перейдите к RSS- [каналу блога в блоге .NET](https://devblogs.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="3a089-107">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="3a089-108">Щелкните страницу правой кнопкой мыши и выберите пункт **Просмотр источника**.</span><span class="sxs-lookup"><span data-stu-id="3a089-108">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="3a089-109">Скопируйте текст веб-канала, нажав клавиши **CTRL + A** , чтобы выделить весь текст, и **CTRL + C** для копирования.</span><span class="sxs-lookup"><span data-stu-id="3a089-109">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="3a089-110">Создание типов данных</span><span class="sxs-lookup"><span data-stu-id="3a089-110">Creating the data types</span></span>  
  
1. <span data-ttu-id="3a089-111">Откройте файл кода, в котором будет использоваться прокси.</span><span class="sxs-lookup"><span data-stu-id="3a089-111">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="3a089-112">Этот файл должен быть частью проекта платформа .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="3a089-112">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="3a089-113">Поместите курсор в такое место в файле, чтобы он был вне пределов описанных в файле классов.</span><span class="sxs-lookup"><span data-stu-id="3a089-113">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="3a089-114">Выберите **Правка**, **Специальная вставка**, **Вставить XML как классы**.</span><span class="sxs-lookup"><span data-stu-id="3a089-114">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="3a089-115">Классы с именами,,, `link` `rss` `rssChannel` `rssChannelImage` `rssChannelItem` и `rssChannelItemGuid` создаются с необходимыми элементами для доступа к элементам RSS-канала.</span><span class="sxs-lookup"><span data-stu-id="3a089-115">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="3a089-116">Использование созданных классов</span><span class="sxs-lookup"><span data-stu-id="3a089-116">Using the generated classes</span></span>  
  
1. <span data-ttu-id="3a089-117">После создания классов их можно использовать в коде так же, как и любые другие классы.</span><span class="sxs-lookup"><span data-stu-id="3a089-117">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="3a089-118">В следующем примере кода показана инициализация нового экземпляра класса `rssChannelImage`.</span><span class="sxs-lookup"><span data-stu-id="3a089-118">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
