---
description: 'Дополнительные сведения о методе: ISymENCUnmanagedMethod:: GetFileNameFromOffset'
title: Метод ISymENCUnmanagedMethod::GetFileNameFromOffset
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: 1322e55f115958a2f4b2634dfa25eff127167d54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738004"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="a2ec3-103">Метод ISymENCUnmanagedMethod::GetFileNameFromOffset</span><span class="sxs-lookup"><span data-stu-id="a2ec3-103">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>

<span data-ttu-id="a2ec3-104">Возвращает имя файла для строки, связанной со смещением.</span><span class="sxs-lookup"><span data-stu-id="a2ec3-104">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2ec3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a2ec3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2ec3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a2ec3-106">Parameters</span></span>  

 `dwOffset`  
 <span data-ttu-id="a2ec3-107">окне Значение типа `ULONG32` , содержащее смещение.</span><span class="sxs-lookup"><span data-stu-id="a2ec3-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a2ec3-108">окне Значение типа `ULONG32` , указывающее размер `szName` буфера.</span><span class="sxs-lookup"><span data-stu-id="a2ec3-108">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a2ec3-109">заполняет Указатель на объект `ULONG32` , который получает размер (в символах) буфера, необходимого для хранения имен файлов.</span><span class="sxs-lookup"><span data-stu-id="a2ec3-109">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="a2ec3-110">заполняет Буфер, содержащий имена файлов.</span><span class="sxs-lookup"><span data-stu-id="a2ec3-110">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2ec3-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a2ec3-111">Return Value</span></span>  

 <span data-ttu-id="a2ec3-112">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="a2ec3-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2ec3-113">Требования</span><span class="sxs-lookup"><span data-stu-id="a2ec3-113">Requirements</span></span>  

 <span data-ttu-id="a2ec3-114">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="a2ec3-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ec3-115">См. также</span><span class="sxs-lookup"><span data-stu-id="a2ec3-115">See also</span></span>

- [<span data-ttu-id="a2ec3-116">Интерфейс ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="a2ec3-116">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
