---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: CloseScope'
title: Метод ISymUnmanagedWriter::CloseScope
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
ms.openlocfilehash: bb41e69955632d1e4d86250a63a9f25a7d1ae807
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762556"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="1abbc-103">Метод ISymUnmanagedWriter::CloseScope</span><span class="sxs-lookup"><span data-stu-id="1abbc-103">ISymUnmanagedWriter::CloseScope Method</span></span>

<span data-ttu-id="1abbc-104">Закрывает текущую лексическую область видимости.</span><span class="sxs-lookup"><span data-stu-id="1abbc-104">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1abbc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1abbc-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1abbc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1abbc-106">Parameters</span></span>  

 `endOffset`  
 <span data-ttu-id="1abbc-107">окне Смещение от начала метода точки в конце последней инструкции в лексической области в байтах.</span><span class="sxs-lookup"><span data-stu-id="1abbc-107">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1abbc-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1abbc-108">Return Value</span></span>  

 <span data-ttu-id="1abbc-109">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="1abbc-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1abbc-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="1abbc-110">Remarks</span></span>  

 <span data-ttu-id="1abbc-111">После закрытия области в ней больше нельзя определять переменные.</span><span class="sxs-lookup"><span data-stu-id="1abbc-111">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="1abbc-112">[ISymUnmanagedWriter:: OpenScope](isymunmanagedwriter-openscope-method.md) возвращает непрозрачный идентификатор области, который можно использовать с [ISymUnmanagedWriter:: сетскоперанже](isymunmanagedwriter-setscoperange-method.md) , чтобы определить начальное и конечное смещение области.</span><span class="sxs-lookup"><span data-stu-id="1abbc-112">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="1abbc-113">В этом случае смещения, переданные методам `ISymUnmanagedWriter::OpenScope` и `ISymUnmanagedWriter::CloseScope`, пропускаются.</span><span class="sxs-lookup"><span data-stu-id="1abbc-113">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="1abbc-114">Идентификаторы областей допустимы только в текущем методе.</span><span class="sxs-lookup"><span data-stu-id="1abbc-114">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1abbc-115">Требования</span><span class="sxs-lookup"><span data-stu-id="1abbc-115">Requirements</span></span>  

 <span data-ttu-id="1abbc-116">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="1abbc-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1abbc-117">См. также</span><span class="sxs-lookup"><span data-stu-id="1abbc-117">See also</span></span>

- [<span data-ttu-id="1abbc-118">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="1abbc-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
