---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter5:: MapTokenToSourceSpan'
title: Метод ISymUnmanagedWriter5::MapTokenToSourceSpan
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: b30d8051f5d2872488639ce999cccd4248af367f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761620"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="f844c-103">Метод ISymUnmanagedWriter5::MapTokenToSourceSpan</span><span class="sxs-lookup"><span data-stu-id="f844c-103">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>

<span data-ttu-id="f844c-104">Сопоставляет заданный токен метаданных с заданным диапазоном исходной строки в указанном исходном файле.</span><span class="sxs-lookup"><span data-stu-id="f844c-104">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="f844c-105">Должен вызываться между вызовами [метода OpenMapTokensToSourceSpans](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) и [метода CloseMapTokensToSourceSpans](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="f844c-105">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f844c-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f844c-106">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f844c-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="f844c-107">Parameters</span></span>  
  
|<span data-ttu-id="f844c-108">Параметр</span><span class="sxs-lookup"><span data-stu-id="f844c-108">Parameter</span></span>|<span data-ttu-id="f844c-109">Описание</span><span class="sxs-lookup"><span data-stu-id="f844c-109">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="f844c-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f844c-110">Return Value</span></span>  

 <span data-ttu-id="f844c-111">Возвращает `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="f844c-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f844c-112">Требования</span><span class="sxs-lookup"><span data-stu-id="f844c-112">Requirements</span></span>  

 <span data-ttu-id="f844c-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="f844c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f844c-114">См. также</span><span class="sxs-lookup"><span data-stu-id="f844c-114">See also</span></span>

- [<span data-ttu-id="f844c-115">Интерфейс ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="f844c-115">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
