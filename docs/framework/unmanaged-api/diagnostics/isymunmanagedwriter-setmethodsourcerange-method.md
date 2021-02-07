---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: Сетмесодсаурцеранже'
title: Метод ISymUnmanagedWriter::SetMethodSourceRange
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
ms.openlocfilehash: 2e2f0f664d8be30a8c3628100fafb3740d34f54f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762075"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="96667-103">Метод ISymUnmanagedWriter::SetMethodSourceRange</span><span class="sxs-lookup"><span data-stu-id="96667-103">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>

<span data-ttu-id="96667-104">Указывает истинные начало и конец метода в исходном файле.</span><span class="sxs-lookup"><span data-stu-id="96667-104">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="96667-105">Этот метод используется для указания экстента метода независимо от точек следования, которые существуют в методе.</span><span class="sxs-lookup"><span data-stu-id="96667-105">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96667-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="96667-106">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96667-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="96667-107">Parameters</span></span>  

 `startDoc`  
 <span data-ttu-id="96667-108">окне Указатель на документ, содержащий начальную точку.</span><span class="sxs-lookup"><span data-stu-id="96667-108">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="96667-109">окне Номер начальной строки.</span><span class="sxs-lookup"><span data-stu-id="96667-109">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="96667-110">окне Начальный столбец.</span><span class="sxs-lookup"><span data-stu-id="96667-110">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="96667-111">окне Указатель на документ, содержащий конечную точку.</span><span class="sxs-lookup"><span data-stu-id="96667-111">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="96667-112">окне Номер конечной строки.</span><span class="sxs-lookup"><span data-stu-id="96667-112">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="96667-113">окне Номер конечного столбца.</span><span class="sxs-lookup"><span data-stu-id="96667-113">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96667-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="96667-114">Return Value</span></span>  

 <span data-ttu-id="96667-115">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="96667-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96667-116">Требования</span><span class="sxs-lookup"><span data-stu-id="96667-116">Requirements</span></span>  

 <span data-ttu-id="96667-117">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="96667-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96667-118">См. также</span><span class="sxs-lookup"><span data-stu-id="96667-118">See also</span></span>

- [<span data-ttu-id="96667-119">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="96667-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
