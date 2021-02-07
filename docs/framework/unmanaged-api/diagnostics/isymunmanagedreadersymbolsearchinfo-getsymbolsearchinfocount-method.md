---
description: 'Дополнительные сведения о методе: ISymUnmanagedReaderSymbolSearchInfo:: GetSymbolSearchInfoCount'
title: Метод ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type:
- apiref
ms.openlocfilehash: b8bfa61397850c3f960fe30c0136e0a8b074cf1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763596"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="bea89-103">Метод ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount</span><span class="sxs-lookup"><span data-stu-id="bea89-103">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>

<span data-ttu-id="bea89-104">Возвращает число сведений о поиске символов.</span><span class="sxs-lookup"><span data-stu-id="bea89-104">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bea89-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bea89-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bea89-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bea89-106">Parameters</span></span>  

 `pcSearchInfo`  
 <span data-ttu-id="bea89-107">] out] указатель на объект `ULONG32` , который получает размер буфера, необходимый для хранения сведений о поиске.</span><span class="sxs-lookup"><span data-stu-id="bea89-107">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bea89-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="bea89-108">Return Value</span></span>  

 <span data-ttu-id="bea89-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="bea89-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bea89-110">Требования</span><span class="sxs-lookup"><span data-stu-id="bea89-110">Requirements</span></span>  

 <span data-ttu-id="bea89-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="bea89-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bea89-112">См. также</span><span class="sxs-lookup"><span data-stu-id="bea89-112">See also</span></span>

- [<span data-ttu-id="bea89-113">Интерфейс ISymUnmanagedReaderSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="bea89-113">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
