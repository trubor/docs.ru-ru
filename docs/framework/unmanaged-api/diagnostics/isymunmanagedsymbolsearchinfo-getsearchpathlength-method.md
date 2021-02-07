---
description: 'Дополнительные сведения о методе: Исимунманажедсимболсеарчинфо:: Жетсеарчпасленгс'
title: Метод ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
ms.openlocfilehash: 3d5faf9d972881ff9c1eaf71bcaa6f68da46dae6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763024"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="44966-103">Метод ISymUnmanagedSymbolSearchInfo::GetSearchPathLength</span><span class="sxs-lookup"><span data-stu-id="44966-103">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>

<span data-ttu-id="44966-104">Возвращает длину пути поиска.</span><span class="sxs-lookup"><span data-stu-id="44966-104">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44966-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="44966-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44966-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="44966-106">Parameters</span></span>  

 `pcchPath`  
 <span data-ttu-id="44966-107">заполняет Указатель на объект `ULONG32` , который получает размер буфера (в символах), необходимый для хранения пути поиска.</span><span class="sxs-lookup"><span data-stu-id="44966-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44966-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="44966-108">Return Value</span></span>  

 <span data-ttu-id="44966-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="44966-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44966-110">Требования</span><span class="sxs-lookup"><span data-stu-id="44966-110">Requirements</span></span>  

 <span data-ttu-id="44966-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="44966-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44966-112">См. также</span><span class="sxs-lookup"><span data-stu-id="44966-112">See also</span></span>

- [<span data-ttu-id="44966-113">Интерфейс ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="44966-113">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
