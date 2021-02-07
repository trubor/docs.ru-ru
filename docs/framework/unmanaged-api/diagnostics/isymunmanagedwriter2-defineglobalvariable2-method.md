---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter2::D efineGlobalVariable2'
title: Метод ISymUnmanagedWriter2::DefineGlobalVariable2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
ms.openlocfilehash: 9a33ff8d452419ff103c9f4402620bd28196ae54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761906"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="89e1f-103">Метод ISymUnmanagedWriter2::DefineGlobalVariable2</span><span class="sxs-lookup"><span data-stu-id="89e1f-103">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>

<span data-ttu-id="89e1f-104">Определяет одну глобальную переменную.</span><span class="sxs-lookup"><span data-stu-id="89e1f-104">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e1f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="89e1f-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89e1f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="89e1f-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="89e1f-107">окне Имя глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="89e1f-107">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="89e1f-108">окне Атрибуты глобальных переменных.</span><span class="sxs-lookup"><span data-stu-id="89e1f-108">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="89e1f-109">окне Маркер метаданных сигнатуры.</span><span class="sxs-lookup"><span data-stu-id="89e1f-109">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="89e1f-110">окне Тип адреса.</span><span class="sxs-lookup"><span data-stu-id="89e1f-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="89e1f-111">окне Первый адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="89e1f-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="89e1f-112">окне Второй адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="89e1f-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="89e1f-113">окне Третий адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="89e1f-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89e1f-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="89e1f-114">Return Value</span></span>  

 <span data-ttu-id="89e1f-115">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="89e1f-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89e1f-116">Требования</span><span class="sxs-lookup"><span data-stu-id="89e1f-116">Requirements</span></span>  

 <span data-ttu-id="89e1f-117">**Заголовок:** Корсим. idl</span><span class="sxs-lookup"><span data-stu-id="89e1f-117">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e1f-118">См. также</span><span class="sxs-lookup"><span data-stu-id="89e1f-118">See also</span></span>

- [<span data-ttu-id="89e1f-119">Интерфейс ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="89e1f-119">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="89e1f-120">Метод DefineGlobalVariable</span><span class="sxs-lookup"><span data-stu-id="89e1f-120">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
