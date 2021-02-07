---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: Method'
title: Метод ISymUnmanagedReader::GetMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
ms.openlocfilehash: 7c0bb65840a3bc1c9450ad29fa8438cdb0377a16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689499"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="38275-103">Метод ISymUnmanagedReader::GetMethod</span><span class="sxs-lookup"><span data-stu-id="38275-103">ISymUnmanagedReader::GetMethod Method</span></span>

<span data-ttu-id="38275-104">Возвращает метод чтения символов по заданному токену метода.</span><span class="sxs-lookup"><span data-stu-id="38275-104">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38275-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="38275-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38275-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="38275-106">Parameters</span></span>  

 `token`  
 <span data-ttu-id="38275-107">окне Токен метода.</span><span class="sxs-lookup"><span data-stu-id="38275-107">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="38275-108">заполняет Указатель на возвращаемый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="38275-108">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38275-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="38275-109">Return Value</span></span>  

 <span data-ttu-id="38275-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="38275-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38275-111">Требования</span><span class="sxs-lookup"><span data-stu-id="38275-111">Requirements</span></span>  

 <span data-ttu-id="38275-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="38275-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38275-113">См. также</span><span class="sxs-lookup"><span data-stu-id="38275-113">See also</span></span>

- [<span data-ttu-id="38275-114">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="38275-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
