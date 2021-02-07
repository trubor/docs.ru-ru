---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter5:: OpenMapTokensToSourceSpans'
title: Метод ISymUnmanagedWriter5::OpenMapTokensToSourceSpans
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 1feeecaf943e3eed228ced2b0c968f3fe4b49f62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761516"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="9d2d5-103">Метод ISymUnmanagedWriter5::OpenMapTokensToSourceSpans</span><span class="sxs-lookup"><span data-stu-id="9d2d5-103">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>

<span data-ttu-id="9d2d5-104">Откройте Специальный раздел настраиваемых данных, чтобы выдать сведения о сопоставлении диапазона от токена к источнику в.</span><span class="sxs-lookup"><span data-stu-id="9d2d5-104">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="9d2d5-105">Открытие этого раздела, если метод уже открыт или наоборот, является ошибкой.</span><span class="sxs-lookup"><span data-stu-id="9d2d5-105">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d2d5-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9d2d5-106">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9d2d5-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9d2d5-107">Return Value</span></span>  

 <span data-ttu-id="9d2d5-108">Возвращает `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="9d2d5-108">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d2d5-109">Требования</span><span class="sxs-lookup"><span data-stu-id="9d2d5-109">Requirements</span></span>  

 <span data-ttu-id="9d2d5-110">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="9d2d5-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d2d5-111">См. также</span><span class="sxs-lookup"><span data-stu-id="9d2d5-111">See also</span></span>

- [<span data-ttu-id="9d2d5-112">Интерфейс ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="9d2d5-112">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
