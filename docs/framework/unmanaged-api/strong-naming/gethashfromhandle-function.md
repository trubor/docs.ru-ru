---
description: Дополнительные сведения о функции GetHashFromHandle
title: Функция GetHashFromHandle
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
ms.openlocfilehash: 5951a5befd9e66b13a3b3033398614fca1f1a9d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736572"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="a456c-103">Функция GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="a456c-103">GetHashFromHandle Function</span></span>

<span data-ttu-id="a456c-104">Создает хэш содержимого файла с заданным дескриптором файла с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="a456c-104">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="a456c-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="a456c-105">This function has been deprecated.</span></span> <span data-ttu-id="a456c-106">Используйте вместо этого метод [метод iclrstrongname:: GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a456c-106">Use the [ICLRStrongName::GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a456c-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a456c-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a456c-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="a456c-108">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="a456c-109">окне Описатель файла для хэширования.</span><span class="sxs-lookup"><span data-stu-id="a456c-109">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="a456c-110">[вход, выход] Константа, указывающая хэш-алгоритм.</span><span class="sxs-lookup"><span data-stu-id="a456c-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="a456c-111">Используйте нуль для алгоритма по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a456c-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="a456c-112">заполняет Возвращаемый буфер хэша.</span><span class="sxs-lookup"><span data-stu-id="a456c-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="a456c-113">окне Запрошенный максимальный размер `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="a456c-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="a456c-114">заполняет Размер возвращаемого объекта (в байтах) `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="a456c-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a456c-115">Требования</span><span class="sxs-lookup"><span data-stu-id="a456c-115">Requirements</span></span>  

 <span data-ttu-id="a456c-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a456c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a456c-117">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="a456c-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a456c-118">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a456c-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a456c-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a456c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a456c-120">См. также</span><span class="sxs-lookup"><span data-stu-id="a456c-120">See also</span></span>

- [<span data-ttu-id="a456c-121">Метод GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="a456c-121">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="a456c-122">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a456c-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
