---
description: 'Дополнительные сведения о методе: ISymUnmanagedNamespace:: Name'
title: Метод ISymUnmanagedNamespace::GetName
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: f4d366363cd089995f98039389f59077e949fb79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721220"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="93ec0-103">Метод ISymUnmanagedNamespace::GetName</span><span class="sxs-lookup"><span data-stu-id="93ec0-103">ISymUnmanagedNamespace::GetName Method</span></span>

<span data-ttu-id="93ec0-104">Возвращает имя этого пространства имен.</span><span class="sxs-lookup"><span data-stu-id="93ec0-104">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93ec0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="93ec0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93ec0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="93ec0-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="93ec0-107">окне Значение типа `ULONG32` , указывающее размер `szName` буфера.</span><span class="sxs-lookup"><span data-stu-id="93ec0-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="93ec0-108">заполняет Указатель на объект `ULONG32` , который получает размер (в символах) буфера, необходимого для хранения имени пространства имен, включая завершение значения NULL.</span><span class="sxs-lookup"><span data-stu-id="93ec0-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="93ec0-109">заполняет Указатель на буфер, содержащий имя пространства имен.</span><span class="sxs-lookup"><span data-stu-id="93ec0-109">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93ec0-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="93ec0-110">Return Value</span></span>  

 <span data-ttu-id="93ec0-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="93ec0-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93ec0-112">Требования</span><span class="sxs-lookup"><span data-stu-id="93ec0-112">Requirements</span></span>  

 <span data-ttu-id="93ec0-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="93ec0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ec0-114">См. также</span><span class="sxs-lookup"><span data-stu-id="93ec0-114">See also</span></span>

- [<span data-ttu-id="93ec0-115">Интерфейс ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="93ec0-115">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
