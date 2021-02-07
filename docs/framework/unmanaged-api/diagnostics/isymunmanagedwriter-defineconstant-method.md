---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter::D Ефинеконстант'
title: Метод ISymUnmanagedWriter::DefineConstant
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
ms.openlocfilehash: 4c3fd3986d42061272406150422f037236c4b9bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762530"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="c2ef6-103">Метод ISymUnmanagedWriter::DefineConstant</span><span class="sxs-lookup"><span data-stu-id="c2ef6-103">ISymUnmanagedWriter::DefineConstant Method</span></span>

<span data-ttu-id="c2ef6-104">Определяет имя для постоянного значения.</span><span class="sxs-lookup"><span data-stu-id="c2ef6-104">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2ef6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c2ef6-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2ef6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c2ef6-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="c2ef6-107">окне Указатель на объект `WCHAR` , который определяет имя константы.</span><span class="sxs-lookup"><span data-stu-id="c2ef6-107">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="c2ef6-108">окне Значение константы.</span><span class="sxs-lookup"><span data-stu-id="c2ef6-108">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="c2ef6-109">[in] Размер массива `signature`.</span><span class="sxs-lookup"><span data-stu-id="c2ef6-109">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="c2ef6-110">окне Сигнатура типа для константы.</span><span class="sxs-lookup"><span data-stu-id="c2ef6-110">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2ef6-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c2ef6-111">Return Value</span></span>  

 <span data-ttu-id="c2ef6-112">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="c2ef6-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2ef6-113">Требования</span><span class="sxs-lookup"><span data-stu-id="c2ef6-113">Requirements</span></span>  

 <span data-ttu-id="c2ef6-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="c2ef6-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ef6-115">См. также</span><span class="sxs-lookup"><span data-stu-id="c2ef6-115">See also</span></span>

- [<span data-ttu-id="c2ef6-116">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="c2ef6-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="c2ef6-117">Метод DefineConstant2</span><span class="sxs-lookup"><span data-stu-id="c2ef6-117">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)
