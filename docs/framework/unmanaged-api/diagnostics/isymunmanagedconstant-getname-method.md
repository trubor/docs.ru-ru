---
description: 'Дополнительные сведения о методе: ISymUnmanagedConstant:: Name'
title: Метод ISymUnmanagedConstant::GetName
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: 57531711ed60c9e35e749a3cb1f1ba5d5c48ca66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689824"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="ab550-103">Метод ISymUnmanagedConstant::GetName</span><span class="sxs-lookup"><span data-stu-id="ab550-103">ISymUnmanagedConstant::GetName Method</span></span>

<span data-ttu-id="ab550-104">Возвращает имя константы.</span><span class="sxs-lookup"><span data-stu-id="ab550-104">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab550-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ab550-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab550-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ab550-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="ab550-107">окне Длина буфера, `szName` на который указывает параметр.</span><span class="sxs-lookup"><span data-stu-id="ab550-107">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ab550-108">заполняет Указатель на объект `ULONG32` , который получает размер (в символах) буфера, необходимого для хранения имени, включая завершение нулевого значения.</span><span class="sxs-lookup"><span data-stu-id="ab550-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="ab550-109">заполняет Буфер, в котором хранится имя.</span><span class="sxs-lookup"><span data-stu-id="ab550-109">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab550-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ab550-110">Return Value</span></span>  

 <span data-ttu-id="ab550-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="ab550-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab550-112">Требования</span><span class="sxs-lookup"><span data-stu-id="ab550-112">Requirements</span></span>  

 <span data-ttu-id="ab550-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="ab550-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab550-114">См. также</span><span class="sxs-lookup"><span data-stu-id="ab550-114">See also</span></span>

- [<span data-ttu-id="ab550-115">Интерфейс ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="ab550-115">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="ab550-116">Метод GetSignature</span><span class="sxs-lookup"><span data-stu-id="ab550-116">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="ab550-117">Метод GetValue</span><span class="sxs-lookup"><span data-stu-id="ab550-117">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
