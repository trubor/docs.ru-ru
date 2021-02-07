---
description: 'Дополнительные сведения о методе: ISymUnmanagedMethod:: Жетсекуенцепоинткаунт'
title: Метод ISymUnmanagedMethod::GetSequencePointCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
ms.openlocfilehash: 6e0341ddc151454de8764a47a92556ab1925bfa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710011"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="91a5e-103">Метод ISymUnmanagedMethod::GetSequencePointCount</span><span class="sxs-lookup"><span data-stu-id="91a5e-103">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>

<span data-ttu-id="91a5e-104">Возвращает число точек следования в этом методе.</span><span class="sxs-lookup"><span data-stu-id="91a5e-104">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a5e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="91a5e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91a5e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="91a5e-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="91a5e-107">заполняет Указатель на объект `ULONG32` , который получает размер буфера, необходимого для хранения точек следования.</span><span class="sxs-lookup"><span data-stu-id="91a5e-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91a5e-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="91a5e-108">Return Value</span></span>  

 <span data-ttu-id="91a5e-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="91a5e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91a5e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="91a5e-110">Requirements</span></span>  

 <span data-ttu-id="91a5e-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="91a5e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a5e-112">См. также</span><span class="sxs-lookup"><span data-stu-id="91a5e-112">See also</span></span>

- [<span data-ttu-id="91a5e-113">Интерфейс ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="91a5e-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
