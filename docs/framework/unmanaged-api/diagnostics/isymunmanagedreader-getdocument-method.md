---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: \ Document'
title: Метод ISymUnmanagedReader::GetDocument
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
ms.openlocfilehash: 7f2f31467cfd00de68737224a2c1af5b1e78efed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764103"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="ab04c-103">Метод ISymUnmanagedReader::GetDocument</span><span class="sxs-lookup"><span data-stu-id="ab04c-103">ISymUnmanagedReader::GetDocument Method</span></span>

<span data-ttu-id="ab04c-104">Находит документ.</span><span class="sxs-lookup"><span data-stu-id="ab04c-104">Finds a document.</span></span> <span data-ttu-id="ab04c-105">Язык документа, поставщик и тип являются необязательными.</span><span class="sxs-lookup"><span data-stu-id="ab04c-105">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab04c-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ab04c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab04c-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="ab04c-107">Parameters</span></span>  

 `url`  
 <span data-ttu-id="ab04c-108">окне URL-адрес, определяющий документ.</span><span class="sxs-lookup"><span data-stu-id="ab04c-108">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="ab04c-109">окне Язык документа.</span><span class="sxs-lookup"><span data-stu-id="ab04c-109">[in] The document language.</span></span> <span data-ttu-id="ab04c-110">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="ab04c-110">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="ab04c-111">окне Удостоверение поставщика для языка документа.</span><span class="sxs-lookup"><span data-stu-id="ab04c-111">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="ab04c-112">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="ab04c-112">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="ab04c-113">окне Тип документа.</span><span class="sxs-lookup"><span data-stu-id="ab04c-113">[in] The type of the document.</span></span> <span data-ttu-id="ab04c-114">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="ab04c-114">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ab04c-115">заполняет Указатель на возвращаемый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ab04c-115">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab04c-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ab04c-116">Return Value</span></span>  

 <span data-ttu-id="ab04c-117">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="ab04c-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab04c-118">Требования</span><span class="sxs-lookup"><span data-stu-id="ab04c-118">Requirements</span></span>  

 <span data-ttu-id="ab04c-119">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="ab04c-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab04c-120">См. также</span><span class="sxs-lookup"><span data-stu-id="ab04c-120">See also</span></span>

- [<span data-ttu-id="ab04c-121">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="ab04c-121">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
