---
description: 'Дополнительные сведения о методе: ISymUnmanagedVariable:: GetAddressField1'
title: Метод ISymUnmanagedVariable::GetAddressField1
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
ms.openlocfilehash: 1ff6862cef52ef8fcb449563198c2df1de356530
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762998"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="8beaa-103">Метод ISymUnmanagedVariable::GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="8beaa-103">ISymUnmanagedVariable::GetAddressField1 Method</span></span>

<span data-ttu-id="8beaa-104">Возвращает первое поле адреса для этой переменной.</span><span class="sxs-lookup"><span data-stu-id="8beaa-104">Gets the first address field for this variable.</span></span> <span data-ttu-id="8beaa-105">Его значение зависит от типа адреса.</span><span class="sxs-lookup"><span data-stu-id="8beaa-105">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8beaa-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8beaa-106">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8beaa-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="8beaa-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="8beaa-108">заполняет Указатель на объект `ULONG32` , который получает первое поле адреса.</span><span class="sxs-lookup"><span data-stu-id="8beaa-108">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8beaa-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8beaa-109">Return Value</span></span>  

 <span data-ttu-id="8beaa-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="8beaa-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8beaa-111">Требования</span><span class="sxs-lookup"><span data-stu-id="8beaa-111">Requirements</span></span>  

 <span data-ttu-id="8beaa-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="8beaa-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8beaa-113">См. также</span><span class="sxs-lookup"><span data-stu-id="8beaa-113">See also</span></span>

- [<span data-ttu-id="8beaa-114">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="8beaa-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="8beaa-115">Метод GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="8beaa-115">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="8beaa-116">Метод GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="8beaa-116">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="8beaa-117">Метод GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="8beaa-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
