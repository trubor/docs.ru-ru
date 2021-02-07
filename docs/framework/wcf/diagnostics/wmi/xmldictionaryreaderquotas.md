---
description: 'Дополнительные сведения о: XmlDictionaryReaderQuotas'
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: d1450051e7107e9b92f848d26e6b182bfd2f2340
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756868"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="1ef9b-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="1ef9b-103">XmlDictionaryReaderQuotas</span></span>

<span data-ttu-id="1ef9b-104">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="1ef9b-104">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef9b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1ef9b-105">Syntax</span></span>  
  
```csharp
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1ef9b-106">Методы</span><span class="sxs-lookup"><span data-stu-id="1ef9b-106">Methods</span></span>  

 <span data-ttu-id="1ef9b-107">Класс XmlDictionaryReaderQuotas не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="1ef9b-107">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1ef9b-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="1ef9b-108">Properties</span></span>  

 <span data-ttu-id="1ef9b-109">Класс XmlDictionaryReaderQuotas имеет следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="1ef9b-109">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="1ef9b-110">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="1ef9b-110">MaxArrayLength</span></span>  

 <span data-ttu-id="1ef9b-111">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="1ef9b-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="1ef9b-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1ef9b-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ef9b-113">Максимально допустимая длина массива.</span><span class="sxs-lookup"><span data-stu-id="1ef9b-113">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="1ef9b-114">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="1ef9b-114">MaxBytesPerRead</span></span>  

 <span data-ttu-id="1ef9b-115">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="1ef9b-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="1ef9b-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1ef9b-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ef9b-117">Максимально допустимое число байтов, возвращаемых для каждой операции чтения.</span><span class="sxs-lookup"><span data-stu-id="1ef9b-117">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="1ef9b-118">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="1ef9b-118">MaxDepth</span></span>  

 <span data-ttu-id="1ef9b-119">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="1ef9b-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="1ef9b-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1ef9b-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ef9b-121">Максимальная глубина вложенного узла для каждого чтения.</span><span class="sxs-lookup"><span data-stu-id="1ef9b-121">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="1ef9b-122">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="1ef9b-122">MaxNameTableCharCount</span></span>  

 <span data-ttu-id="1ef9b-123">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="1ef9b-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="1ef9b-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1ef9b-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ef9b-125">Максимально допустимое количество символов в имени таблицы.</span><span class="sxs-lookup"><span data-stu-id="1ef9b-125">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="1ef9b-126">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="1ef9b-126">MaxStringContentLength</span></span>  

 <span data-ttu-id="1ef9b-127">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="1ef9b-127">Data type: sint32</span></span>  
  
 <span data-ttu-id="1ef9b-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="1ef9b-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ef9b-129">Максимальное допустимое число символов в содержимом элемента XML.</span><span class="sxs-lookup"><span data-stu-id="1ef9b-129">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ef9b-130">Требования</span><span class="sxs-lookup"><span data-stu-id="1ef9b-130">Requirements</span></span>  
  
|<span data-ttu-id="1ef9b-131">MOF</span><span class="sxs-lookup"><span data-stu-id="1ef9b-131">MOF</span></span>|<span data-ttu-id="1ef9b-132">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1ef9b-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1ef9b-133">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="1ef9b-133">Namespace</span></span>|<span data-ttu-id="1ef9b-134">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="1ef9b-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ef9b-135">См. также</span><span class="sxs-lookup"><span data-stu-id="1ef9b-135">See also</span></span>

- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
