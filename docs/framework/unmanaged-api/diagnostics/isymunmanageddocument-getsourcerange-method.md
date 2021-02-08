---
description: 'Дополнительные сведения о методе: ISymUnmanagedDocument:: GetSourceRange'
title: Метод ISymUnmanagedDocument::GetSourceRange
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
ms.openlocfilehash: 98718298d7bf2f44d418a40f17ad19cdee0b6771
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790169"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="d988d-103">Метод ISymUnmanagedDocument::GetSourceRange</span><span class="sxs-lookup"><span data-stu-id="d988d-103">ISymUnmanagedDocument::GetSourceRange Method</span></span>

<span data-ttu-id="d988d-104">Возвращает указанный диапазон внедренного источника в заданный буфер.</span><span class="sxs-lookup"><span data-stu-id="d988d-104">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="d988d-105">Буфер должен быть достаточно большим, чтобы вместить исходный код.</span><span class="sxs-lookup"><span data-stu-id="d988d-105">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d988d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d988d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d988d-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="d988d-107">Parameters</span></span>  

 `startLine`  
 <span data-ttu-id="d988d-108">окне Начальная строка текущего документа.</span><span class="sxs-lookup"><span data-stu-id="d988d-108">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="d988d-109">окне Начальный столбец в текущем документе.</span><span class="sxs-lookup"><span data-stu-id="d988d-109">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="d988d-110">окне Последняя строка в текущем документе.</span><span class="sxs-lookup"><span data-stu-id="d988d-110">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="d988d-111">окне Последний столбец в текущем документе.</span><span class="sxs-lookup"><span data-stu-id="d988d-111">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="d988d-112">окне Размер источника в байтах.</span><span class="sxs-lookup"><span data-stu-id="d988d-112">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="d988d-113">заполняет Указатель на переменную, которая получает исходный размер.</span><span class="sxs-lookup"><span data-stu-id="d988d-113">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="d988d-114">заполняет Размер и длина указанного диапазона исходного документа в байтах.</span><span class="sxs-lookup"><span data-stu-id="d988d-114">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d988d-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d988d-115">Return Value</span></span>  

 <span data-ttu-id="d988d-116">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="d988d-116">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d988d-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d988d-117">See also</span></span>

- [<span data-ttu-id="d988d-118">Интерфейс ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="d988d-118">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
