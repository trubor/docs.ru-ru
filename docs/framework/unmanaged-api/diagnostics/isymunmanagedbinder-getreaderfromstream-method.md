---
description: 'Дополнительные сведения о методе: ISymUnmanagedBinder:: Жетреадерфромстреам'
title: Метод ISymUnmanagedBinder::GetReaderFromStream
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
ms.openlocfilehash: da238ed8e450250be427ae27c4492c1e091f7997
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689993"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="8477c-103">Метод ISymUnmanagedBinder::GetReaderFromStream</span><span class="sxs-lookup"><span data-stu-id="8477c-103">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>

<span data-ttu-id="8477c-104">При наличии интерфейса метаданных и потока, содержащего хранилище символов, возвращает правильную структуру [ISymUnmanagedReader](isymunmanagedreader-interface.md) , которая будет считывать отладочные символы из заданного хранилища символов.</span><span class="sxs-lookup"><span data-stu-id="8477c-104">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8477c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8477c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8477c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8477c-106">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="8477c-107">окне Указатель на интерфейс импорта метаданных.</span><span class="sxs-lookup"><span data-stu-id="8477c-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="8477c-108">окне Указатель на поток, содержащий хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="8477c-108">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="8477c-109">заполняет Указатель, которому присваивается возвращаемый интерфейс [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8477c-109">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8477c-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8477c-110">Return Value</span></span>  

 <span data-ttu-id="8477c-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="8477c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8477c-112">Требования</span><span class="sxs-lookup"><span data-stu-id="8477c-112">Requirements</span></span>  

 <span data-ttu-id="8477c-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="8477c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8477c-114">См. также</span><span class="sxs-lookup"><span data-stu-id="8477c-114">See also</span></span>

- [<span data-ttu-id="8477c-115">Интерфейс ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="8477c-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
