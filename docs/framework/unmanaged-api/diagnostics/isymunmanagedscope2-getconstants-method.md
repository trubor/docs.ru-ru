---
description: "Дополнительные сведения: метод ISymUnmanagedScope2:: ' Constant '"
title: Метод ISymUnmanagedScope2::GetConstants
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: 025bb9ddd0501f2309b2c0a3f7af20eb961604cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763219"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="3db70-103">Метод ISymUnmanagedScope2::GetConstants</span><span class="sxs-lookup"><span data-stu-id="3db70-103">ISymUnmanagedScope2::GetConstants Method</span></span>

<span data-ttu-id="3db70-104">Возвращает локальные константы, определенные в этой области.</span><span class="sxs-lookup"><span data-stu-id="3db70-104">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3db70-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3db70-105">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3db70-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3db70-106">Parameters</span></span>  

 `cConstants`  
 <span data-ttu-id="3db70-107">окне Длина буфера, `pcConstants` на который указывает параметр.</span><span class="sxs-lookup"><span data-stu-id="3db70-107">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="3db70-108">заполняет Указатель на объект `ULONG32` , который получает размер буфера (в символах), необходимого для хранения констант.</span><span class="sxs-lookup"><span data-stu-id="3db70-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="3db70-109">заполняет Буфер, в котором хранятся константы.</span><span class="sxs-lookup"><span data-stu-id="3db70-109">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3db70-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3db70-110">Return Value</span></span>  

 <span data-ttu-id="3db70-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="3db70-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3db70-112">Требования</span><span class="sxs-lookup"><span data-stu-id="3db70-112">Requirements</span></span>  

 <span data-ttu-id="3db70-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="3db70-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db70-114">См. также</span><span class="sxs-lookup"><span data-stu-id="3db70-114">See also</span></span>

- [<span data-ttu-id="3db70-115">Интерфейс ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="3db70-115">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
