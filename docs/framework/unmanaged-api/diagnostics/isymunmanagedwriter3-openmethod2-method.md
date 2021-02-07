---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter3:: OpenMethod2'
title: Метод ISymUnmanagedWriter3::OpenMethod2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: 7e76be03598599a6498ed45bc3799c6d6f21e088
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761698"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="b586e-103">Метод ISymUnmanagedWriter3::OpenMethod2</span><span class="sxs-lookup"><span data-stu-id="b586e-103">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>

<span data-ttu-id="b586e-104">Открывает метод и предоставляет его фактическое смещение раздела в изображении.</span><span class="sxs-lookup"><span data-stu-id="b586e-104">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b586e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b586e-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b586e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b586e-106">Parameters</span></span>  

 `method`  
 <span data-ttu-id="b586e-107">окне Токен метаданных для открываемого метода.</span><span class="sxs-lookup"><span data-stu-id="b586e-107">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="b586e-108">окне Смещение раздела в изображении.</span><span class="sxs-lookup"><span data-stu-id="b586e-108">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="b586e-109">окне Смещение в изображении.</span><span class="sxs-lookup"><span data-stu-id="b586e-109">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b586e-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b586e-110">Return Value</span></span>  

 <span data-ttu-id="b586e-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="b586e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b586e-112">Требования</span><span class="sxs-lookup"><span data-stu-id="b586e-112">Requirements</span></span>  

 <span data-ttu-id="b586e-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="b586e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b586e-114">См. также</span><span class="sxs-lookup"><span data-stu-id="b586e-114">See also</span></span>

- [<span data-ttu-id="b586e-115">Интерфейс ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="b586e-115">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="b586e-116">Метод OpenMethod</span><span class="sxs-lookup"><span data-stu-id="b586e-116">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
