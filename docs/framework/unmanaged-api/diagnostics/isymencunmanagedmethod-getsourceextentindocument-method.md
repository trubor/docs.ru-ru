---
description: 'Дополнительные сведения о методе: ISymENCUnmanagedMethod:: Жетсаурцеекстентиндокумент'
title: Метод ISymENCUnmanagedMethod::GetSourceExtentInDocument
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
ms.openlocfilehash: 6fa9edb524a59b4420ebc737eb8d34eaf0c5c873
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737887"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="17208-103">Метод ISymENCUnmanagedMethod::GetSourceExtentInDocument</span><span class="sxs-lookup"><span data-stu-id="17208-103">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>

<span data-ttu-id="17208-104">Возвращает наименьшую начальную строку и самую новую конечную строку для метода в определенном документе.</span><span class="sxs-lookup"><span data-stu-id="17208-104">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17208-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17208-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17208-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="17208-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="17208-107">окне Указатель на документ.</span><span class="sxs-lookup"><span data-stu-id="17208-107">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="17208-108">заполняет Указатель на объект `ULONG32` , получающий начальную строку.</span><span class="sxs-lookup"><span data-stu-id="17208-108">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="17208-109">заполняет Указатель на объект `ULONG32` , который получает конечную строку.</span><span class="sxs-lookup"><span data-stu-id="17208-109">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17208-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="17208-110">Return Value</span></span>  

 <span data-ttu-id="17208-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="17208-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17208-112">Требования</span><span class="sxs-lookup"><span data-stu-id="17208-112">Requirements</span></span>  

 <span data-ttu-id="17208-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="17208-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17208-114">См. также</span><span class="sxs-lookup"><span data-stu-id="17208-114">See also</span></span>

- [<span data-ttu-id="17208-115">Интерфейс ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="17208-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
