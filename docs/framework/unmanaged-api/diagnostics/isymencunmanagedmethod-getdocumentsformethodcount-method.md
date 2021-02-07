---
description: 'Дополнительные сведения о методе: ISymENCUnmanagedMethod:: GetDocumentsForMethodCount'
title: Метод ISymENCUnmanagedMethod::GetDocumentsForMethodCount
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
ms.openlocfilehash: 0594771c544ad1de32531e92f30fe96f245b5699
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738017"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="0573b-103">Метод ISymENCUnmanagedMethod::GetDocumentsForMethodCount</span><span class="sxs-lookup"><span data-stu-id="0573b-103">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>

<span data-ttu-id="0573b-104">Возвращает число документов, в которых у этого метода есть строки.</span><span class="sxs-lookup"><span data-stu-id="0573b-104">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0573b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0573b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0573b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0573b-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="0573b-107">заполняет Указатель на объект `ULONG32` , который получает размер буфера, необходимого для хранения документов.</span><span class="sxs-lookup"><span data-stu-id="0573b-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0573b-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0573b-108">Return Value</span></span>  

 <span data-ttu-id="0573b-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="0573b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0573b-110">Требования</span><span class="sxs-lookup"><span data-stu-id="0573b-110">Requirements</span></span>  

 <span data-ttu-id="0573b-111">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="0573b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0573b-112">См. также</span><span class="sxs-lookup"><span data-stu-id="0573b-112">See also</span></span>

- [<span data-ttu-id="0573b-113">Интерфейс ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="0573b-113">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
