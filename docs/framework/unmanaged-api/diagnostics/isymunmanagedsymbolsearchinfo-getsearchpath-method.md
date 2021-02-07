---
description: 'Дополнительные сведения о методе: Исимунманажедсимболсеарчинфо:: GetSearchPath'
title: Метод ISymUnmanagedSymbolSearchInfo::GetSearchPath
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type:
- apiref
ms.openlocfilehash: 2ae85733ccca8ac63fbca5d2556026221e5681bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763037"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="4d0d3-103">Метод ISymUnmanagedSymbolSearchInfo::GetSearchPath</span><span class="sxs-lookup"><span data-stu-id="4d0d3-103">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>

<span data-ttu-id="4d0d3-104">Возвращает путь поиска.</span><span class="sxs-lookup"><span data-stu-id="4d0d3-104">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d0d3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4d0d3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d0d3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4d0d3-106">Parameters</span></span>  

 `pcchPath`  
 <span data-ttu-id="4d0d3-107">заполняет Указатель на объект `ULONG32` , который получает размер буфера (в символах), необходимый для хранения пути поиска.</span><span class="sxs-lookup"><span data-stu-id="4d0d3-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d0d3-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4d0d3-108">Return Value</span></span>  

 <span data-ttu-id="4d0d3-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="4d0d3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d0d3-110">Требования</span><span class="sxs-lookup"><span data-stu-id="4d0d3-110">Requirements</span></span>  

 <span data-ttu-id="4d0d3-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="4d0d3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d0d3-112">См. также</span><span class="sxs-lookup"><span data-stu-id="4d0d3-112">See also</span></span>

- [<span data-ttu-id="4d0d3-113">Интерфейс ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="4d0d3-113">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
