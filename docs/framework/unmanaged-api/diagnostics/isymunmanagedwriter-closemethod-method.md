---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: Клосемесод'
title: Метод ISymUnmanagedWriter::CloseMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
ms.openlocfilehash: 8d19de0827f94d52c92852b0d1f2b5567e109c15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762582"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="599a6-103">Метод ISymUnmanagedWriter::CloseMethod</span><span class="sxs-lookup"><span data-stu-id="599a6-103">ISymUnmanagedWriter::CloseMethod Method</span></span>

<span data-ttu-id="599a6-104">Закрывает текущий метод.</span><span class="sxs-lookup"><span data-stu-id="599a6-104">Closes the current method.</span></span> <span data-ttu-id="599a6-105">После закрытия метода в нем нельзя определять символы.</span><span class="sxs-lookup"><span data-stu-id="599a6-105">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="599a6-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="599a6-106">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="599a6-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="599a6-107">Return Value</span></span>  

 <span data-ttu-id="599a6-108">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="599a6-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="599a6-109">Требования</span><span class="sxs-lookup"><span data-stu-id="599a6-109">Requirements</span></span>  

 <span data-ttu-id="599a6-110">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="599a6-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="599a6-111">См. также</span><span class="sxs-lookup"><span data-stu-id="599a6-111">See also</span></span>

- [<span data-ttu-id="599a6-112">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="599a6-112">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="599a6-113">Метод OpenMethod</span><span class="sxs-lookup"><span data-stu-id="599a6-113">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
