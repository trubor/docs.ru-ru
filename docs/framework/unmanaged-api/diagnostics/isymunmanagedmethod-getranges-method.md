---
description: 'См. Дополнительные сведения о методе ISymUnmanagedMethod:: Range.'
title: Метод ISymUnmanagedMethod::GetRanges
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
ms.openlocfilehash: e6a1da285c0574ef5910e8e727c3bcc5cb9e5d35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790104"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="1fefc-103">Метод ISymUnmanagedMethod::GetRanges</span><span class="sxs-lookup"><span data-stu-id="1fefc-103">ISymUnmanagedMethod::GetRanges Method</span></span>

<span data-ttu-id="1fefc-104">При наличии позиции в документе возвращает массив пар начального и конечного смещения, соответствующих диапазонам промежуточного языка MSIL, которые находятся в этом методе.</span><span class="sxs-lookup"><span data-stu-id="1fefc-104">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="1fefc-105">Массив является массивом целых чисел и имеет формат [начало, конец, начало, конец].</span><span class="sxs-lookup"><span data-stu-id="1fefc-105">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="1fefc-106">Число пар диапазонов — это длина массива, деленная на 2.</span><span class="sxs-lookup"><span data-stu-id="1fefc-106">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fefc-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1fefc-107">Syntax</span></span>  
  
```cpp  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fefc-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="1fefc-108">Parameters</span></span>  

 `document`  
 <span data-ttu-id="1fefc-109">окне Документ, для которого запрашивается смещение.</span><span class="sxs-lookup"><span data-stu-id="1fefc-109">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="1fefc-110">окне Строка документа, соответствующая диапазонам.</span><span class="sxs-lookup"><span data-stu-id="1fefc-110">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="1fefc-111">окне Столбец документа, соответствующий диапазонам.</span><span class="sxs-lookup"><span data-stu-id="1fefc-111">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="1fefc-112">[in] Размер массива `ranges`.</span><span class="sxs-lookup"><span data-stu-id="1fefc-112">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="1fefc-113">заполняет Указатель на объект `ULONG32` , который получает размер буфера, необходимого для хранения диапазонов.</span><span class="sxs-lookup"><span data-stu-id="1fefc-113">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="1fefc-114">заполняет Указатель на буфер, который получает диапазоны.</span><span class="sxs-lookup"><span data-stu-id="1fefc-114">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fefc-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1fefc-115">Return Value</span></span>  

 <span data-ttu-id="1fefc-116">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="1fefc-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fefc-117">Требования</span><span class="sxs-lookup"><span data-stu-id="1fefc-117">Requirements</span></span>  

 <span data-ttu-id="1fefc-118">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="1fefc-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fefc-119">См. также</span><span class="sxs-lookup"><span data-stu-id="1fefc-119">See also</span></span>

- [<span data-ttu-id="1fefc-120">Интерфейс ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="1fefc-120">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
