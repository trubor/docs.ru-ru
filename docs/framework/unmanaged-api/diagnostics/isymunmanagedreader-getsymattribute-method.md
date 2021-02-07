---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: GetSymAttribute'
title: Метод ISymUnmanagedReader::GetSymAttribute
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
ms.openlocfilehash: cd1c453e9f2ef68799fc5eccf1288a7665c5cfdf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763973"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="38b95-103">Метод ISymUnmanagedReader::GetSymAttribute</span><span class="sxs-lookup"><span data-stu-id="38b95-103">ISymUnmanagedReader::GetSymAttribute Method</span></span>

<span data-ttu-id="38b95-104">Возвращает настраиваемый атрибут на основе его имени.</span><span class="sxs-lookup"><span data-stu-id="38b95-104">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="38b95-105">В отличие от пользовательских атрибутов метаданных эти пользовательские атрибуты хранятся в хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="38b95-105">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38b95-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="38b95-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38b95-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="38b95-107">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="38b95-108">окне Токен метаданных для объекта, для которого запрашивается атрибут.</span><span class="sxs-lookup"><span data-stu-id="38b95-108">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="38b95-109">окне Указатель на переменную, которая указывает извлекаемый атрибут.</span><span class="sxs-lookup"><span data-stu-id="38b95-109">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="38b95-110">[in] Размер массива `buffer`.</span><span class="sxs-lookup"><span data-stu-id="38b95-110">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="38b95-111">заполняет Указатель на переменную, которая получает длину данных атрибута.</span><span class="sxs-lookup"><span data-stu-id="38b95-111">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="38b95-112">заполняет Указатель на переменную, которая получает данные атрибута.</span><span class="sxs-lookup"><span data-stu-id="38b95-112">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38b95-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="38b95-113">Return Value</span></span>  

 <span data-ttu-id="38b95-114">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="38b95-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38b95-115">Требования</span><span class="sxs-lookup"><span data-stu-id="38b95-115">Requirements</span></span>  

 <span data-ttu-id="38b95-116">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="38b95-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38b95-117">См. также</span><span class="sxs-lookup"><span data-stu-id="38b95-117">See also</span></span>

- [<span data-ttu-id="38b95-118">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="38b95-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
