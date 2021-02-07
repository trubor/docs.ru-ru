---
description: 'Дополнительные сведения о методе: ISymUnmanagedDocument:: Финдклосестлине'
title: Метод ISymUnmanagedDocument::FindClosestLine
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
ms.openlocfilehash: 0409a5cc29bf148a49a5267d34662f763fc302d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737835"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="226b0-103">Метод ISymUnmanagedDocument::FindClosestLine</span><span class="sxs-lookup"><span data-stu-id="226b0-103">ISymUnmanagedDocument::FindClosestLine Method</span></span>

<span data-ttu-id="226b0-104">Возвращает ближайшую строку, которая является точкой последовательности, с учетом строки в этом документе, которая может быть или не являться точкой последовательности.</span><span class="sxs-lookup"><span data-stu-id="226b0-104">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="226b0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="226b0-105">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="226b0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="226b0-106">Parameters</span></span>  

 `line`  
 <span data-ttu-id="226b0-107">окне Строка в этом документе.</span><span class="sxs-lookup"><span data-stu-id="226b0-107">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="226b0-108">заполняет Указатель на переменную, которая получает строку.</span><span class="sxs-lookup"><span data-stu-id="226b0-108">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="226b0-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="226b0-109">Return Value</span></span>  

 <span data-ttu-id="226b0-110">S_OK, если метод выполнен. в противном случае — код ошибки.</span><span class="sxs-lookup"><span data-stu-id="226b0-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226b0-111">См. также</span><span class="sxs-lookup"><span data-stu-id="226b0-111">See also</span></span>

- [<span data-ttu-id="226b0-112">Интерфейс ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="226b0-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
