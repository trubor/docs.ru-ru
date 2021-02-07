---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: Сетскоперанже'
title: Метод ISymUnmanagedWriter::SetScopeRange
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
ms.openlocfilehash: 43cfbeaa0d366b9f2d25068cfa7b91a0fea8ac59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762062"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="82624-103">Метод ISymUnmanagedWriter::SetScopeRange</span><span class="sxs-lookup"><span data-stu-id="82624-103">ISymUnmanagedWriter::SetScopeRange Method</span></span>

<span data-ttu-id="82624-104">Определяет диапазон смещений для заданной лексической области видимости.</span><span class="sxs-lookup"><span data-stu-id="82624-104">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="82624-105">Область становится новой текущей областью и помещается в стек областей.</span><span class="sxs-lookup"><span data-stu-id="82624-105">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="82624-106">Области должны образовывать иерархию.</span><span class="sxs-lookup"><span data-stu-id="82624-106">Scopes must form a hierarchy.</span></span> <span data-ttu-id="82624-107">Не допускается перекрытие одноуровневых элементов.</span><span class="sxs-lookup"><span data-stu-id="82624-107">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82624-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="82624-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82624-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="82624-109">Parameters</span></span>  

 `scopeId`  
 <span data-ttu-id="82624-110">окне Идентификатор области.</span><span class="sxs-lookup"><span data-stu-id="82624-110">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="82624-111">окне Смещение первой инструкции в лексической области от начала метода (в байтах).</span><span class="sxs-lookup"><span data-stu-id="82624-111">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="82624-112">окне Смещение (в байтах) последней инструкции в лексической области от начала метода.</span><span class="sxs-lookup"><span data-stu-id="82624-112">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82624-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="82624-113">Return Value</span></span>  

 <span data-ttu-id="82624-114">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="82624-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82624-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="82624-115">Remarks</span></span>  

 <span data-ttu-id="82624-116">[ISymUnmanagedWriter:: OpenScope](isymunmanagedwriter-openscope-method.md) возвращает непрозрачный идентификатор области, который можно использовать с `ISymUnmanagedWriter::SetScopeRange` для определения начального и конечного смещения области в более позднее время.</span><span class="sxs-lookup"><span data-stu-id="82624-116">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="82624-117">В этом случае смещения, передаваемые в `ISymUnmanagedWriter::OpenScope` и [ISymUnmanagedWriter:: CloseScope](isymunmanagedwriter-closescope-method.md) , игнорируются.</span><span class="sxs-lookup"><span data-stu-id="82624-117">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="82624-118">Идентификаторы областей допустимы только в текущем методе.</span><span class="sxs-lookup"><span data-stu-id="82624-118">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82624-119">Требования</span><span class="sxs-lookup"><span data-stu-id="82624-119">Requirements</span></span>  

 <span data-ttu-id="82624-120">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="82624-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82624-121">См. также</span><span class="sxs-lookup"><span data-stu-id="82624-121">See also</span></span>

- [<span data-ttu-id="82624-122">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="82624-122">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
