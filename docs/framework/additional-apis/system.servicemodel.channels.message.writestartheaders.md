---
description: Дополнительные сведения о методе Message. Вритестарсеадерс
title: Метод Message. Вритестарсеадерс (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 20cadf5f1eecf6d8e02c5dc4597889abaef4ec36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699367"
---
# <a name="messagewritestartheaders-method"></a><span data-ttu-id="4a861-103">Метод Message. Вритестарсеадерс</span><span class="sxs-lookup"><span data-stu-id="4a861-103">Message.WriteStartHeaders Method</span></span>

<span data-ttu-id="4a861-104">Записывает начальный заголовок в XML-файл, вызвав <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="4a861-104">Writes the start header into an XML file by calling the <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a><span data-ttu-id="4a861-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="4a861-105">Parameters</span></span>

- <span data-ttu-id="4a861-106">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="4a861-106">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="4a861-107">Модуль записи, используемый для записи начального заголовка в XML-файл.</span><span class="sxs-lookup"><span data-stu-id="4a861-107">The writer that is used to write the start header into an XML file.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a861-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="4a861-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="4a861-109">`Message.WriteStartHeaders`Метод является внутренним и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="4a861-109">The `Message.WriteStartHeaders` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="4a861-110">Корпорация Майкрософт не поддерживает использование этого метода в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="4a861-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="4a861-111">Требования</span><span class="sxs-lookup"><span data-stu-id="4a861-111">Requirements</span></span>

<span data-ttu-id="4a861-112">**Пространство имен:** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="4a861-112">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="4a861-113">**Сборка:** System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="4a861-113">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="4a861-114">**Платформа .NET Framework версии:** Доступно с 3,0.</span><span class="sxs-lookup"><span data-stu-id="4a861-114">**.NET Framework versions:** Available since 3.0.</span></span>
