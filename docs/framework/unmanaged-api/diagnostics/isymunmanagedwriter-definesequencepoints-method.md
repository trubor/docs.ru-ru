---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter::D Ефинесекуенцепоинтс'
title: Метод ISymUnmanagedWriter::DefineSequencePoints
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
ms.openlocfilehash: 0c5ac9854ef341512f58cb1cd63ed7dfcde9962e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762335"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="55c75-103">Метод ISymUnmanagedWriter::DefineSequencePoints</span><span class="sxs-lookup"><span data-stu-id="55c75-103">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>

<span data-ttu-id="55c75-104">Определяет группу точек следования в текущем методе.</span><span class="sxs-lookup"><span data-stu-id="55c75-104">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="55c75-105">Каждая начальная строка и начальный столбец определяют начало инструкции в методе.</span><span class="sxs-lookup"><span data-stu-id="55c75-105">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="55c75-106">Каждая конечная строка и конечный столбец определяют конец оператора в методе.</span><span class="sxs-lookup"><span data-stu-id="55c75-106">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="55c75-107">Массивы должны быть отсортированы в порядке возрастания смещений.</span><span class="sxs-lookup"><span data-stu-id="55c75-107">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="55c75-108">Смещение всегда измеряется от начала метода в байтах.</span><span class="sxs-lookup"><span data-stu-id="55c75-108">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55c75-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="55c75-109">Syntax</span></span>  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55c75-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="55c75-110">Parameters</span></span>  

 `document`  
 <span data-ttu-id="55c75-111">окне Объект документа, для которого определяются точки следования.</span><span class="sxs-lookup"><span data-stu-id="55c75-111">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="55c75-112">окне Значение типа `ULONG32` , которое указывает размер каждого `offsets` буфера,, `lines` , `columns` `endLines` и `endColumns` .</span><span class="sxs-lookup"><span data-stu-id="55c75-112">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="55c75-113">окне Смещение точек последовательности, измеряемое от начала метода.</span><span class="sxs-lookup"><span data-stu-id="55c75-113">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="55c75-114">окне Начальные номера строк точек следования.</span><span class="sxs-lookup"><span data-stu-id="55c75-114">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="55c75-115">окне Начальные номера столбцов точек следования.</span><span class="sxs-lookup"><span data-stu-id="55c75-115">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="55c75-116">окне Номера конечных строк точек следования.</span><span class="sxs-lookup"><span data-stu-id="55c75-116">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="55c75-117">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="55c75-117">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="55c75-118">окне Конечные номера столбцов точек следования.</span><span class="sxs-lookup"><span data-stu-id="55c75-118">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="55c75-119">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="55c75-119">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55c75-120">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="55c75-120">Return Value</span></span>  

 <span data-ttu-id="55c75-121">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="55c75-121">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55c75-122">Требования</span><span class="sxs-lookup"><span data-stu-id="55c75-122">Requirements</span></span>  

 <span data-ttu-id="55c75-123">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="55c75-123">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c75-124">См. также</span><span class="sxs-lookup"><span data-stu-id="55c75-124">See also</span></span>

- [<span data-ttu-id="55c75-125">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="55c75-125">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
