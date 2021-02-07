---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: OpenScope'
title: Метод ISymUnmanagedWriter::OpenScope
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
ms.openlocfilehash: 1e47d97941b053fedcf08c7582e1083988a9fed4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762114"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="6ead1-103">Метод ISymUnmanagedWriter::OpenScope</span><span class="sxs-lookup"><span data-stu-id="6ead1-103">ISymUnmanagedWriter::OpenScope Method</span></span>

<span data-ttu-id="6ead1-104">Открывает новую лексическую область видимости в текущем методе.</span><span class="sxs-lookup"><span data-stu-id="6ead1-104">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="6ead1-105">Область становится новой текущей областью и помещается в стек областей.</span><span class="sxs-lookup"><span data-stu-id="6ead1-105">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="6ead1-106">Области должны образовывать иерархию.</span><span class="sxs-lookup"><span data-stu-id="6ead1-106">Scopes must form a hierarchy.</span></span> <span data-ttu-id="6ead1-107">Не допускается перекрытие одноуровневых элементов.</span><span class="sxs-lookup"><span data-stu-id="6ead1-107">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ead1-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6ead1-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ead1-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="6ead1-109">Parameters</span></span>  

 `startOffset`  
 <span data-ttu-id="6ead1-110">окне Смещение первой инструкции в лексической области в байтах от начала метода.</span><span class="sxs-lookup"><span data-stu-id="6ead1-110">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6ead1-111">заполняет Указатель на объект `ULONG32` , который получает идентификатор области.</span><span class="sxs-lookup"><span data-stu-id="6ead1-111">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ead1-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6ead1-112">Return Value</span></span>  

 <span data-ttu-id="6ead1-113">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="6ead1-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ead1-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="6ead1-114">Remarks</span></span>  

 <span data-ttu-id="6ead1-115">`ISymUnmanagedWriter::OpenScope` возвращает непрозрачный идентификатор области, который можно использовать с [ISymUnmanagedWriter:: сетскоперанже](isymunmanagedwriter-setscoperange-method.md) для определения начального и конечного смещения области в более позднее время.</span><span class="sxs-lookup"><span data-stu-id="6ead1-115">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="6ead1-116">В этом случае смещения, передаваемые в `ISymUnmanagedWriter::OpenScope` и [ISymUnmanagedWriter:: CloseScope](isymunmanagedwriter-closescope-method.md) , игнорируются.</span><span class="sxs-lookup"><span data-stu-id="6ead1-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="6ead1-117">Идентификаторы областей допустимы только в текущем методе.</span><span class="sxs-lookup"><span data-stu-id="6ead1-117">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ead1-118">Требования</span><span class="sxs-lookup"><span data-stu-id="6ead1-118">Requirements</span></span>  

 <span data-ttu-id="6ead1-119">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="6ead1-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ead1-120">См. также</span><span class="sxs-lookup"><span data-stu-id="6ead1-120">See also</span></span>

- [<span data-ttu-id="6ead1-121">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="6ead1-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
