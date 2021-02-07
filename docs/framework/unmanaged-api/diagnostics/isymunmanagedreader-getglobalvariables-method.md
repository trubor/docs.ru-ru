---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: Жетглобалвариаблес'
title: Метод ISymUnmanagedReader::GetGlobalVariables
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
ms.openlocfilehash: 2b017d2a5746942f701cf79d3d29f1eb571dceab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689655"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="ab669-103">Метод ISymUnmanagedReader::GetGlobalVariables</span><span class="sxs-lookup"><span data-stu-id="ab669-103">ISymUnmanagedReader::GetGlobalVariables Method</span></span>

<span data-ttu-id="ab669-104">Возвращает все глобальные переменные.</span><span class="sxs-lookup"><span data-stu-id="ab669-104">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab669-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ab669-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab669-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ab669-106">Parameters</span></span>  

 `cVars`  
 <span data-ttu-id="ab669-107">окне Длина буфера, на который указывает `pcVars` .</span><span class="sxs-lookup"><span data-stu-id="ab669-107">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="ab669-108">заполняет Указатель на объект `ULONG32` , который получает размер буфера, необходимого для хранения переменных.</span><span class="sxs-lookup"><span data-stu-id="ab669-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="ab669-109">заполняет Буфер, содержащий переменные.</span><span class="sxs-lookup"><span data-stu-id="ab669-109">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab669-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ab669-110">Return Value</span></span>  

 <span data-ttu-id="ab669-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="ab669-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab669-112">Требования</span><span class="sxs-lookup"><span data-stu-id="ab669-112">Requirements</span></span>  

 <span data-ttu-id="ab669-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="ab669-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab669-114">См. также</span><span class="sxs-lookup"><span data-stu-id="ab669-114">See also</span></span>

- [<span data-ttu-id="ab669-115">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="ab669-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
