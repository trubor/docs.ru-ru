---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader2:: GetSymAttributePreRemap'
title: Метод ISymUnmanagedReader2::GetSymAttributePreRemap
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: 843a3d2d2a568fdff83d2e416fff426daad14645
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763635"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="a3b71-103">Метод ISymUnmanagedReader2::GetSymAttributePreRemap</span><span class="sxs-lookup"><span data-stu-id="a3b71-103">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>

<span data-ttu-id="a3b71-104">Возвращает настраиваемый атрибут на основе его имени.</span><span class="sxs-lookup"><span data-stu-id="a3b71-104">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="a3b71-105">В отличие от пользовательских атрибутов метаданных эти атрибуты хранятся в хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="a3b71-105">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3b71-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a3b71-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3b71-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="a3b71-107">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="a3b71-108">окне Маркер метаданных родителя.</span><span class="sxs-lookup"><span data-stu-id="a3b71-108">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="a3b71-109">окне Указатель на объект `WCHAR` , содержащий имя.</span><span class="sxs-lookup"><span data-stu-id="a3b71-109">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="a3b71-110">окне Значение типа `ULONG32` , указывающее размер `buffer` массива.</span><span class="sxs-lookup"><span data-stu-id="a3b71-110">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="a3b71-111">заполняет Указатель на объект `ULONG32` , который получает размер буфера, необходимого для хранения байтов атрибута.</span><span class="sxs-lookup"><span data-stu-id="a3b71-111">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="a3b71-112">заполняет Указатель на буфер, который получает байты атрибута.</span><span class="sxs-lookup"><span data-stu-id="a3b71-112">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3b71-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a3b71-113">Return Value</span></span>  

 <span data-ttu-id="a3b71-114">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="a3b71-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3b71-115">Требования</span><span class="sxs-lookup"><span data-stu-id="a3b71-115">Requirements</span></span>  

 <span data-ttu-id="a3b71-116">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="a3b71-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b71-117">См. также</span><span class="sxs-lookup"><span data-stu-id="a3b71-117">See also</span></span>

- [<span data-ttu-id="a3b71-118">Интерфейс ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="a3b71-118">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
