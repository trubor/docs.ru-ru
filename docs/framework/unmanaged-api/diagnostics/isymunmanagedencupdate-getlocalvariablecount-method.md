---
description: 'Дополнительные сведения о методе: ISymUnmanagedENCUpdate:: Жетлокалвариаблекаунт'
title: Метод ISymUnmanagedENCUpdate::GetLocalVariableCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
ms.openlocfilehash: ab75ba0b0dda5722aebdbdc8b9a242cc90b0ac11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790156"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="0949b-103">Метод ISymUnmanagedENCUpdate::GetLocalVariableCount</span><span class="sxs-lookup"><span data-stu-id="0949b-103">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>

<span data-ttu-id="0949b-104">Возвращает число локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="0949b-104">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0949b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0949b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0949b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0949b-106">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="0949b-107">окне Маркер метаданных методов.</span><span class="sxs-lookup"><span data-stu-id="0949b-107">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="0949b-108">заполняет Указатель на объект `ULONG32` , который получает размер буфера (в символах), необходимого для хранения числа локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="0949b-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0949b-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0949b-109">Return Value</span></span>  

 <span data-ttu-id="0949b-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="0949b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0949b-111">Требования</span><span class="sxs-lookup"><span data-stu-id="0949b-111">Requirements</span></span>  

 <span data-ttu-id="0949b-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="0949b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0949b-113">См. также</span><span class="sxs-lookup"><span data-stu-id="0949b-113">See also</span></span>

- [<span data-ttu-id="0949b-114">Интерфейс ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="0949b-114">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
