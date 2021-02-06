---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: GetHashFromFile'
title: Метод ICLRStrongName::GetHashFromFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: e930f1c21e5b0be441fe44ad352b2ef2f43d0f67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637057"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="d8006-103">Метод ICLRStrongName::GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="d8006-103">ICLRStrongName::GetHashFromFile Method</span></span>

<span data-ttu-id="d8006-104">Создает хэш содержимого указанного файла.</span><span class="sxs-lookup"><span data-stu-id="d8006-104">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8006-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d8006-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8006-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d8006-106">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="d8006-107">окне Имя файла для хэширования.</span><span class="sxs-lookup"><span data-stu-id="d8006-107">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d8006-108">[вход, выход] Алгоритм, используемый при формировании хэша.</span><span class="sxs-lookup"><span data-stu-id="d8006-108">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="d8006-109">Допустимыми являются алгоритмы, определяемые интерфейсом Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="d8006-109">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="d8006-110">Если параметр `piHashAlg` имеет значение 0, используется алгоритм по умолчанию CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="d8006-110">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d8006-111">заполняет Массив байтов, содержащий созданный хэш.</span><span class="sxs-lookup"><span data-stu-id="d8006-111">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d8006-112">окне Максимальный размер буфера, `pbHash` на который указывает.</span><span class="sxs-lookup"><span data-stu-id="d8006-112">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d8006-113">заполняет Размер возвращаемого объекта (в байтах) `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="d8006-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8006-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d8006-114">Return Value</span></span>  

 <span data-ttu-id="d8006-115">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="d8006-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8006-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="d8006-116">Remarks</span></span>  

 <span data-ttu-id="d8006-117">Этот метод аналогичен методу [метод iclrstrongname:: GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) , за исключением того, что спецификация имени файла является ANSI, а не Unicode.</span><span class="sxs-lookup"><span data-stu-id="d8006-117">This method is the same as the [ICLRStrongName::GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8006-118">Требования</span><span class="sxs-lookup"><span data-stu-id="d8006-118">Requirements</span></span>  

 <span data-ttu-id="d8006-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8006-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8006-120">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="d8006-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d8006-121">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d8006-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8006-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8006-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8006-123">См. также</span><span class="sxs-lookup"><span data-stu-id="d8006-123">See also</span></span>

- [<span data-ttu-id="d8006-124">Метод GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="d8006-124">GetHashFromFileW Method</span></span>](iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="d8006-125">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="d8006-125">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
