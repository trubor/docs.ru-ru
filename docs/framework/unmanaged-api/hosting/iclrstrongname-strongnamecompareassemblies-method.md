---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameCompareAssemblies'
title: Метод ICLRStrongName::StrongNameCompareAssemblies
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: ab02312073f9caf5059ecf7b4eeddaef864bd7b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799657"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="ade44-103">Метод ICLRStrongName::StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="ade44-103">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>

<span data-ttu-id="ade44-104">Определяет, отличаются ли две сборки только подписями строгого имени.</span><span class="sxs-lookup"><span data-stu-id="ade44-104">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ade44-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ade44-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ade44-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ade44-106">Parameters</span></span>  

 `wszAssembly1`  
 <span data-ttu-id="ade44-107">окне Путь к первой сборке.</span><span class="sxs-lookup"><span data-stu-id="ade44-107">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="ade44-108">окне Путь к второй сборке.</span><span class="sxs-lookup"><span data-stu-id="ade44-108">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="ade44-109">заполняет Одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="ade44-109">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="ade44-110">`SN_CMP_DIFFERENT` (0) — указывает, что сборки содержат различные данные.</span><span class="sxs-lookup"><span data-stu-id="ade44-110">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="ade44-111">`SN_CMP_IDENTICAL` (1) — указывает, что сборки точно одинаковы, включая их подписи и контрольные суммы.</span><span class="sxs-lookup"><span data-stu-id="ade44-111">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="ade44-112">`SN_CMP_SIGONLY` (2) — указывает, что сборки отличаются только сигнатурой и контрольной суммой.</span><span class="sxs-lookup"><span data-stu-id="ade44-112">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ade44-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ade44-113">Return Value</span></span>  

 <span data-ttu-id="ade44-114">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="ade44-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ade44-115">Требования</span><span class="sxs-lookup"><span data-stu-id="ade44-115">Requirements</span></span>  

 <span data-ttu-id="ade44-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ade44-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ade44-117">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="ade44-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ade44-118">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ade44-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ade44-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ade44-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ade44-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="ade44-120">Remarks</span></span>  

 <span data-ttu-id="ade44-121">Подпись строгого имени сборки состоит из текстового имени, версии, языка и региональных параметров сборки, а также токена открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="ade44-121">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade44-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ade44-122">See also</span></span>

- [<span data-ttu-id="ade44-123">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ade44-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
