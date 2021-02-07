---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter2::D efineLocalVariable2'
title: Метод ISymUnmanagedWriter2::DefineLocalVariable2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
ms.openlocfilehash: 169a086b8420b5dbe20af8e16b21d5b41a958ead
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761815"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="95ef0-103">Метод ISymUnmanagedWriter2::DefineLocalVariable2</span><span class="sxs-lookup"><span data-stu-id="95ef0-103">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>

<span data-ttu-id="95ef0-104">Определяет одну переменную в текущей лексической области видимости.</span><span class="sxs-lookup"><span data-stu-id="95ef0-104">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="95ef0-105">Этот метод может вызываться несколько раз для переменной с тем же именем, которая имеет несколько домов в пределах области.</span><span class="sxs-lookup"><span data-stu-id="95ef0-105">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="95ef0-106">Однако в этом случае значения `startOffset` `endOffset` параметров и не должны перекрываться.</span><span class="sxs-lookup"><span data-stu-id="95ef0-106">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95ef0-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="95ef0-107">Syntax</span></span>  
  
```cpp  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95ef0-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="95ef0-108">Parameters</span></span>  

 `name`  
 <span data-ttu-id="95ef0-109">окне Имя локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="95ef0-109">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="95ef0-110">окне Атрибуты локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="95ef0-110">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="95ef0-111">окне Маркер метаданных сигнатуры.</span><span class="sxs-lookup"><span data-stu-id="95ef0-111">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="95ef0-112">окне Тип адреса.</span><span class="sxs-lookup"><span data-stu-id="95ef0-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="95ef0-113">окне Первый адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="95ef0-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="95ef0-114">окне Второй адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="95ef0-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="95ef0-115">окне Третий адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="95ef0-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="95ef0-116">окне Начальное смещение для переменной.</span><span class="sxs-lookup"><span data-stu-id="95ef0-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="95ef0-117">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="95ef0-117">This parameter is optional.</span></span> <span data-ttu-id="95ef0-118">Если значение равно 0, этот параметр не учитывается, и переменная определяется всей областью.</span><span class="sxs-lookup"><span data-stu-id="95ef0-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="95ef0-119">Если это ненулевое значение, переменная попадает в диапазон смещений текущей области.</span><span class="sxs-lookup"><span data-stu-id="95ef0-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="95ef0-120">окне Конечное смещение для переменной.</span><span class="sxs-lookup"><span data-stu-id="95ef0-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="95ef0-121">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="95ef0-121">This parameter is optional.</span></span> <span data-ttu-id="95ef0-122">Если значение равно 0, этот параметр не учитывается, и переменная определяется всей областью.</span><span class="sxs-lookup"><span data-stu-id="95ef0-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="95ef0-123">Если это ненулевое значение, переменная попадает в диапазон смещений текущей области.</span><span class="sxs-lookup"><span data-stu-id="95ef0-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95ef0-124">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="95ef0-124">Return Value</span></span>  

 <span data-ttu-id="95ef0-125">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="95ef0-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95ef0-126">Требования</span><span class="sxs-lookup"><span data-stu-id="95ef0-126">Requirements</span></span>  

 <span data-ttu-id="95ef0-127">**Заголовок:** Корсим. idl</span><span class="sxs-lookup"><span data-stu-id="95ef0-127">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ef0-128">См. также</span><span class="sxs-lookup"><span data-stu-id="95ef0-128">See also</span></span>

- [<span data-ttu-id="95ef0-129">Интерфейс ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="95ef0-129">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="95ef0-130">Метод DefineLocalVariable</span><span class="sxs-lookup"><span data-stu-id="95ef0-130">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
