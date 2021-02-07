---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: GetSymbolStoreFileName'
title: Метод ISymUnmanagedReader::GetSymbolStoreFileName
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
ms.openlocfilehash: 5cbb33a39cf2e93eab64d5f1f1fefc5ceba1d418
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763947"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="f0536-103">Метод ISymUnmanagedReader::GetSymbolStoreFileName</span><span class="sxs-lookup"><span data-stu-id="f0536-103">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>

<span data-ttu-id="f0536-104">Предоставляет имя файла на диске для хранилища символов.</span><span class="sxs-lookup"><span data-stu-id="f0536-104">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0536-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f0536-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0536-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f0536-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="f0536-107">окне Размер `szName` буфера.</span><span class="sxs-lookup"><span data-stu-id="f0536-107">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f0536-108">заполняет Указатель на переменную, которая получает длину имени, возвращаемого в `szName` , включая завершение значения NULL.</span><span class="sxs-lookup"><span data-stu-id="f0536-108">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="f0536-109">заполняет Указатель на переменную, которая получает имя файла хранилища символов.</span><span class="sxs-lookup"><span data-stu-id="f0536-109">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0536-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f0536-110">Return Value</span></span>  

 <span data-ttu-id="f0536-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="f0536-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0536-112">Требования</span><span class="sxs-lookup"><span data-stu-id="f0536-112">Requirements</span></span>  

 <span data-ttu-id="f0536-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="f0536-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0536-114">См. также</span><span class="sxs-lookup"><span data-stu-id="f0536-114">See also</span></span>

- [<span data-ttu-id="f0536-115">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="f0536-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
