---
description: 'Дополнительные сведения о методе: ISymUnmanagedENCUpdate:: Getlocalvariables-'
title: Метод ISymUnmanagedENCUpdate::GetLocalVariables
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
ms.openlocfilehash: bc034603dd6a09ea78dad789e11ea951d65e839b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721467"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="69e4f-103">Метод ISymUnmanagedENCUpdate::GetLocalVariables</span><span class="sxs-lookup"><span data-stu-id="69e4f-103">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>

<span data-ttu-id="69e4f-104">Возвращает локальные переменные.</span><span class="sxs-lookup"><span data-stu-id="69e4f-104">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69e4f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="69e4f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69e4f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="69e4f-106">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="69e4f-107">окне Маркер метаданных метода.</span><span class="sxs-lookup"><span data-stu-id="69e4f-107">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="69e4f-108">окне Значение типа `ULONG` , указывающее размер `rgLocals` параметра.</span><span class="sxs-lookup"><span data-stu-id="69e4f-108">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="69e4f-109">заполняет Возвращаемый массив экземпляров [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="69e4f-109">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="69e4f-110">заполняет Указатель на объект `ULONG` , который получает размер `rgLocals` буфера, необходимого для хранения локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="69e4f-110">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69e4f-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="69e4f-111">Return Value</span></span>  

 <span data-ttu-id="69e4f-112">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="69e4f-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69e4f-113">Требования</span><span class="sxs-lookup"><span data-stu-id="69e4f-113">Requirements</span></span>  

 <span data-ttu-id="69e4f-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="69e4f-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e4f-115">См. также</span><span class="sxs-lookup"><span data-stu-id="69e4f-115">See also</span></span>

- [<span data-ttu-id="69e4f-116">Интерфейс ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="69e4f-116">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
