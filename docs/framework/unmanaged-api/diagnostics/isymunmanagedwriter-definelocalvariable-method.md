---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter::D Ефинелокалвариабле'
title: Метод ISymUnmanagedWriter::DefineLocalVariable
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
ms.openlocfilehash: cd817e3002c2a55fd8bbd7e565283752926f746b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762374"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="c2e16-103">Метод ISymUnmanagedWriter::DefineLocalVariable</span><span class="sxs-lookup"><span data-stu-id="c2e16-103">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>

<span data-ttu-id="c2e16-104">Определяет одну переменную в текущей лексической области видимости.</span><span class="sxs-lookup"><span data-stu-id="c2e16-104">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="c2e16-105">Этот метод может вызываться несколько раз для переменной с тем же именем, которая имеет несколько домов в пределах области.</span><span class="sxs-lookup"><span data-stu-id="c2e16-105">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="c2e16-106">Однако в этом случае значения `startOffset` `endOffset` параметров и не должны перекрываться.</span><span class="sxs-lookup"><span data-stu-id="c2e16-106">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2e16-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c2e16-107">Syntax</span></span>  
  
```cpp  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2e16-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="c2e16-108">Parameters</span></span>  

 `name`  
 <span data-ttu-id="c2e16-109">окне Указатель на объект `WCHAR` , который определяет имя локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="c2e16-109">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="c2e16-110">окне Атрибуты локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="c2e16-110">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="c2e16-111">окне Значение типа `ULONG32` , указывающее размер буфера (в байтах) `signature` .</span><span class="sxs-lookup"><span data-stu-id="c2e16-111">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="c2e16-112">окне Сигнатура локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="c2e16-112">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="c2e16-113">окне Тип адреса.</span><span class="sxs-lookup"><span data-stu-id="c2e16-113">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="c2e16-114">окне Первый адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="c2e16-114">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="c2e16-115">окне Второй адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="c2e16-115">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="c2e16-116">окне Третий адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="c2e16-116">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="c2e16-117">окне Начальное смещение для переменной.</span><span class="sxs-lookup"><span data-stu-id="c2e16-117">[in] The start offset for the variable.</span></span> <span data-ttu-id="c2e16-118">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="c2e16-118">This parameter is optional.</span></span> <span data-ttu-id="c2e16-119">Если значение равно 0, этот параметр не учитывается, и переменная определяется всей областью.</span><span class="sxs-lookup"><span data-stu-id="c2e16-119">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="c2e16-120">Если это ненулевое значение, переменная попадает в диапазон смещений текущей области.</span><span class="sxs-lookup"><span data-stu-id="c2e16-120">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="c2e16-121">окне Конечное смещение для переменной.</span><span class="sxs-lookup"><span data-stu-id="c2e16-121">[in] The end offset for the variable.</span></span> <span data-ttu-id="c2e16-122">Этот параметр является необязательным.</span><span class="sxs-lookup"><span data-stu-id="c2e16-122">This parameter is optional.</span></span> <span data-ttu-id="c2e16-123">Если значение равно 0, этот параметр не учитывается, и переменная определяется всей областью.</span><span class="sxs-lookup"><span data-stu-id="c2e16-123">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="c2e16-124">Если это ненулевое значение, переменная попадает в диапазон смещений текущей области.</span><span class="sxs-lookup"><span data-stu-id="c2e16-124">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2e16-125">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c2e16-125">Return Value</span></span>  

 <span data-ttu-id="c2e16-126">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="c2e16-126">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2e16-127">Требования</span><span class="sxs-lookup"><span data-stu-id="c2e16-127">Requirements</span></span>  

 <span data-ttu-id="c2e16-128">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="c2e16-128">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e16-129">См. также</span><span class="sxs-lookup"><span data-stu-id="c2e16-129">See also</span></span>

- [<span data-ttu-id="c2e16-130">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="c2e16-130">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="c2e16-131">Метод DefineGlobalVariable</span><span class="sxs-lookup"><span data-stu-id="c2e16-131">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="c2e16-132">Метод DefineLocalVariable2</span><span class="sxs-lookup"><span data-stu-id="c2e16-132">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)
