---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: GetHashFromAssemblyFile'
title: Метод ICLRStrongName::GetHashFromAssemblyFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
ms.openlocfilehash: 40a8e2aabe9ade00243c535d63389f4265cc6ab0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799707"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="30baf-103">Метод ICLRStrongName::GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="30baf-103">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>

<span data-ttu-id="30baf-104">Получает хэш указанного файла сборки с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="30baf-104">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30baf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="30baf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30baf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="30baf-106">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="30baf-107">окне Путь к файлу для хэширования.</span><span class="sxs-lookup"><span data-stu-id="30baf-107">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="30baf-108">[вход, выход] Константа, указывающая хэш-алгоритм.</span><span class="sxs-lookup"><span data-stu-id="30baf-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="30baf-109">Для алгоритма хэширования по умолчанию используется нуль.</span><span class="sxs-lookup"><span data-stu-id="30baf-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="30baf-110">заполняет Возвращаемый буфер хэша.</span><span class="sxs-lookup"><span data-stu-id="30baf-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="30baf-111">окне Запрошенный максимальный размер `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="30baf-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="30baf-112">заполняет Возвращаемый размер (в байтах) для `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="30baf-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30baf-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="30baf-113">Return Value</span></span>  

 <span data-ttu-id="30baf-114">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="30baf-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30baf-115">Требования</span><span class="sxs-lookup"><span data-stu-id="30baf-115">Requirements</span></span>  

 <span data-ttu-id="30baf-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30baf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30baf-117">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="30baf-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="30baf-118">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="30baf-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30baf-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30baf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30baf-120">См. также</span><span class="sxs-lookup"><span data-stu-id="30baf-120">See also</span></span>

- [<span data-ttu-id="30baf-121">Метод GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="30baf-121">GetHashFromAssemblyFileW Method</span></span>](iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="30baf-122">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="30baf-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
