---
description: 'Дополнительные сведения о методе: ISymUnmanagedDocument:: CheckSum'
title: Метод ISymUnmanagedDocument::GetCheckSum
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
ms.openlocfilehash: 9f9a42e58b22661a2233fcb457b9b42b0d6a3d1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737692"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="58ffd-103">Метод ISymUnmanagedDocument::GetCheckSum</span><span class="sxs-lookup"><span data-stu-id="58ffd-103">ISymUnmanagedDocument::GetCheckSum Method</span></span>

<span data-ttu-id="58ffd-104">Возвращает контрольную сумму.</span><span class="sxs-lookup"><span data-stu-id="58ffd-104">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58ffd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="58ffd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58ffd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="58ffd-106">Parameters</span></span>  

 `cData`  
 <span data-ttu-id="58ffd-107">окне Длина буфера, предоставленного `data` параметром</span><span class="sxs-lookup"><span data-stu-id="58ffd-107">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="58ffd-108">заполняет Размер и длина контрольной суммы в байтах.</span><span class="sxs-lookup"><span data-stu-id="58ffd-108">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="58ffd-109">заполняет Буфер, получающий контрольную сумму.</span><span class="sxs-lookup"><span data-stu-id="58ffd-109">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58ffd-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="58ffd-110">Return Value</span></span>  

 <span data-ttu-id="58ffd-111">S_OK, если метод выполнен. в противном случае — код ошибки.</span><span class="sxs-lookup"><span data-stu-id="58ffd-111">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ffd-112">См. также</span><span class="sxs-lookup"><span data-stu-id="58ffd-112">See also</span></span>

- [<span data-ttu-id="58ffd-113">Интерфейс ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="58ffd-113">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
