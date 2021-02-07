---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter2::D efineConstant2'
title: Метод ISymUnmanagedWriter2::DefineConstant2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
ms.openlocfilehash: 9a0c444909055e18bdcd0b54fefbc8534ff8681e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761932"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="9d7ee-103">Метод ISymUnmanagedWriter2::DefineConstant2</span><span class="sxs-lookup"><span data-stu-id="9d7ee-103">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>

<span data-ttu-id="9d7ee-104">Определяет имя для постоянного значения.</span><span class="sxs-lookup"><span data-stu-id="9d7ee-104">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7ee-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9d7ee-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d7ee-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9d7ee-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="9d7ee-107">окне Имя константы.</span><span class="sxs-lookup"><span data-stu-id="9d7ee-107">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="9d7ee-108">окне Значение константы.</span><span class="sxs-lookup"><span data-stu-id="9d7ee-108">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="9d7ee-109">окне Маркер метаданных константы.</span><span class="sxs-lookup"><span data-stu-id="9d7ee-109">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d7ee-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9d7ee-110">Return Value</span></span>  

 <span data-ttu-id="9d7ee-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="9d7ee-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d7ee-112">Требования</span><span class="sxs-lookup"><span data-stu-id="9d7ee-112">Requirements</span></span>  

 <span data-ttu-id="9d7ee-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="9d7ee-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d7ee-114">См. также</span><span class="sxs-lookup"><span data-stu-id="9d7ee-114">See also</span></span>

- [<span data-ttu-id="9d7ee-115">Интерфейс ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="9d7ee-115">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="9d7ee-116">Метод DefineConstant</span><span class="sxs-lookup"><span data-stu-id="9d7ee-116">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)
