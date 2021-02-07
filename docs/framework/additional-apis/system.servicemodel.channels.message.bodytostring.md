---
description: Дополнительные сведения о методе Message. Бодитостринг
title: Метод Message. Бодитостринг (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: babcd881d191ff46b98e9999c4ff04166479a68d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699380"
---
# <a name="messagebodytostring-method"></a><span data-ttu-id="bbfe4-103">Метод Message. Бодитостринг</span><span class="sxs-lookup"><span data-stu-id="bbfe4-103">Message.BodyToString Method</span></span>

<span data-ttu-id="bbfe4-104">Преобразует текст сообщения в строку путем вызова <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> метода.</span><span class="sxs-lookup"><span data-stu-id="bbfe4-104">Converts the message body into a string by calling the <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a><span data-ttu-id="bbfe4-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="bbfe4-105">Parameters</span></span>

- <span data-ttu-id="bbfe4-106">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="bbfe4-106">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="bbfe4-107">Модуль записи, используемый для преобразования тела сообщения в строку.</span><span class="sxs-lookup"><span data-stu-id="bbfe4-107">The writer that is used to convert the message body to a string.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbfe4-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="bbfe4-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="bbfe4-109">`Message.BodyToString`Метод является внутренним и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="bbfe4-109">The `Message.BodyToString` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="bbfe4-110">Корпорация Майкрософт не поддерживает использование этого метода в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="bbfe4-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="bbfe4-111">Требования</span><span class="sxs-lookup"><span data-stu-id="bbfe4-111">Requirements</span></span>

<span data-ttu-id="bbfe4-112">**Пространство имен:** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="bbfe4-112">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="bbfe4-113">**Сборка:** System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="bbfe4-113">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="bbfe4-114">**Платформа .NET Framework версии:** Доступно с 3,0.</span><span class="sxs-lookup"><span data-stu-id="bbfe4-114">**.NET Framework versions:** Available since 3.0.</span></span>
