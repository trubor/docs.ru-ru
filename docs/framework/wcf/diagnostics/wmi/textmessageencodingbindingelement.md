---
description: 'Дополнительные сведения о: Текстмессажеенкодингбиндинжелемент'
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 9848f1660642f92c4bce3542fbd404f463b8c84d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757349"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="5c495-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="5c495-103">TextMessageEncodingBindingElement</span></span>

<span data-ttu-id="5c495-104">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="5c495-104">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c495-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5c495-105">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5c495-106">Методы</span><span class="sxs-lookup"><span data-stu-id="5c495-106">Methods</span></span>  

 <span data-ttu-id="5c495-107">Класс TextMessageEncodingBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="5c495-107">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5c495-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="5c495-108">Properties</span></span>  

 <span data-ttu-id="5c495-109">Класс TextMessageEncodingBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="5c495-109">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="5c495-110">Кодирование</span><span class="sxs-lookup"><span data-stu-id="5c495-110">Encoding</span></span>  

 <span data-ttu-id="5c495-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="5c495-111">Data type: string</span></span>  
  
 <span data-ttu-id="5c495-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5c495-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5c495-113">Кодировка, используемая при отправке сообщений через привязку.</span><span class="sxs-lookup"><span data-stu-id="5c495-113">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="5c495-114">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="5c495-114">MaxReadPoolSize</span></span>  

 <span data-ttu-id="5c495-115">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="5c495-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="5c495-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5c495-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5c495-117">Целое число, определяющее количество сообщений, которые можно читать одновременно, не выделяя памяти для новых средств чтения.</span><span class="sxs-lookup"><span data-stu-id="5c495-117">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="5c495-118">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="5c495-118">MaxWritePoolSize</span></span>  

 <span data-ttu-id="5c495-119">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="5c495-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="5c495-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5c495-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5c495-121">Целое число, обозначающее количество сообщений, которые можно отправлять одновременно, не выделяя памяти для новых средств записи.</span><span class="sxs-lookup"><span data-stu-id="5c495-121">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="5c495-122">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="5c495-122">ReaderQuotas</span></span>  

 <span data-ttu-id="5c495-123">Тип данных: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="5c495-123">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="5c495-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="5c495-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5c495-125">Квоты средств чтения.</span><span class="sxs-lookup"><span data-stu-id="5c495-125">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c495-126">Требования</span><span class="sxs-lookup"><span data-stu-id="5c495-126">Requirements</span></span>  
  
|<span data-ttu-id="5c495-127">MOF</span><span class="sxs-lookup"><span data-stu-id="5c495-127">MOF</span></span>|<span data-ttu-id="5c495-128">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5c495-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5c495-129">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="5c495-129">Namespace</span></span>|<span data-ttu-id="5c495-130">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="5c495-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c495-131">См. также</span><span class="sxs-lookup"><span data-stu-id="5c495-131">See also</span></span>

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
