---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: GetHashFromAssemblyFileW'
title: Метод ICLRStrongName::GetHashFromAssemblyFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
ms.openlocfilehash: 27123ed8217d49765fe3fd7c19efc92f4e770722
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637083"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="269ff-103">Метод ICLRStrongName::GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="269ff-103">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>

<span data-ttu-id="269ff-104">Создает хэш содержимого файла, указанного строкой Юникода.</span><span class="sxs-lookup"><span data-stu-id="269ff-104">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="269ff-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="269ff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="269ff-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="269ff-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="269ff-107">окне Путь к файлу для хэширования.</span><span class="sxs-lookup"><span data-stu-id="269ff-107">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="269ff-108">Этот параметр должен быть строкой в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="269ff-108">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="269ff-109">[вход, выход] Константа, указывающая хэш-алгоритм.</span><span class="sxs-lookup"><span data-stu-id="269ff-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="269ff-110">Для алгоритма хэширования по умолчанию используется нуль.</span><span class="sxs-lookup"><span data-stu-id="269ff-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="269ff-111">заполняет Возвращаемый буфер хэша.</span><span class="sxs-lookup"><span data-stu-id="269ff-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="269ff-112">окне Запрошенный максимальный размер `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="269ff-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="269ff-113">заполняет Возвращаемый размер (в байтах) для `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="269ff-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="269ff-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="269ff-114">Return Value</span></span>  

 <span data-ttu-id="269ff-115">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="269ff-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="269ff-116">Требования</span><span class="sxs-lookup"><span data-stu-id="269ff-116">Requirements</span></span>  

 <span data-ttu-id="269ff-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="269ff-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="269ff-118">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="269ff-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="269ff-119">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="269ff-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="269ff-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="269ff-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="269ff-121">См. также</span><span class="sxs-lookup"><span data-stu-id="269ff-121">See also</span></span>

- [<span data-ttu-id="269ff-122">Метод GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="269ff-122">GetHashFromAssemblyFile Method</span></span>](iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="269ff-123">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="269ff-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
