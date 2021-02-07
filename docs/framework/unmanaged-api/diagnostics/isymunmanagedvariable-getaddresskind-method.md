---
description: 'Дополнительные сведения о методе: ISymUnmanagedVariable:: Жетаддресскинд'
title: Метод ISymUnmanagedVariable::GetAddressKind
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
ms.openlocfilehash: 4b090560335432ad39157fee987ce15728fece63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762855"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="8cb8b-103">Метод ISymUnmanagedVariable::GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="8cb8b-103">ISymUnmanagedVariable::GetAddressKind Method</span></span>

<span data-ttu-id="8cb8b-104">Возвращает тип адреса этой переменной.</span><span class="sxs-lookup"><span data-stu-id="8cb8b-104">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cb8b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8cb8b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cb8b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8cb8b-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="8cb8b-107">заполняет Указатель на объект `ULONG32` , который получает значение.</span><span class="sxs-lookup"><span data-stu-id="8cb8b-107">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="8cb8b-108">Возможные значения определяются в перечислении [корсимаддркинд](corsymaddrkind-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="8cb8b-108">The possible values are defined in the [CorSymAddrKind](corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cb8b-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8cb8b-109">Return Value</span></span>  

 <span data-ttu-id="8cb8b-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="8cb8b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cb8b-111">Требования</span><span class="sxs-lookup"><span data-stu-id="8cb8b-111">Requirements</span></span>  

 <span data-ttu-id="8cb8b-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="8cb8b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cb8b-113">См. также</span><span class="sxs-lookup"><span data-stu-id="8cb8b-113">See also</span></span>

- [<span data-ttu-id="8cb8b-114">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="8cb8b-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
