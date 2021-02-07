---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: WebMethod'
title: Метод ISymUnmanagedReader::GetVariables
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
ms.openlocfilehash: 93208e6c5c65c4c770c533b7ea72de513451d97d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763908"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="bd431-103">Метод ISymUnmanagedReader::GetVariables</span><span class="sxs-lookup"><span data-stu-id="bd431-103">ISymUnmanagedReader::GetVariables Method</span></span>

<span data-ttu-id="bd431-104">Возвращает нелокальную переменную с учетом ее родителя и имени.</span><span class="sxs-lookup"><span data-stu-id="bd431-104">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd431-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bd431-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd431-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bd431-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="bd431-107">окне Родительский объект переменной.</span><span class="sxs-lookup"><span data-stu-id="bd431-107">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="bd431-108">[in] Размер массива `pVars`.</span><span class="sxs-lookup"><span data-stu-id="bd431-108">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="bd431-109">заполняет Указатель на переменную, которая получает количество переменных, возвращаемых в `pVars` .</span><span class="sxs-lookup"><span data-stu-id="bd431-109">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="bd431-110">заполняет Указатель на переменную, которая получает переменные.</span><span class="sxs-lookup"><span data-stu-id="bd431-110">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd431-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="bd431-111">Return Value</span></span>  

 <span data-ttu-id="bd431-112">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="bd431-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd431-113">Требования</span><span class="sxs-lookup"><span data-stu-id="bd431-113">Requirements</span></span>  

 <span data-ttu-id="bd431-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="bd431-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd431-115">См. также</span><span class="sxs-lookup"><span data-stu-id="bd431-115">See also</span></span>

- [<span data-ttu-id="bd431-116">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="bd431-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
