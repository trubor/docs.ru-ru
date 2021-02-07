---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: Сетсиматтрибуте'
title: Метод ISymUnmanagedWriter::SetSymAttribute
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
ms.openlocfilehash: 0509e6430646fa67112b29d30d5053eb4a541415
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761997"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="88a44-103">Метод ISymUnmanagedWriter::SetSymAttribute</span><span class="sxs-lookup"><span data-stu-id="88a44-103">ISymUnmanagedWriter::SetSymAttribute Method</span></span>

<span data-ttu-id="88a44-104">Определяет настраиваемый атрибут на основе его имени.</span><span class="sxs-lookup"><span data-stu-id="88a44-104">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="88a44-105">Эти атрибуты хранятся в хранилище символов в отличие от пользовательских атрибутов метаданных.</span><span class="sxs-lookup"><span data-stu-id="88a44-105">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88a44-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="88a44-106">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88a44-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="88a44-107">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="88a44-108">окне Токен метаданных, для которого определяется атрибут.</span><span class="sxs-lookup"><span data-stu-id="88a44-108">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="88a44-109">окне Указатель на объект `WCHAR` , содержащий имя атрибута.</span><span class="sxs-lookup"><span data-stu-id="88a44-109">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="88a44-110">окне Значение типа `ULONG32` , указывающее размер `data` массива.</span><span class="sxs-lookup"><span data-stu-id="88a44-110">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="88a44-111">окне Значение атрибута.</span><span class="sxs-lookup"><span data-stu-id="88a44-111">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88a44-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="88a44-112">Return Value</span></span>  

 <span data-ttu-id="88a44-113">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="88a44-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88a44-114">Требования</span><span class="sxs-lookup"><span data-stu-id="88a44-114">Requirements</span></span>  

 <span data-ttu-id="88a44-115">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="88a44-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a44-116">См. также</span><span class="sxs-lookup"><span data-stu-id="88a44-116">See also</span></span>

- [<span data-ttu-id="88a44-117">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="88a44-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
