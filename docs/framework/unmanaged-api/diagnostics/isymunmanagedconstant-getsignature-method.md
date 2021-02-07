---
description: 'Дополнительные сведения о методе: ISymUnmanagedConstant:: Signature'
title: Метод ISymUnmanagedConstant::GetSignature
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
ms.openlocfilehash: d28051c9d0e2675e980926fe63ffa7c4d13ef13a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689798"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="7cb11-103">Метод ISymUnmanagedConstant::GetSignature</span><span class="sxs-lookup"><span data-stu-id="7cb11-103">ISymUnmanagedConstant::GetSignature Method</span></span>

<span data-ttu-id="7cb11-104">Возвращает сигнатуру константы.</span><span class="sxs-lookup"><span data-stu-id="7cb11-104">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cb11-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7cb11-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cb11-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7cb11-106">Parameters</span></span>  

 `cSig`  
 <span data-ttu-id="7cb11-107">окне Длина буфера, `pcSig` на который указывает параметр.</span><span class="sxs-lookup"><span data-stu-id="7cb11-107">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="7cb11-108">заполняет Указатель на объект `ULONG32` , который получает размер (в символах) буфера, необходимого для хранения подписи.</span><span class="sxs-lookup"><span data-stu-id="7cb11-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="7cb11-109">заполняет Буфер, в котором хранится подпись.</span><span class="sxs-lookup"><span data-stu-id="7cb11-109">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cb11-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7cb11-110">Return Value</span></span>  

 <span data-ttu-id="7cb11-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="7cb11-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cb11-112">Требования</span><span class="sxs-lookup"><span data-stu-id="7cb11-112">Requirements</span></span>  

 <span data-ttu-id="7cb11-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="7cb11-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb11-114">См. также</span><span class="sxs-lookup"><span data-stu-id="7cb11-114">See also</span></span>

- [<span data-ttu-id="7cb11-115">Интерфейс ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="7cb11-115">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="7cb11-116">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="7cb11-116">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="7cb11-117">Метод GetValue</span><span class="sxs-lookup"><span data-stu-id="7cb11-117">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
