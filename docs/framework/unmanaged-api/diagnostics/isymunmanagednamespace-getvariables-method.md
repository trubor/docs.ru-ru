---
description: 'Дополнительные сведения о методе: ISymUnmanagedNamespace:: WebMethod'
title: Метод ISymUnmanagedNamespace::GetVariables
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
ms.openlocfilehash: 63316bf3ba1e4736d542be3362076c3ae6e95def
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721207"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="f4cc2-103">Метод ISymUnmanagedNamespace::GetVariables</span><span class="sxs-lookup"><span data-stu-id="f4cc2-103">ISymUnmanagedNamespace::GetVariables Method</span></span>

<span data-ttu-id="f4cc2-104">Возвращает все переменные, определенные в глобальной области видимости в этом пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="f4cc2-104">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4cc2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f4cc2-105">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4cc2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f4cc2-106">Parameters</span></span>  

 `cVars`  
 <span data-ttu-id="f4cc2-107">окне Значение типа `ULONG32` , указывающее размер `pVars` массива.</span><span class="sxs-lookup"><span data-stu-id="f4cc2-107">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="f4cc2-108">заполняет Указатель на объект `ULONG32` , который получает размер буфера, необходимого для хранения пространств имен.</span><span class="sxs-lookup"><span data-stu-id="f4cc2-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="f4cc2-109">заполняет Указатель на буфер, содержащий пространства имен.</span><span class="sxs-lookup"><span data-stu-id="f4cc2-109">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4cc2-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f4cc2-110">Return Value</span></span>  

 <span data-ttu-id="f4cc2-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="f4cc2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4cc2-112">Требования</span><span class="sxs-lookup"><span data-stu-id="f4cc2-112">Requirements</span></span>  

 <span data-ttu-id="f4cc2-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="f4cc2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4cc2-114">См. также</span><span class="sxs-lookup"><span data-stu-id="f4cc2-114">See also</span></span>

- [<span data-ttu-id="f4cc2-115">Интерфейс ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="f4cc2-115">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
