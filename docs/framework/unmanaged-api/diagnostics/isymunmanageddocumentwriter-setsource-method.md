---
description: 'Дополнительные сведения о методе: ISymUnmanagedDocumentWriter:: SetSource'
title: Метод ISymUnmanagedDocumentWriter::SetSource
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
ms.openlocfilehash: e24e34a297a9931babf3df4f2bae1b5e8f60db1b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721480"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="7c7d4-103">Метод ISymUnmanagedDocumentWriter::SetSource</span><span class="sxs-lookup"><span data-stu-id="7c7d4-103">ISymUnmanagedDocumentWriter::SetSource Method</span></span>

<span data-ttu-id="7c7d4-104">Задает внедренный источник для записываемого документа.</span><span class="sxs-lookup"><span data-stu-id="7c7d4-104">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c7d4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7c7d4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c7d4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7c7d4-106">Parameters</span></span>  

 `sourceSize`  
 <span data-ttu-id="7c7d4-107">окне Значение типа `ULONG32` , содержащее размер `source` буфера.</span><span class="sxs-lookup"><span data-stu-id="7c7d4-107">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="7c7d4-108">окне Буфер, в котором хранится внедренный источник.</span><span class="sxs-lookup"><span data-stu-id="7c7d4-108">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c7d4-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7c7d4-109">Return Value</span></span>  

 <span data-ttu-id="7c7d4-110">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="7c7d4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c7d4-111">Требования</span><span class="sxs-lookup"><span data-stu-id="7c7d4-111">Requirements</span></span>  

 <span data-ttu-id="7c7d4-112">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="7c7d4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c7d4-113">См. также</span><span class="sxs-lookup"><span data-stu-id="7c7d4-113">See also</span></span>

- [<span data-ttu-id="7c7d4-114">Интерфейс ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="7c7d4-114">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
