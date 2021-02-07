---
description: 'Дополнительные сведения о методе: ISymUnmanagedVariable:: GetAddressField2'
title: Метод ISymUnmanagedVariable::GetAddressField2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type:
- apiref
ms.openlocfilehash: 5d9bc226bfc462157e66b1d8fb43762945cdc016
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762972"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="4562b-103">Метод ISymUnmanagedVariable::GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="4562b-103">ISymUnmanagedVariable::GetAddressField2 Method</span></span>

<span data-ttu-id="4562b-104">Получает второе поле адреса для этой переменной.</span><span class="sxs-lookup"><span data-stu-id="4562b-104">Gets the second address field for this variable.</span></span> <span data-ttu-id="4562b-105">Его значение зависит от типа адреса.</span><span class="sxs-lookup"><span data-stu-id="4562b-105">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4562b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4562b-106">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4562b-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="4562b-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="4562b-108">заполняет Указатель на объект `ULONG32` , который получает второе поле адреса.</span><span class="sxs-lookup"><span data-stu-id="4562b-108">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4562b-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4562b-109">Return Value</span></span>  

 <span data-ttu-id="4562b-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="4562b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4562b-111">Требования</span><span class="sxs-lookup"><span data-stu-id="4562b-111">Requirements</span></span>  

 <span data-ttu-id="4562b-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="4562b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4562b-113">См. также</span><span class="sxs-lookup"><span data-stu-id="4562b-113">See also</span></span>

- [<span data-ttu-id="4562b-114">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="4562b-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="4562b-115">Метод GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="4562b-115">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="4562b-116">Метод GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="4562b-116">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="4562b-117">Метод GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="4562b-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
