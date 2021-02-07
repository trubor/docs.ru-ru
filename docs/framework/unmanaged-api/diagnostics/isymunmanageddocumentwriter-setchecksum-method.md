---
description: 'Дополнительные сведения о методе: ISymUnmanagedDocumentWriter:: Сетчекксум'
title: Метод ISymUnmanagedDocumentWriter::SetCheckSum
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
ms.openlocfilehash: ac2ba9654f3610dca333cf0e06c20696cf31bd1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710092"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="92979-103">Метод ISymUnmanagedDocumentWriter::SetCheckSum</span><span class="sxs-lookup"><span data-stu-id="92979-103">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>

<span data-ttu-id="92979-104">Задает сведения о контрольной сумме.</span><span class="sxs-lookup"><span data-stu-id="92979-104">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92979-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="92979-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92979-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="92979-106">Parameters</span></span>  

 `algorithmId`  
 <span data-ttu-id="92979-107">окне Идентификатор GUID, представляющий идентификатор алгоритма.</span><span class="sxs-lookup"><span data-stu-id="92979-107">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="92979-108">окне Значение типа `ULONG32` , указывающее размер буфера (в байтах) `checkSum` .</span><span class="sxs-lookup"><span data-stu-id="92979-108">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="92979-109">окне Буфер, в котором хранятся сведения о контрольной сумме.</span><span class="sxs-lookup"><span data-stu-id="92979-109">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92979-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="92979-110">Return Value</span></span>  

 <span data-ttu-id="92979-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="92979-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92979-112">Требования</span><span class="sxs-lookup"><span data-stu-id="92979-112">Requirements</span></span>  

 <span data-ttu-id="92979-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="92979-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92979-114">См. также</span><span class="sxs-lookup"><span data-stu-id="92979-114">See also</span></span>

- [<span data-ttu-id="92979-115">Интерфейс ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="92979-115">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
