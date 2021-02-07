---
description: 'Дополнительные сведения о методе: ISymUnmanagedReaderSymbolSearchInfo:: Жетсимболсеарчинфо'
title: Метод ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type:
- apiref
ms.openlocfilehash: e14f78d6736684205b3f86150ce1fbb44a8112b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763609"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="6e2dc-103">Метод ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="6e2dc-103">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>

<span data-ttu-id="6e2dc-104">Возвращает сведения о поиске символов.</span><span class="sxs-lookup"><span data-stu-id="6e2dc-104">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e2dc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6e2dc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e2dc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6e2dc-106">Parameters</span></span>  

 `cSearchInfo`  
 <span data-ttu-id="6e2dc-107">окне Значение типа `ULONG32` , указывающее размер `rgpSearchInfo` .</span><span class="sxs-lookup"><span data-stu-id="6e2dc-107">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="6e2dc-108">заполняет Указатель на объект `ULONG32` , который получает размер буфера, необходимого для хранения сведений о поиске.</span><span class="sxs-lookup"><span data-stu-id="6e2dc-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="6e2dc-109">заполняет Указатель, которому присваивается возвращаемый интерфейс [исимунманажедсимболсеарчинфо](isymunmanagedsymbolsearchinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6e2dc-109">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e2dc-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6e2dc-110">Return Value</span></span>  

 <span data-ttu-id="6e2dc-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="6e2dc-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e2dc-112">Требования</span><span class="sxs-lookup"><span data-stu-id="6e2dc-112">Requirements</span></span>  

 <span data-ttu-id="6e2dc-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="6e2dc-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e2dc-114">См. также</span><span class="sxs-lookup"><span data-stu-id="6e2dc-114">See also</span></span>

- [<span data-ttu-id="6e2dc-115">Интерфейс ISymUnmanagedReaderSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="6e2dc-115">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
