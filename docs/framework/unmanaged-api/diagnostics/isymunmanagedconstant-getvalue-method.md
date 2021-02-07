---
description: 'Дополнительные сведения о методе: ISymUnmanagedConstant:: GetValue'
title: Метод ISymUnmanagedConstant::GetValue
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
ms.openlocfilehash: 05818028deb804bf2a2426285b5185b01776199d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689694"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="1aa95-103">Метод ISymUnmanagedConstant::GetValue</span><span class="sxs-lookup"><span data-stu-id="1aa95-103">ISymUnmanagedConstant::GetValue Method</span></span>

<span data-ttu-id="1aa95-104"> Возвращает значение константы.</span><span class="sxs-lookup"><span data-stu-id="1aa95-104">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aa95-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1aa95-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1aa95-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1aa95-106">Parameters</span></span>  

 `pValue`  
 <span data-ttu-id="1aa95-107">заполняет Указатель на переменную, которая получает значение.</span><span class="sxs-lookup"><span data-stu-id="1aa95-107">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1aa95-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1aa95-108">Return Value</span></span>  

 <span data-ttu-id="1aa95-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="1aa95-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aa95-110">Требования</span><span class="sxs-lookup"><span data-stu-id="1aa95-110">Requirements</span></span>  

 <span data-ttu-id="1aa95-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="1aa95-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa95-112">См. также</span><span class="sxs-lookup"><span data-stu-id="1aa95-112">See also</span></span>

- [<span data-ttu-id="1aa95-113">Интерфейс ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="1aa95-113">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="1aa95-114">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="1aa95-114">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="1aa95-115">Метод GetSignature</span><span class="sxs-lookup"><span data-stu-id="1aa95-115">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
