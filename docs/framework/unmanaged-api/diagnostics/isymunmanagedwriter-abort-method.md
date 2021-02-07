---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: Abort'
title: Метод ISymUnmanagedWriter::Abort
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
ms.openlocfilehash: 312694bf2b667ea78bf5ddc993d0e2b71c85a8ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762686"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="baa91-103">Метод ISymUnmanagedWriter::Abort</span><span class="sxs-lookup"><span data-stu-id="baa91-103">ISymUnmanagedWriter::Abort Method</span></span>

<span data-ttu-id="baa91-104">Закрывает модуль записи символов без фиксации символов в хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="baa91-104">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="baa91-105">После этого вызова средство записи символов станет недействительным для последующих обновлений.</span><span class="sxs-lookup"><span data-stu-id="baa91-105">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="baa91-106">Чтобы зафиксировать символы и закрыть средство записи символов, используйте вместо этого метод [ISymUnmanagedWriter:: Close](isymunmanagedwriter-close-method.md) .</span><span class="sxs-lookup"><span data-stu-id="baa91-106">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baa91-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="baa91-107">Syntax</span></span>  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="baa91-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="baa91-108">Return Value</span></span>  

 <span data-ttu-id="baa91-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="baa91-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baa91-110">Требования</span><span class="sxs-lookup"><span data-stu-id="baa91-110">Requirements</span></span>  

 <span data-ttu-id="baa91-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="baa91-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa91-112">См. также</span><span class="sxs-lookup"><span data-stu-id="baa91-112">See also</span></span>

- [<span data-ttu-id="baa91-113">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="baa91-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
