---
description: 'Дополнительные сведения: привязка'
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 36887a9296bfafd0790105e7f4d513efc3009bf8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757791"
---
# <a name="binding"></a><span data-ttu-id="cc61d-103">Привязка</span><span class="sxs-lookup"><span data-stu-id="cc61d-103">Binding</span></span>

<span data-ttu-id="cc61d-104">wmi Binding</span><span class="sxs-lookup"><span data-stu-id="cc61d-104">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc61d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cc61d-105">Syntax</span></span>  
  
```csharp
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cc61d-106">Методы</span><span class="sxs-lookup"><span data-stu-id="cc61d-106">Methods</span></span>  

 <span data-ttu-id="cc61d-107">Класс Binding не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="cc61d-107">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cc61d-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="cc61d-108">Properties</span></span>  

 <span data-ttu-id="cc61d-109">Класс Binding имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="cc61d-109">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="cc61d-110">BindingElements</span><span class="sxs-lookup"><span data-stu-id="cc61d-110">BindingElements</span></span>  

 <span data-ttu-id="cc61d-111">Тип данных: массив BindingElement</span><span class="sxs-lookup"><span data-stu-id="cc61d-111">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="cc61d-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="cc61d-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cc61d-113">Коллекция элементов привязки, реализованных привязкой.</span><span class="sxs-lookup"><span data-stu-id="cc61d-113">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="cc61d-114">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="cc61d-114">CloseTimeout</span></span>  

 <span data-ttu-id="cc61d-115">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="cc61d-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="cc61d-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="cc61d-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cc61d-117">Интервал времени, предусмотренный для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="cc61d-117">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="cc61d-118">Имя</span><span class="sxs-lookup"><span data-stu-id="cc61d-118">Name</span></span>  

 <span data-ttu-id="cc61d-119">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="cc61d-119">Data type: string</span></span>  
  
 <span data-ttu-id="cc61d-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="cc61d-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cc61d-121">Имя привязки.</span><span class="sxs-lookup"><span data-stu-id="cc61d-121">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="cc61d-122">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="cc61d-122">Namespace</span></span>  

 <span data-ttu-id="cc61d-123">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="cc61d-123">Data type: string</span></span>  
  
 <span data-ttu-id="cc61d-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="cc61d-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cc61d-125">Пространство имен XML привязки.</span><span class="sxs-lookup"><span data-stu-id="cc61d-125">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="cc61d-126">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="cc61d-126">OpenTimeout</span></span>  

 <span data-ttu-id="cc61d-127">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="cc61d-127">Data type: datetime</span></span>  
  
 <span data-ttu-id="cc61d-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="cc61d-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cc61d-129">Интервал времени, предусмотренный для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="cc61d-129">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="cc61d-130">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="cc61d-130">ReceiveTimeout</span></span>  

 <span data-ttu-id="cc61d-131">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="cc61d-131">Data type: datetime</span></span>  
  
 <span data-ttu-id="cc61d-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="cc61d-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cc61d-133">Интервал времени, предусмотренный для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="cc61d-133">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="cc61d-134">Схема</span><span class="sxs-lookup"><span data-stu-id="cc61d-134">Scheme</span></span>  

 <span data-ttu-id="cc61d-135">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="cc61d-135">Data type: string</span></span>  
  
 <span data-ttu-id="cc61d-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="cc61d-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cc61d-137">Схема транспорта универсальных кодов ресурсов (URI), которая используется производствами каналов и прослушивателей, созданными привязкой.</span><span class="sxs-lookup"><span data-stu-id="cc61d-137">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="cc61d-138">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="cc61d-138">SendTimeout</span></span>  

 <span data-ttu-id="cc61d-139">Тип данных: datetime</span><span class="sxs-lookup"><span data-stu-id="cc61d-139">Data type: datetime</span></span>  
  
 <span data-ttu-id="cc61d-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="cc61d-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cc61d-141">Интервал времени, предусмотренный для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="cc61d-141">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc61d-142">Требования</span><span class="sxs-lookup"><span data-stu-id="cc61d-142">Requirements</span></span>  
  
|<span data-ttu-id="cc61d-143">MOF</span><span class="sxs-lookup"><span data-stu-id="cc61d-143">MOF</span></span>|<span data-ttu-id="cc61d-144">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cc61d-144">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cc61d-145">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="cc61d-145">Namespace</span></span>|<span data-ttu-id="cc61d-146">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="cc61d-146">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc61d-147">См. также</span><span class="sxs-lookup"><span data-stu-id="cc61d-147">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
