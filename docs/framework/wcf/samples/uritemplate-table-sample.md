---
description: Дополнительные сведения см. в примере таблицы UriTemplate
title: Пример таблицы UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: 505fb810c1543b3526955eccc2d5b2a5d041acb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685430"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="78ff0-103">Пример таблицы UriTemplate</span><span class="sxs-lookup"><span data-stu-id="78ff0-103">UriTemplate Table Sample</span></span>

<span data-ttu-id="78ff0-104">Класс <xref:System.UriTemplateTable> предоставляет структуру ассоциативной таблицы, подобную словарю, для работы с набором экземпляров `UriTemplate`.</span><span class="sxs-lookup"><span data-stu-id="78ff0-104">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="78ff0-105">Конкретные универсальные коды ресурса (URI) могут эффективно сравниваться со всеми шаблонами в таблице, после чего могут извлекаться данные, связанные с совпадающим шаблоном.</span><span class="sxs-lookup"><span data-stu-id="78ff0-105">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="78ff0-106">Данный пример демонстрирует следующие ключевые понятия, связанные с классом `UriTemplateTable`:</span><span class="sxs-lookup"><span data-stu-id="78ff0-106">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="78ff0-107">Синтаксис для создания экземпляров `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="78ff0-107">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="78ff0-108">Занесение в `UriTemplateTable` набора пар ключ/значение.</span><span class="sxs-lookup"><span data-stu-id="78ff0-108">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="78ff0-109">Сравнение потенциального универсального кода ресурса (URI) по таблице с использованием <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="78ff0-109">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="78ff0-110">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="78ff0-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="78ff0-111">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="78ff0-111">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="78ff0-112">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="78ff0-112">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="78ff0-113">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="78ff0-113">The samples may already be installed on your computer.</span></span> <span data-ttu-id="78ff0-114">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="78ff0-114">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="78ff0-115">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="78ff0-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="78ff0-116">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="78ff0-116">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="78ff0-117">См. также</span><span class="sxs-lookup"><span data-stu-id="78ff0-117">See also</span></span>

- [<span data-ttu-id="78ff0-118">Диспетчер таблицы UriTemplate</span><span class="sxs-lookup"><span data-stu-id="78ff0-118">UriTemplate Table Dispatcher</span></span>](uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="78ff0-119">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="78ff0-119">UriTemplate</span></span>](uritemplate-sample.md)
