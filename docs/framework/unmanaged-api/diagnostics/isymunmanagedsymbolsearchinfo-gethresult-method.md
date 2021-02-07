---
description: 'Дополнительные сведения о методе: Исимунманажедсимболсеарчинфо:: не HRESULT'
title: Метод ISymUnmanagedSymbolSearchInfo::GetHRESULT
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
ms.openlocfilehash: 5d351d84ba4e91ccb9acb531e77407a2d1caceec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763115"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="1d84e-103">Метод ISymUnmanagedSymbolSearchInfo::GetHRESULT</span><span class="sxs-lookup"><span data-stu-id="1d84e-103">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>

<span data-ttu-id="1d84e-104">Возвращает значение HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1d84e-104">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d84e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1d84e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d84e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1d84e-106">Parameters</span></span>  

 `phr`  
 <span data-ttu-id="1d84e-107">заполняет Указатель на значение HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1d84e-107">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d84e-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1d84e-108">Return Value</span></span>  

 <span data-ttu-id="1d84e-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="1d84e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d84e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="1d84e-110">Requirements</span></span>  

 <span data-ttu-id="1d84e-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="1d84e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d84e-112">См. также</span><span class="sxs-lookup"><span data-stu-id="1d84e-112">See also</span></span>

- [<span data-ttu-id="1d84e-113">Интерфейс ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="1d84e-113">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
