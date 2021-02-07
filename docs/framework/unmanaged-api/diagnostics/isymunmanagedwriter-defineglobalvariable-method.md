---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter::D Ефинеглобалвариабле'
title: Метод ISymUnmanagedWriter::DefineGlobalVariable
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: 70dccfed054a9ac79baf3f28683edc9a14d3cdf7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762387"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="cb52b-103">Метод ISymUnmanagedWriter::DefineGlobalVariable</span><span class="sxs-lookup"><span data-stu-id="cb52b-103">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>

<span data-ttu-id="cb52b-104">Определяет одну глобальную переменную.</span><span class="sxs-lookup"><span data-stu-id="cb52b-104">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb52b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cb52b-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb52b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cb52b-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="cb52b-107">окне Указатель на объект `WCHAR` , который определяет имя глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="cb52b-107">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="cb52b-108">окне Атрибуты глобальных переменных.</span><span class="sxs-lookup"><span data-stu-id="cb52b-108">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="cb52b-109">окне Значение типа `ULONG32` , указывающее размер буфера (в символах) `signature` .</span><span class="sxs-lookup"><span data-stu-id="cb52b-109">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="cb52b-110">окне Сигнатура глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="cb52b-110">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="cb52b-111">окне Тип адреса.</span><span class="sxs-lookup"><span data-stu-id="cb52b-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="cb52b-112">окне Первый адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="cb52b-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="cb52b-113">окне Второй адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="cb52b-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="cb52b-114">окне Третий адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="cb52b-114">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb52b-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cb52b-115">Return Value</span></span>  

 <span data-ttu-id="cb52b-116">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="cb52b-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb52b-117">Требования</span><span class="sxs-lookup"><span data-stu-id="cb52b-117">Requirements</span></span>  

 <span data-ttu-id="cb52b-118">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="cb52b-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb52b-119">См. также</span><span class="sxs-lookup"><span data-stu-id="cb52b-119">See also</span></span>

- [<span data-ttu-id="cb52b-120">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="cb52b-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="cb52b-121">Метод DefineLocalVariable</span><span class="sxs-lookup"><span data-stu-id="cb52b-121">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="cb52b-122">Метод DefineGlobalVariable2</span><span class="sxs-lookup"><span data-stu-id="cb52b-122">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)
