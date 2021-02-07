---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: Клосенамеспаце'
title: Метод ISymUnmanagedWriter::CloseNamespace
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type:
- apiref
ms.openlocfilehash: c552d8bc86ab2bbd93918fdd6be3f880b3d83178
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762569"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="9f258-103">Метод ISymUnmanagedWriter::CloseNamespace</span><span class="sxs-lookup"><span data-stu-id="9f258-103">ISymUnmanagedWriter::CloseNamespace Method</span></span>

<span data-ttu-id="9f258-104">Закрывает Последнее открытое пространство имен.</span><span class="sxs-lookup"><span data-stu-id="9f258-104">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f258-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9f258-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9f258-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9f258-106">Return Value</span></span>  

 <span data-ttu-id="9f258-107">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="9f258-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f258-108">Требования</span><span class="sxs-lookup"><span data-stu-id="9f258-108">Requirements</span></span>  

 <span data-ttu-id="9f258-109">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="9f258-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f258-110">См. также</span><span class="sxs-lookup"><span data-stu-id="9f258-110">See also</span></span>

- [<span data-ttu-id="9f258-111">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="9f258-111">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="9f258-112">Метод OpenNamespace</span><span class="sxs-lookup"><span data-stu-id="9f258-112">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)
