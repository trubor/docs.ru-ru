---
description: 'Дополнительные сведения о методе: ISymUnmanagedVariable:: Name'
title: Метод ISymUnmanagedVariable::GetName
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
ms.openlocfilehash: 88d8cf4c81200a30e2a102b63af2817fef2b50c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762790"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="24b2e-103">Метод ISymUnmanagedVariable::GetName</span><span class="sxs-lookup"><span data-stu-id="24b2e-103">ISymUnmanagedVariable::GetName Method</span></span>

<span data-ttu-id="24b2e-104">Возвращает имя этой переменной.</span><span class="sxs-lookup"><span data-stu-id="24b2e-104">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24b2e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="24b2e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24b2e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="24b2e-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="24b2e-107">окне Длина буфера, `pcchName` на который указывает параметр.</span><span class="sxs-lookup"><span data-stu-id="24b2e-107">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="24b2e-108">заполняет Указатель на объект `ULONG32` , который получает размер (в символах) буфера, необходимого для хранения имени, включая завершение нулевого значения.</span><span class="sxs-lookup"><span data-stu-id="24b2e-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="24b2e-109">заполняет Буфер, в котором хранится имя.</span><span class="sxs-lookup"><span data-stu-id="24b2e-109">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24b2e-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="24b2e-110">Return Value</span></span>  

 <span data-ttu-id="24b2e-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="24b2e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24b2e-112">Требования</span><span class="sxs-lookup"><span data-stu-id="24b2e-112">Requirements</span></span>  

 <span data-ttu-id="24b2e-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="24b2e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b2e-114">См. также</span><span class="sxs-lookup"><span data-stu-id="24b2e-114">See also</span></span>

- [<span data-ttu-id="24b2e-115">Интерфейс ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="24b2e-115">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
