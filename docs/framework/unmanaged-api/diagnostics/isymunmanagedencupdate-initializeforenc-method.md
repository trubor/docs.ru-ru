---
description: 'Дополнительные сведения о методе: ISymUnmanagedENCUpdate:: InitializeForEnc'
title: Метод ISymUnmanagedENCUpdate::InitializeForEnc
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.InitializeForEnc
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc
helpviewer_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc method [.NET Framework debugging]
- InitializeForEnc method [.NET Framework debugging]
ms.assetid: 796b2154-b53c-4d07-9e67-80fd6064725a
topic_type:
- apiref
ms.openlocfilehash: 2b70554cc565f025dcf35e2a84523a5f9a6130f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710105"
---
# <a name="isymunmanagedencupdateinitializeforenc-method"></a><span data-ttu-id="fedd5-103">Метод ISymUnmanagedENCUpdate::InitializeForEnc</span><span class="sxs-lookup"><span data-stu-id="fedd5-103">ISymUnmanagedENCUpdate::InitializeForEnc Method</span></span>

<span data-ttu-id="fedd5-104">Позволяет вычислять границы методов перед первым вызовом метода [ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fedd5-104">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fedd5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fedd5-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForEnc();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fedd5-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fedd5-106">Return Value</span></span>  

 <span data-ttu-id="fedd5-107">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="fedd5-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fedd5-108">Требования</span><span class="sxs-lookup"><span data-stu-id="fedd5-108">Requirements</span></span>  

 <span data-ttu-id="fedd5-109">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="fedd5-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fedd5-110">См. также</span><span class="sxs-lookup"><span data-stu-id="fedd5-110">See also</span></span>

- [<span data-ttu-id="fedd5-111">Интерфейс ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="fedd5-111">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
