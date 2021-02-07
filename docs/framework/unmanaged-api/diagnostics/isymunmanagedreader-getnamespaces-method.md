---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: namespace'
title: Метод ISymUnmanagedReader::GetNamespaces
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
ms.openlocfilehash: 47f7bff829ca2a52eb95d7d7693a7486301de092
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764012"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="9b8b0-103">Метод ISymUnmanagedReader::GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="9b8b0-103">ISymUnmanagedReader::GetNamespaces Method</span></span>

<span data-ttu-id="9b8b0-104">Возвращает пространства имен, определенные в глобальной области в этом хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="9b8b0-104">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b8b0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9b8b0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b8b0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9b8b0-106">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="9b8b0-107">окне Размер массива пространств имен.</span><span class="sxs-lookup"><span data-stu-id="9b8b0-107">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="9b8b0-108">заполняет Указатель на переменную, которая получает длину списка пространств имен.</span><span class="sxs-lookup"><span data-stu-id="9b8b0-108">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="9b8b0-109">заполняет Указатель на переменную, которая получает список пространств имен.</span><span class="sxs-lookup"><span data-stu-id="9b8b0-109">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b8b0-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9b8b0-110">Return Value</span></span>  

 <span data-ttu-id="9b8b0-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="9b8b0-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b8b0-112">Требования</span><span class="sxs-lookup"><span data-stu-id="9b8b0-112">Requirements</span></span>  

 <span data-ttu-id="9b8b0-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="9b8b0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b8b0-114">См. также</span><span class="sxs-lookup"><span data-stu-id="9b8b0-114">See also</span></span>

- [<span data-ttu-id="9b8b0-115">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="9b8b0-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
