---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: GetHashFromFileW'
title: Метод ICLRStrongName::GetHashFromFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
ms.openlocfilehash: 6145a044f490ef3827de6db8d84d16222306642d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636979"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="41846-103">Метод ICLRStrongName::GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="41846-103">ICLRStrongName::GetHashFromFileW Method</span></span>

<span data-ttu-id="41846-104">Создает хэш содержимого файла, указанного строкой Юникода.</span><span class="sxs-lookup"><span data-stu-id="41846-104">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41846-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="41846-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="41846-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="41846-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="41846-107">окне Имя файла в Юникоде для хэширования.</span><span class="sxs-lookup"><span data-stu-id="41846-107">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="41846-108">[вход, выход] Алгоритм, используемый при формировании хэша.</span><span class="sxs-lookup"><span data-stu-id="41846-108">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="41846-109">Допустимыми являются алгоритмы, определяемые интерфейсом Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="41846-109">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="41846-110">Если параметр `piHashAlg` имеет значение 0, используется алгоритм по умолчанию CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="41846-110">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="41846-111">заполняет Массив байтов, содержащий созданный хэш.</span><span class="sxs-lookup"><span data-stu-id="41846-111">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="41846-112">окне Максимальный размер буфера, на который указывает `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="41846-112">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="41846-113">заполняет Размер (в байтах) `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="41846-113">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41846-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="41846-114">Return Value</span></span>  

 <span data-ttu-id="41846-115">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="41846-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41846-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="41846-116">Remarks</span></span>  

 <span data-ttu-id="41846-117">Этот метод аналогичен методу [метод iclrstrongname:: GetHashFromFile](iclrstrongname-gethashfromfile-method.md) , за исключением того, что спецификация имени файла имеет кодировку Unicode, а не ANSI.</span><span class="sxs-lookup"><span data-stu-id="41846-117">This method is the same as the [ICLRStrongName::GetHashFromFile](iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41846-118">Требования</span><span class="sxs-lookup"><span data-stu-id="41846-118">Requirements</span></span>  

 <span data-ttu-id="41846-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41846-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41846-120">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="41846-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="41846-121">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41846-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41846-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41846-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41846-123">См. также</span><span class="sxs-lookup"><span data-stu-id="41846-123">See also</span></span>

- [<span data-ttu-id="41846-124">Метод GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="41846-124">GetHashFromFile Method</span></span>](iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="41846-125">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="41846-125">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
