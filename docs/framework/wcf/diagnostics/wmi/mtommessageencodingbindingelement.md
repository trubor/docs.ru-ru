---
description: 'Дополнительные сведения о: Мтоммессажеенкодингбиндинжелемент'
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: f06e3d7266c4f7e6f9b4639f7d82941cbabb5dd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803143"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="654f4-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="654f4-103">MtomMessageEncodingBindingElement</span></span>

<span data-ttu-id="654f4-104">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="654f4-104">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="654f4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="654f4-105">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="654f4-106">Методы</span><span class="sxs-lookup"><span data-stu-id="654f4-106">Methods</span></span>  

 <span data-ttu-id="654f4-107">Класс MtomMessageEncodingBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="654f4-107">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="654f4-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="654f4-108">Properties</span></span>  

 <span data-ttu-id="654f4-109">Класс MtomMessageEncodingBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="654f4-109">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="654f4-110">Кодирование</span><span class="sxs-lookup"><span data-stu-id="654f4-110">Encoding</span></span>  

 <span data-ttu-id="654f4-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="654f4-111">Data type: string</span></span>  
  
 <span data-ttu-id="654f4-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="654f4-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="654f4-113">Кодировка, используемая при отправке сообщений через привязку.</span><span class="sxs-lookup"><span data-stu-id="654f4-113">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="654f4-114">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="654f4-114">MaxReadPoolSize</span></span>  

 <span data-ttu-id="654f4-115">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="654f4-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="654f4-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="654f4-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="654f4-117">Целое число, определяющее количество сообщений, которые можно читать одновременно, не выделяя памяти для новых средств чтения.</span><span class="sxs-lookup"><span data-stu-id="654f4-117">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="654f4-118">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="654f4-118">MaxWritePoolSize</span></span>  

 <span data-ttu-id="654f4-119">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="654f4-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="654f4-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="654f4-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="654f4-121">Целое число, обозначающее количество сообщений, которые можно отправлять одновременно, не выделяя памяти для новых средств записи.</span><span class="sxs-lookup"><span data-stu-id="654f4-121">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="654f4-122">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="654f4-122">ReaderQuotas</span></span>  

 <span data-ttu-id="654f4-123">Тип данных: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="654f4-123">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="654f4-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="654f4-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="654f4-125">Квоты средств чтения.</span><span class="sxs-lookup"><span data-stu-id="654f4-125">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="654f4-126">Требования</span><span class="sxs-lookup"><span data-stu-id="654f4-126">Requirements</span></span>  
  
|<span data-ttu-id="654f4-127">MOF</span><span class="sxs-lookup"><span data-stu-id="654f4-127">MOF</span></span>|<span data-ttu-id="654f4-128">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="654f4-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="654f4-129">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="654f4-129">Namespace</span></span>|<span data-ttu-id="654f4-130">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="654f4-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="654f4-131">См. также</span><span class="sxs-lookup"><span data-stu-id="654f4-131">See also</span></span>

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
