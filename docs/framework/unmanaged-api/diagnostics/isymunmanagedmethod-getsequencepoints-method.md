---
description: 'Дополнительные сведения о методе: ISymUnmanagedMethod:: Жетсекуенцепоинтс'
title: Метод ISymUnmanagedMethod::GetSequencePoints
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: acdfcb014648593065bd1ae252ef936898a1e8b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721298"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="6123d-103">Метод ISymUnmanagedMethod::GetSequencePoints</span><span class="sxs-lookup"><span data-stu-id="6123d-103">ISymUnmanagedMethod::GetSequencePoints Method</span></span>

<span data-ttu-id="6123d-104">Возвращает все точки следования в этом методе.</span><span class="sxs-lookup"><span data-stu-id="6123d-104">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6123d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6123d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6123d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6123d-106">Parameters</span></span>  

 `cPoints`  
 <span data-ttu-id="6123d-107">окне Объект `ULONG32` , который получает размер `offsets` массивов,,,, `documents` `lines` `columns` `endLines` и `endColumns` .</span><span class="sxs-lookup"><span data-stu-id="6123d-107">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="6123d-108">заполняет Указатель на объект `ULONG32` , который получает длину буфера, необходимого для хранения точек следования.</span><span class="sxs-lookup"><span data-stu-id="6123d-108">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="6123d-109">окне Массив, в котором хранятся смещения MSIL от начала метода для точек следования.</span><span class="sxs-lookup"><span data-stu-id="6123d-109">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="6123d-110">окне Массив, в котором хранятся документы, в которых находятся точки следования.</span><span class="sxs-lookup"><span data-stu-id="6123d-110">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="6123d-111">окне Массив, в котором хранятся строки в документах, где находятся точки следования.</span><span class="sxs-lookup"><span data-stu-id="6123d-111">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="6123d-112">окне Массив, в котором хранятся столбцы в документах, где находятся точки следования.</span><span class="sxs-lookup"><span data-stu-id="6123d-112">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="6123d-113">окне Массив строк в документах, в которых заканчивается точка следования.</span><span class="sxs-lookup"><span data-stu-id="6123d-113">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="6123d-114">окне Массив столбцов в документах, в которых находятся конечные точки последовательности.</span><span class="sxs-lookup"><span data-stu-id="6123d-114">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6123d-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6123d-115">Return Value</span></span>  

 <span data-ttu-id="6123d-116">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="6123d-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6123d-117">Требования</span><span class="sxs-lookup"><span data-stu-id="6123d-117">Requirements</span></span>  

 <span data-ttu-id="6123d-118">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="6123d-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6123d-119">См. также</span><span class="sxs-lookup"><span data-stu-id="6123d-119">See also</span></span>

- [<span data-ttu-id="6123d-120">Интерфейс ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="6123d-120">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
