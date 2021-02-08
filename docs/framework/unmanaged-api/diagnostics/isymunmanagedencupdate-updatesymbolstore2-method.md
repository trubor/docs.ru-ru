---
description: 'Дополнительные сведения о методе: ISymUnmanagedENCUpdate:: UpdateSymbolStore2'
title: Метод ISymUnmanagedENCUpdate::UpdateSymbolStore2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
ms.openlocfilehash: f2e5cbf51c1bab3a538fbf5a3e5824739fa3b250
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790143"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="40b52-103">Метод ISymUnmanagedENCUpdate::UpdateSymbolStore2</span><span class="sxs-lookup"><span data-stu-id="40b52-103">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>

<span data-ttu-id="40b52-104">Позволяет компилятору опускать функции, которые не были изменены из потока базы данных программы (PDB), при условии, что сведения о строке соответствуют требованиям.</span><span class="sxs-lookup"><span data-stu-id="40b52-104">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="40b52-105">Правильная информация о строке может быть определена со старыми сведениями о строке PDB и одной разностью для всех строк в функции.</span><span class="sxs-lookup"><span data-stu-id="40b52-105">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40b52-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="40b52-106">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40b52-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="40b52-107">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="40b52-108">окне Указатель на объект [IStream](/windows/desktop/api/objidl/nn-objidl-istream) , содержащий сведения о строке.</span><span class="sxs-lookup"><span data-stu-id="40b52-108">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="40b52-109">окне Указатель на структуру [SYMLINEDELTA](symlinedelta-structure.md) , содержащую измененные строки.</span><span class="sxs-lookup"><span data-stu-id="40b52-109">[in] A pointer to a [SYMLINEDELTA](symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="40b52-110">окне Объект `ULONG` , представляющий число измененных строк.</span><span class="sxs-lookup"><span data-stu-id="40b52-110">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40b52-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="40b52-111">Return Value</span></span>  

 <span data-ttu-id="40b52-112">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="40b52-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40b52-113">Требования</span><span class="sxs-lookup"><span data-stu-id="40b52-113">Requirements</span></span>  

 <span data-ttu-id="40b52-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="40b52-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40b52-115">См. также</span><span class="sxs-lookup"><span data-stu-id="40b52-115">See also</span></span>

- [<span data-ttu-id="40b52-116">Интерфейс ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="40b52-116">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
