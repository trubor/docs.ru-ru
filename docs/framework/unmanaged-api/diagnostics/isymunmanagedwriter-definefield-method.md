---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter::D Ефинефиелд'
title: Метод ISymUnmanagedWriter::DefineField
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
ms.openlocfilehash: f5bb47d4691780d94baf50cc9ceb3c14b1fa16ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762400"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="00d3c-103">Метод ISymUnmanagedWriter::DefineField</span><span class="sxs-lookup"><span data-stu-id="00d3c-103">ISymUnmanagedWriter::DefineField Method</span></span>

<span data-ttu-id="00d3c-104">Определяет одну переменную, не находящиеся в методе.</span><span class="sxs-lookup"><span data-stu-id="00d3c-104">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="00d3c-105">Этот метод используется для определенных полей в классах, битовых полях и т. д.</span><span class="sxs-lookup"><span data-stu-id="00d3c-105">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d3c-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="00d3c-106">Syntax</span></span>  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00d3c-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="00d3c-107">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="00d3c-108">окне Тип метаданных или токен метода.</span><span class="sxs-lookup"><span data-stu-id="00d3c-108">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="00d3c-109">окне Имя поля.</span><span class="sxs-lookup"><span data-stu-id="00d3c-109">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="00d3c-110">окне Атрибуты поля.</span><span class="sxs-lookup"><span data-stu-id="00d3c-110">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="00d3c-111">окне Объект `ULONG32` , который представляет собой размер (в символах) буфера, необходимого для хранения подписи поля.</span><span class="sxs-lookup"><span data-stu-id="00d3c-111">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="00d3c-112">окне Массив подписей полей.</span><span class="sxs-lookup"><span data-stu-id="00d3c-112">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="00d3c-113">окне Тип адреса.</span><span class="sxs-lookup"><span data-stu-id="00d3c-113">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="00d3c-114">окне Первый адрес для спецификации поля.</span><span class="sxs-lookup"><span data-stu-id="00d3c-114">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="00d3c-115">окне Второй адрес для спецификации поля.</span><span class="sxs-lookup"><span data-stu-id="00d3c-115">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="00d3c-116">окне Третий адрес для спецификации поля.</span><span class="sxs-lookup"><span data-stu-id="00d3c-116">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00d3c-117">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="00d3c-117">Return Value</span></span>  

 <span data-ttu-id="00d3c-118">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="00d3c-118">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00d3c-119">Требования</span><span class="sxs-lookup"><span data-stu-id="00d3c-119">Requirements</span></span>  

 <span data-ttu-id="00d3c-120">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="00d3c-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d3c-121">См. также</span><span class="sxs-lookup"><span data-stu-id="00d3c-121">See also</span></span>

- [<span data-ttu-id="00d3c-122">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="00d3c-122">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
