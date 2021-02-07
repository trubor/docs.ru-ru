---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedDocument'
title: Интерфейс ISymUnmanagedDocument
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
ms.openlocfilehash: cd1907e570dd15ebcac3ee12aa09c626c9bb7787
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710144"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="84b6a-103">Интерфейс ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="84b6a-103">ISymUnmanagedDocument Interface</span></span>

<span data-ttu-id="84b6a-104">Представляет документ, на который ссылается хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="84b6a-104">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="84b6a-105">Документ определяется по универсальному указателю ресурсов (URL-адрес) и GUID типа документа.</span><span class="sxs-lookup"><span data-stu-id="84b6a-105">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="84b6a-106">Документ можно разместить независимо от того, как он хранится, используя URL-адрес и GUID типа документа.</span><span class="sxs-lookup"><span data-stu-id="84b6a-106">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="84b6a-107">Вы можете сохранить источник документа в хранилище символов и получить его через этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="84b6a-107">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84b6a-108">Методы</span><span class="sxs-lookup"><span data-stu-id="84b6a-108">Methods</span></span>  
  
|<span data-ttu-id="84b6a-109">Метод</span><span class="sxs-lookup"><span data-stu-id="84b6a-109">Method</span></span>|<span data-ttu-id="84b6a-110">Описание</span><span class="sxs-lookup"><span data-stu-id="84b6a-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="84b6a-111">Метод FindClosestLine</span><span class="sxs-lookup"><span data-stu-id="84b6a-111">FindClosestLine Method</span></span>](isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="84b6a-112">Возвращает ближайшую строку, которая является точкой последовательности, с учетом строки в этом документе, которая может быть или не являться точкой последовательности.</span><span class="sxs-lookup"><span data-stu-id="84b6a-112">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="84b6a-113">Метод GetCheckSum</span><span class="sxs-lookup"><span data-stu-id="84b6a-113">GetCheckSum Method</span></span>](isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="84b6a-114">Возвращает контрольную сумму.</span><span class="sxs-lookup"><span data-stu-id="84b6a-114">Gets the checksum.</span></span>|  
|[<span data-ttu-id="84b6a-115">Метод GetCheckSumAlgorithmId</span><span class="sxs-lookup"><span data-stu-id="84b6a-115">GetCheckSumAlgorithmId Method</span></span>](isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="84b6a-116">Возвращает идентификатор алгоритма контрольной суммы или возвращает идентификатор GUID всех нулей, если контрольная сумма отсутствует.</span><span class="sxs-lookup"><span data-stu-id="84b6a-116">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="84b6a-117">Метод GetDocumentType</span><span class="sxs-lookup"><span data-stu-id="84b6a-117">GetDocumentType Method</span></span>](isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="84b6a-118">Возвращает тип документа этого документа.</span><span class="sxs-lookup"><span data-stu-id="84b6a-118">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="84b6a-119">Метод GetLanguage</span><span class="sxs-lookup"><span data-stu-id="84b6a-119">GetLanguage Method</span></span>](isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="84b6a-120">Возвращает идентификатор языка этого документа.</span><span class="sxs-lookup"><span data-stu-id="84b6a-120">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="84b6a-121">Метод GetLanguageVendor</span><span class="sxs-lookup"><span data-stu-id="84b6a-121">GetLanguageVendor Method</span></span>](isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="84b6a-122">Получает поставщика языка этого документа.</span><span class="sxs-lookup"><span data-stu-id="84b6a-122">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="84b6a-123">Метод GetSourceLength</span><span class="sxs-lookup"><span data-stu-id="84b6a-123">GetSourceLength Method</span></span>](isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="84b6a-124">Возвращает длину внедренного источника в байтах.</span><span class="sxs-lookup"><span data-stu-id="84b6a-124">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="84b6a-125">Метод GetSourceRange</span><span class="sxs-lookup"><span data-stu-id="84b6a-125">GetSourceRange Method</span></span>](isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="84b6a-126">Возвращает указанный диапазон внедренного источника в заданный буфер.</span><span class="sxs-lookup"><span data-stu-id="84b6a-126">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="84b6a-127">Метод GetURL</span><span class="sxs-lookup"><span data-stu-id="84b6a-127">GetURL Method</span></span>](isymunmanageddocument-geturl-method.md)|<span data-ttu-id="84b6a-128">Возвращает URL-адрес для этого документа.</span><span class="sxs-lookup"><span data-stu-id="84b6a-128">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="84b6a-129">Метод HasEmbeddedSource</span><span class="sxs-lookup"><span data-stu-id="84b6a-129">HasEmbeddedSource Method</span></span>](isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="84b6a-130">Возвращает `true` , если документ имеет исходный код, внедренный в отладочные символы; в противном случае возвращает `false` .</span><span class="sxs-lookup"><span data-stu-id="84b6a-130">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84b6a-131">См. также</span><span class="sxs-lookup"><span data-stu-id="84b6a-131">See also</span></span>

- [<span data-ttu-id="84b6a-132">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="84b6a-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
