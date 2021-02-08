---
description: 'Дополнительные сведения: метод ISymUnmanagedReader:: WebMethod'
title: Метод ISymUnmanagedReader::GetDocuments
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
ms.openlocfilehash: 8ee2a2d8e83fcbe2f5b39960fa99e11de2ab4cd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800218"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="f4d82-103">Метод ISymUnmanagedReader::GetDocuments</span><span class="sxs-lookup"><span data-stu-id="f4d82-103">ISymUnmanagedReader::GetDocuments Method</span></span>

<span data-ttu-id="f4d82-104">Возвращает массив всех документов, определенных в хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="f4d82-104">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4d82-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f4d82-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4d82-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f4d82-106">Parameters</span></span>  

 `cDocs`  
 <span data-ttu-id="f4d82-107">[in] Размер массива `pDocs`.</span><span class="sxs-lookup"><span data-stu-id="f4d82-107">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="f4d82-108">заполняет Указатель на переменную, которая получает длину массива.</span><span class="sxs-lookup"><span data-stu-id="f4d82-108">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="f4d82-109">заполняет Указатель на переменную, которая получает массив документов.</span><span class="sxs-lookup"><span data-stu-id="f4d82-109">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4d82-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f4d82-110">Return Value</span></span>  

 <span data-ttu-id="f4d82-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="f4d82-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4d82-112">Требования</span><span class="sxs-lookup"><span data-stu-id="f4d82-112">Requirements</span></span>  

 <span data-ttu-id="f4d82-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="f4d82-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d82-114">См. также</span><span class="sxs-lookup"><span data-stu-id="f4d82-114">See also</span></span>

- [<span data-ttu-id="f4d82-115">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="f4d82-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
