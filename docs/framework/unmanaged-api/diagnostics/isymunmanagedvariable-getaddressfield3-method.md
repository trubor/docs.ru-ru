---
description: 'Дополнительные сведения о методе: ISymUnmanagedVariable:: GetAddressField3'
title: Метод ISymUnmanagedVariable::GetAddressField3
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
ms.openlocfilehash: 286d8382857e941173c22a7aebe65adc22ab779b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762920"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="e17e1-103">Метод ISymUnmanagedVariable::GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="e17e1-103">ISymUnmanagedVariable::GetAddressField3 Method</span></span>

<span data-ttu-id="e17e1-104">Возвращает третье поле адреса для этой переменной.</span><span class="sxs-lookup"><span data-stu-id="e17e1-104">Gets the third address field for this variable.</span></span> <span data-ttu-id="e17e1-105">Его значение зависит от типа адреса.</span><span class="sxs-lookup"><span data-stu-id="e17e1-105">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e17e1-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e17e1-106">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e17e1-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="e17e1-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="e17e1-108">заполняет Указатель на объект `ULONG32` , который получает третье поле адреса.</span><span class="sxs-lookup"><span data-stu-id="e17e1-108">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e17e1-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e17e1-109">Return Value</span></span>  

 <span data-ttu-id="e17e1-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="e17e1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e17e1-111">Требования</span><span class="sxs-lookup"><span data-stu-id="e17e1-111">Requirements</span></span>  

 <span data-ttu-id="e17e1-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="e17e1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e17e1-113">См. также</span><span class="sxs-lookup"><span data-stu-id="e17e1-113">See also</span></span>

- [<span data-ttu-id="e17e1-114">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="e17e1-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="e17e1-115">Метод GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="e17e1-115">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="e17e1-116">Метод GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="e17e1-116">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="e17e1-117">Метод GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="e17e1-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
