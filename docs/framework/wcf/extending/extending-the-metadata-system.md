---
description: 'Дополнительные сведения: расширение системы метаданных'
title: Расширение системы метаданных
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: e8409e29f9dc604ccc6bf399497f3d48f3bcd8f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685560"
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="7059a-103">Расширение системы метаданных</span><span class="sxs-lookup"><span data-stu-id="7059a-103">Extending the Metadata System</span></span>

<span data-ttu-id="7059a-104">Система метаданных Windows Communication Foundation (WCF) — это группа классов и интерфейсов, представляющих метаданные, необходимые для реализации приложений на основе служб.</span><span class="sxs-lookup"><span data-stu-id="7059a-104">The Windows Communication Foundation (WCF) metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="7059a-105">Можно изменять или расширять классы, реализовывать и настраивать интерфейсы для экспорта и импорта пользовательских метаданных, например расширений языка WSDL или пользовательских утверждений WS-PolicyAttachments.</span><span class="sxs-lookup"><span data-stu-id="7059a-105">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7059a-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="7059a-106">In This Section</span></span>  

 [<span data-ttu-id="7059a-107">Экспорт пользовательских метаданных для расширения WCF</span><span class="sxs-lookup"><span data-stu-id="7059a-107">Exporting Custom Metadata for a WCF Extension</span></span>](exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="7059a-108">Содержит описание, как реализовать и использовать интерфейс <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> для внедрения в документы WSDL пользовательских утверждений политики.</span><span class="sxs-lookup"><span data-stu-id="7059a-108">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="7059a-109">Импорт пользовательских метаданных для расширения WCF</span><span class="sxs-lookup"><span data-stu-id="7059a-109">Importing Custom Metadata for a WCF Extension</span></span>](importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="7059a-110">Содержит описание, как реализовать и использовать интерфейс <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> для чтения пользовательских утверждений политики в документах WSDL и ответа на них.</span><span class="sxs-lookup"><span data-stu-id="7059a-110">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="7059a-111">Публикация и получение метаданных через пользовательскую привязку</span><span class="sxs-lookup"><span data-stu-id="7059a-111">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="7059a-112">Содержит описание обмена данными для пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="7059a-112">Describes how to exchange metadata over custom bindings.</span></span>
