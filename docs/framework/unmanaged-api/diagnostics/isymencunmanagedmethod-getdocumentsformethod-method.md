---
description: 'Дополнительные сведения о методе: ISymENCUnmanagedMethod:: Жетдокументсформесод'
title: Метод ISymENCUnmanagedMethod::GetDocumentsForMethod
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type:
- apiref
ms.openlocfilehash: 01c7280abe437266618d96c6e195e61a4f830131
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721545"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="fba84-103">Метод ISymENCUnmanagedMethod::GetDocumentsForMethod</span><span class="sxs-lookup"><span data-stu-id="fba84-103">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>

<span data-ttu-id="fba84-104">Возвращает документы, в которых у этого метода есть строки.</span><span class="sxs-lookup"><span data-stu-id="fba84-104">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fba84-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fba84-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fba84-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fba84-106">Parameters</span></span>  

 `cDocs`  
 <span data-ttu-id="fba84-107">окне Длина буфера, на который указывает `pcDocs` .</span><span class="sxs-lookup"><span data-stu-id="fba84-107">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="fba84-108">заполняет Указатель на объект `ULONG32` , который получает размер (в символах) буфера, необходимого для хранения документов.</span><span class="sxs-lookup"><span data-stu-id="fba84-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="fba84-109">окне Буфер, содержащий документы.</span><span class="sxs-lookup"><span data-stu-id="fba84-109">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fba84-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fba84-110">Return Value</span></span>  

 <span data-ttu-id="fba84-111">S_OK, если метод выполнен. в противном случае — код ошибки.</span><span class="sxs-lookup"><span data-stu-id="fba84-111">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fba84-112">Требования</span><span class="sxs-lookup"><span data-stu-id="fba84-112">Requirements</span></span>  

 <span data-ttu-id="fba84-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="fba84-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fba84-114">См. также</span><span class="sxs-lookup"><span data-stu-id="fba84-114">See also</span></span>

- [<span data-ttu-id="fba84-115">Интерфейс ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="fba84-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
