---
description: 'Дополнительные сведения о: Бинаримессажеенкодингбиндинжелемент'
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: e2bc711416c61ca29a93fbf75e4e734137f2b4be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757882"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="c886a-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c886a-103">BinaryMessageEncodingBindingElement</span></span>

<span data-ttu-id="c886a-104">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c886a-104">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c886a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c886a-105">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c886a-106">Методы</span><span class="sxs-lookup"><span data-stu-id="c886a-106">Methods</span></span>  

 <span data-ttu-id="c886a-107">Класс BinaryMessageEncodingBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="c886a-107">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c886a-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="c886a-108">Properties</span></span>  

 <span data-ttu-id="c886a-109">Класс BinaryMessageEncodingBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="c886a-109">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="c886a-110">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="c886a-110">MaxReadPoolSize</span></span>  

 <span data-ttu-id="c886a-111">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="c886a-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="c886a-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c886a-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c886a-113">Целое число, определяющее количество сообщений, которые можно читать одновременно, не выделяя памяти для новых средств чтения.</span><span class="sxs-lookup"><span data-stu-id="c886a-113">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="c886a-114">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="c886a-114">MaxSessionSize</span></span>  

 <span data-ttu-id="c886a-115">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="c886a-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="c886a-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c886a-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c886a-117">Значение, указывающее максимальный размер буфера, используемого для кодирования (в байтах).</span><span class="sxs-lookup"><span data-stu-id="c886a-117">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="c886a-118">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="c886a-118">MaxWritePoolSize</span></span>  

 <span data-ttu-id="c886a-119">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="c886a-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="c886a-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c886a-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c886a-121">Целое число, обозначающее количество сообщений, которые можно отправлять одновременно, не выделяя памяти для новых средств записи.</span><span class="sxs-lookup"><span data-stu-id="c886a-121">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="c886a-122">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c886a-122">ReaderQuotas</span></span>  

 <span data-ttu-id="c886a-123">Тип данных: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c886a-123">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="c886a-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="c886a-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c886a-125">Квоты средств чтения.</span><span class="sxs-lookup"><span data-stu-id="c886a-125">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c886a-126">Требования</span><span class="sxs-lookup"><span data-stu-id="c886a-126">Requirements</span></span>  
  
|<span data-ttu-id="c886a-127">MOF</span><span class="sxs-lookup"><span data-stu-id="c886a-127">MOF</span></span>|<span data-ttu-id="c886a-128">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c886a-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c886a-129">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="c886a-129">Namespace</span></span>|<span data-ttu-id="c886a-130">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="c886a-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c886a-131">См. также</span><span class="sxs-lookup"><span data-stu-id="c886a-131">See also</span></span>

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
