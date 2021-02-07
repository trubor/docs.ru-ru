---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter3:: Commit'
title: Метод ISymUnmanagedWriter3::Commit
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
ms.openlocfilehash: 308f5d3a16cf60a0e77a581a318d6fd6c398b3f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761763"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="f587c-103">Метод ISymUnmanagedWriter3::Commit</span><span class="sxs-lookup"><span data-stu-id="f587c-103">ISymUnmanagedWriter3::Commit Method</span></span>

<span data-ttu-id="f587c-104">Фиксирует изменения, записанные на данный момент в поток.</span><span class="sxs-lookup"><span data-stu-id="f587c-104">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f587c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f587c-105">Syntax</span></span>  
  
```cpp  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f587c-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f587c-106">Return Value</span></span>  

 <span data-ttu-id="f587c-107">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="f587c-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f587c-108">Требования</span><span class="sxs-lookup"><span data-stu-id="f587c-108">Requirements</span></span>  

 <span data-ttu-id="f587c-109">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="f587c-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f587c-110">См. также</span><span class="sxs-lookup"><span data-stu-id="f587c-110">See also</span></span>

- [<span data-ttu-id="f587c-111">Интерфейс ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="f587c-111">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
