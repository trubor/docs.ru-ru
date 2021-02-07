---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: Жетусерентрипоинт'
title: Метод ISymUnmanagedReader::GetUserEntryPoint
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type:
- apiref
ms.openlocfilehash: b8696a339fc8aefca2b1a1f9b960ba94ce565d8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763921"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="77667-103">Метод ISymUnmanagedReader::GetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="77667-103">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>

<span data-ttu-id="77667-104">Возвращает метод, указанный в качестве точки входа пользователя для модуля, если он есть.</span><span class="sxs-lookup"><span data-stu-id="77667-104">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="77667-105">Например, этот метод может быть основным методом пользователя вместо заглушек, созданных компилятором, перед методом Main.</span><span class="sxs-lookup"><span data-stu-id="77667-105">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77667-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77667-106">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77667-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="77667-107">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="77667-108">заполняет Указатель на переменную, которая получает точку входа.</span><span class="sxs-lookup"><span data-stu-id="77667-108">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77667-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="77667-109">Return Value</span></span>  

 <span data-ttu-id="77667-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="77667-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77667-111">Требования</span><span class="sxs-lookup"><span data-stu-id="77667-111">Requirements</span></span>  

 <span data-ttu-id="77667-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="77667-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77667-113">См. также</span><span class="sxs-lookup"><span data-stu-id="77667-113">See also</span></span>

- [<span data-ttu-id="77667-114">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="77667-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
