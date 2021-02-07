---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: Close'
title: Метод ISymUnmanagedWriter::Close
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: 02f4d8d4a232240160ad5065947282f40af42f4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762634"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="f0299-103">Метод ISymUnmanagedWriter::Close</span><span class="sxs-lookup"><span data-stu-id="f0299-103">ISymUnmanagedWriter::Close Method</span></span>

<span data-ttu-id="f0299-104">Закрывает модуль записи символов после фиксации символов в хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="f0299-104">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0299-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f0299-105">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f0299-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f0299-106">Return Value</span></span>  

 <span data-ttu-id="f0299-107">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="f0299-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0299-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="f0299-108">Remarks</span></span>  

 <span data-ttu-id="f0299-109">После этого вызова средство записи символов станет недействительным для последующих обновлений.</span><span class="sxs-lookup"><span data-stu-id="f0299-109">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="f0299-110">Чтобы закрыть средство записи символов без фиксации символов, следует использовать метод [ISymUnmanagedWriter:: Abort](isymunmanagedwriter-abort-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f0299-110">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0299-111">Требования</span><span class="sxs-lookup"><span data-stu-id="f0299-111">Requirements</span></span>  

 <span data-ttu-id="f0299-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="f0299-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0299-113">См. также</span><span class="sxs-lookup"><span data-stu-id="f0299-113">See also</span></span>

- [<span data-ttu-id="f0299-114">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="f0299-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
