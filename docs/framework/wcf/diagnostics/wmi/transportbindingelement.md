---
description: 'Дополнительные сведения о: TransportBindingElement'
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: de08feaf8abec3a0dfee97e92d68d5223cd0de44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757115"
---
# <a name="transportbindingelement"></a><span data-ttu-id="94bf4-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="94bf4-103">TransportBindingElement</span></span>

<span data-ttu-id="94bf4-104">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="94bf4-104">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94bf4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="94bf4-105">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="94bf4-106">Методы</span><span class="sxs-lookup"><span data-stu-id="94bf4-106">Methods</span></span>  

 <span data-ttu-id="94bf4-107">Класс TransportBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="94bf4-107">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="94bf4-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="94bf4-108">Properties</span></span>  

 <span data-ttu-id="94bf4-109">Класс TransportBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="94bf4-109">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="94bf4-110">ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="94bf4-110">ManualAddressing</span></span>  

 <span data-ttu-id="94bf4-111">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="94bf4-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="94bf4-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="94bf4-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94bf4-113">Логическое значение, указывающее, требуется ли пользователю контролировать адресацию сообщений.</span><span class="sxs-lookup"><span data-stu-id="94bf4-113">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="94bf4-114">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="94bf4-114">MaxBufferPoolSize</span></span>  

 <span data-ttu-id="94bf4-115">Тип данных: sint64</span><span class="sxs-lookup"><span data-stu-id="94bf4-115">Data type: sint64</span></span>  
  
 <span data-ttu-id="94bf4-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="94bf4-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94bf4-117">Максимальный размер буферного пула для этой привязки.</span><span class="sxs-lookup"><span data-stu-id="94bf4-117">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="94bf4-118">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="94bf4-118">MaxReceivedMessageSize</span></span>  

 <span data-ttu-id="94bf4-119">Тип данных: sint64</span><span class="sxs-lookup"><span data-stu-id="94bf4-119">Data type: sint64</span></span>  
  
 <span data-ttu-id="94bf4-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="94bf4-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94bf4-121">Максимально размер сообщения, обрабатываемого данной привязкой.</span><span class="sxs-lookup"><span data-stu-id="94bf4-121">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="94bf4-122">Схема</span><span class="sxs-lookup"><span data-stu-id="94bf4-122">Scheme</span></span>  

 <span data-ttu-id="94bf4-123">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="94bf4-123">Data type: string</span></span>  
  
 <span data-ttu-id="94bf4-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="94bf4-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94bf4-125">Схема универсального кода ресурса (URI) для транспорта.</span><span class="sxs-lookup"><span data-stu-id="94bf4-125">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94bf4-126">Требования</span><span class="sxs-lookup"><span data-stu-id="94bf4-126">Requirements</span></span>  
  
|<span data-ttu-id="94bf4-127">MOF</span><span class="sxs-lookup"><span data-stu-id="94bf4-127">MOF</span></span>|<span data-ttu-id="94bf4-128">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="94bf4-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="94bf4-129">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="94bf4-129">Namespace</span></span>|<span data-ttu-id="94bf4-130">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="94bf4-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94bf4-131">См. также</span><span class="sxs-lookup"><span data-stu-id="94bf4-131">See also</span></span>

- <xref:System.ServiceModel.Channels.TransportBindingElement>
