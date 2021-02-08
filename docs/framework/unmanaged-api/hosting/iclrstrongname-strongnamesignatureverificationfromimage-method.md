---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameSignatureVerificationFromImage'
title: Метод ICLRStrongName::StrongNameSignatureVerificationFromImage
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
ms.openlocfilehash: 5c1c3568dd0ad506c478525503f168d8b8c2dfbc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781835"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="6aa74-103">Метод ICLRStrongName::StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="6aa74-103">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>

<span data-ttu-id="6aa74-104">Проверяет допустимость сборки, которая уже была сопоставлена с памятью, для связанного открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="6aa74-104">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aa74-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6aa74-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aa74-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6aa74-106">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="6aa74-107">окне Относительный виртуальный адрес сопоставленного манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="6aa74-107">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="6aa74-108">окне Размер сопоставленного изображения в байтах.</span><span class="sxs-lookup"><span data-stu-id="6aa74-108">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="6aa74-109">окне Флаги, влияющие на поведение при проверке.</span><span class="sxs-lookup"><span data-stu-id="6aa74-109">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="6aa74-110">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="6aa74-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="6aa74-111">`SN_INFLAG_FORCE_VER` (0x00000001) — принудительная проверка, даже если необходимо переопределить параметры реестра.</span><span class="sxs-lookup"><span data-stu-id="6aa74-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="6aa74-112">`SN_INFLAG_INSTALL` (0x00000002) — указывает, что это первая проверка, выполняемая на этом образе.</span><span class="sxs-lookup"><span data-stu-id="6aa74-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="6aa74-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) — указывает, что кэш будет разрешать доступ только тем пользователям, у которых есть права администратора.</span><span class="sxs-lookup"><span data-stu-id="6aa74-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="6aa74-114">`SN_INFLAG_USER_ACCESS` (0x00000008) — указывает, что сборка будет доступна только текущему пользователю.</span><span class="sxs-lookup"><span data-stu-id="6aa74-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="6aa74-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) — указывает, что кэш не предоставляет никаких гарантий ограничения доступа.</span><span class="sxs-lookup"><span data-stu-id="6aa74-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="6aa74-116">`SN_INFLAG_RUNTIME` (0x80000000) — зарезервировано для внутренней отладки.</span><span class="sxs-lookup"><span data-stu-id="6aa74-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="6aa74-117">заполняет Флаг для дополнительных выходных данных.</span><span class="sxs-lookup"><span data-stu-id="6aa74-117">[out] A flag for additional output information.</span></span> <span data-ttu-id="6aa74-118">Поддерживается следующее значение:</span><span class="sxs-lookup"><span data-stu-id="6aa74-118">The following value is supported:</span></span>  
  
- <span data-ttu-id="6aa74-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — это значение `false` указывает, что проверка прошла удачно из-за параметров реестра.</span><span class="sxs-lookup"><span data-stu-id="6aa74-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6aa74-120">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6aa74-120">Return Value</span></span>  

 <span data-ttu-id="6aa74-121">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="6aa74-121">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aa74-122">Требования</span><span class="sxs-lookup"><span data-stu-id="6aa74-122">Requirements</span></span>  

 <span data-ttu-id="6aa74-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6aa74-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aa74-124">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="6aa74-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6aa74-125">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6aa74-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6aa74-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aa74-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa74-127">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6aa74-127">See also</span></span>

- [<span data-ttu-id="6aa74-128">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="6aa74-128">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
