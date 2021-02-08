---
description: 'Дополнительные сведения о методе: ISymUnmanagedMethod:: методом offset'
title: Метод ISymUnmanagedMethod::GetOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
ms.openlocfilehash: 3bc7154a47a38fd2cbadc62921f6e57f7901087e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790130"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="fe6e3-103">Метод ISymUnmanagedMethod::GetOffset</span><span class="sxs-lookup"><span data-stu-id="fe6e3-103">ISymUnmanagedMethod::GetOffset Method</span></span>

<span data-ttu-id="fe6e3-104">Возвращает смещение в этом методе, соответствующее заданной позиции в документе.</span><span class="sxs-lookup"><span data-stu-id="fe6e3-104">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe6e3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fe6e3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe6e3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fe6e3-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="fe6e3-107">окне Указатель на документ, для которого запрашивается смещение.</span><span class="sxs-lookup"><span data-stu-id="fe6e3-107">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="fe6e3-108">окне Строка документа, для которой запрашивается смещение.</span><span class="sxs-lookup"><span data-stu-id="fe6e3-108">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="fe6e3-109">окне Столбец документа, для которого запрашивается смещение.</span><span class="sxs-lookup"><span data-stu-id="fe6e3-109">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="fe6e3-110">заполняет Указатель на объект `ULONG32` , который получает смещения.</span><span class="sxs-lookup"><span data-stu-id="fe6e3-110">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe6e3-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fe6e3-111">Return Value</span></span>  

 <span data-ttu-id="fe6e3-112">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="fe6e3-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe6e3-113">Требования</span><span class="sxs-lookup"><span data-stu-id="fe6e3-113">Requirements</span></span>  

 <span data-ttu-id="fe6e3-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="fe6e3-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe6e3-115">См. также</span><span class="sxs-lookup"><span data-stu-id="fe6e3-115">See also</span></span>

- [<span data-ttu-id="fe6e3-116">Интерфейс ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="fe6e3-116">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
