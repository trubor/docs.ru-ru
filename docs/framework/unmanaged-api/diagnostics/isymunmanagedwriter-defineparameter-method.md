---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter::D Ефинепараметер'
title: Метод ISymUnmanagedWriter::DefineParameter
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
ms.openlocfilehash: 1e42140e33a99b224ccf3eff7ea29b7aa3ff1b15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762361"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="90e7a-103">Метод ISymUnmanagedWriter::DefineParameter</span><span class="sxs-lookup"><span data-stu-id="90e7a-103">ISymUnmanagedWriter::DefineParameter Method</span></span>

<span data-ttu-id="90e7a-104">Определяет один параметр в текущем методе.</span><span class="sxs-lookup"><span data-stu-id="90e7a-104">Defines a single parameter in the current method.</span></span> <span data-ttu-id="90e7a-105">Тип параметра берется из расположения параметра (Sequence) в сигнатуре метода.</span><span class="sxs-lookup"><span data-stu-id="90e7a-105">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="90e7a-106">Если в метаданных для данного метода определены параметры, их не нужно определять повторно с помощью этого метода.</span><span class="sxs-lookup"><span data-stu-id="90e7a-106">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="90e7a-107">Прежде чем проверять хранилище символов, средства чтения символов должны проверить обычные метаданные для параметров.</span><span class="sxs-lookup"><span data-stu-id="90e7a-107">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90e7a-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="90e7a-108">Syntax</span></span>  
  
```cpp  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90e7a-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="90e7a-109">Parameters</span></span>  

 `name`  
 <span data-ttu-id="90e7a-110">окне Имя параметра.</span><span class="sxs-lookup"><span data-stu-id="90e7a-110">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="90e7a-111">окне Атрибуты параметра.</span><span class="sxs-lookup"><span data-stu-id="90e7a-111">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="90e7a-112">окне Сигнатура параметра.</span><span class="sxs-lookup"><span data-stu-id="90e7a-112">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="90e7a-113">окне Тип адреса.</span><span class="sxs-lookup"><span data-stu-id="90e7a-113">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="90e7a-114">окне Первый адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="90e7a-114">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="90e7a-115">окне Второй адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="90e7a-115">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="90e7a-116">окне Третий адрес для спецификации параметра.</span><span class="sxs-lookup"><span data-stu-id="90e7a-116">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90e7a-117">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="90e7a-117">Return Value</span></span>  

 <span data-ttu-id="90e7a-118">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="90e7a-118">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90e7a-119">Требования</span><span class="sxs-lookup"><span data-stu-id="90e7a-119">Requirements</span></span>  

 <span data-ttu-id="90e7a-120">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="90e7a-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e7a-121">См. также</span><span class="sxs-lookup"><span data-stu-id="90e7a-121">See also</span></span>

- [<span data-ttu-id="90e7a-122">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="90e7a-122">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
