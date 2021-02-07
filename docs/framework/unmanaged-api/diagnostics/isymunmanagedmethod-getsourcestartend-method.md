---
description: 'Дополнительные сведения о методе: ISymUnmanagedMethod:: Жетсаурцестартенд'
title: Метод ISymUnmanagedMethod::GetSourceStartEnd
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
ms.openlocfilehash: 0d247427998970d86c1ad1ec37f5b32a846a6f7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709988"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="9251f-103">Метод ISymUnmanagedMethod::GetSourceStartEnd</span><span class="sxs-lookup"><span data-stu-id="9251f-103">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>

<span data-ttu-id="9251f-104">Возвращает начальную и конечную позиции документа для источника данного метода.</span><span class="sxs-lookup"><span data-stu-id="9251f-104">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="9251f-105">Первой позицией массива является начало, а вторая — конец.</span><span class="sxs-lookup"><span data-stu-id="9251f-105">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9251f-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9251f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9251f-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="9251f-107">Parameters</span></span>  

 `docs`  
 <span data-ttu-id="9251f-108">окне Начальный и конечный документы источника.</span><span class="sxs-lookup"><span data-stu-id="9251f-108">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="9251f-109">окне Начальная и конечная строки соответствующих исходных документов.</span><span class="sxs-lookup"><span data-stu-id="9251f-109">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="9251f-110">окне Начальные и конечные столбцы в соответствующих исходных документах.</span><span class="sxs-lookup"><span data-stu-id="9251f-110">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="9251f-111">[out] `true` значение, если позиции определены; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="9251f-111">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9251f-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9251f-112">Return Value</span></span>  

 <span data-ttu-id="9251f-113">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="9251f-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9251f-114">Требования</span><span class="sxs-lookup"><span data-stu-id="9251f-114">Requirements</span></span>  

 <span data-ttu-id="9251f-115">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="9251f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9251f-116">См. также</span><span class="sxs-lookup"><span data-stu-id="9251f-116">See also</span></span>

- [<span data-ttu-id="9251f-117">Интерфейс ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="9251f-117">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
