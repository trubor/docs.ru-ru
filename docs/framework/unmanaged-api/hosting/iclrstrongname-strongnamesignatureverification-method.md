---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameSignatureVerification'
title: Метод ICLRStrongName::StrongNameSignatureVerification
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
ms.openlocfilehash: 985a00ffe464f2dd6a92c299dae14206fd37a898
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781848"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="9c079-103">Метод ICLRStrongName::StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="9c079-103">ICLRStrongName::StrongNameSignatureVerification Method</span></span>

<span data-ttu-id="9c079-104">Возвращает значение, указывающее, содержит ли манифест сборки по указанному пути подпись строгого имени, которая проверяется в соответствии с заданными флагами.</span><span class="sxs-lookup"><span data-stu-id="9c079-104">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c079-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9c079-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c079-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9c079-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="9c079-107">окне Путь к переносимому исполняемому файлу (DLL или exe), для которого проверяется сборка.</span><span class="sxs-lookup"><span data-stu-id="9c079-107">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="9c079-108">окне Флаги для изменения поведения проверки.</span><span class="sxs-lookup"><span data-stu-id="9c079-108">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="9c079-109">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="9c079-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="9c079-110">`SN_INFLAG_FORCE_VER` (0x00000001) — принудительная проверка, даже если необходимо переопределить параметры реестра.</span><span class="sxs-lookup"><span data-stu-id="9c079-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="9c079-111">`SN_INFLAG_INSTALL` (0x00000002) — указывает, что это первый раз при проверке манифеста.</span><span class="sxs-lookup"><span data-stu-id="9c079-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="9c079-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) — указывает, что кэш будет разрешать доступ только тем пользователям, у которых есть права администратора.</span><span class="sxs-lookup"><span data-stu-id="9c079-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="9c079-113">`SN_INFLAG_USER_ACCESS` (0x00000008) — указывает, что сборка будет доступна только текущему пользователю.</span><span class="sxs-lookup"><span data-stu-id="9c079-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="9c079-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) — указывает, что кэш не предоставляет никаких гарантий ограничения доступа.</span><span class="sxs-lookup"><span data-stu-id="9c079-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="9c079-115">`SN_INFLAG_RUNTIME` (0x80000000) — зарезервировано для внутренней отладки.</span><span class="sxs-lookup"><span data-stu-id="9c079-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="9c079-116">заполняет Флаги, указывающие, была ли проверена подпись строгого имени.</span><span class="sxs-lookup"><span data-stu-id="9c079-116">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="9c079-117">Поддерживается следующее значение:</span><span class="sxs-lookup"><span data-stu-id="9c079-117">The following value is supported:</span></span>  
  
- <span data-ttu-id="9c079-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — это значение `false` указывает, что проверка прошла удачно из-за параметров реестра.</span><span class="sxs-lookup"><span data-stu-id="9c079-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c079-119">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9c079-119">Return Value</span></span>  

 <span data-ttu-id="9c079-120">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="9c079-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c079-121">Требования</span><span class="sxs-lookup"><span data-stu-id="9c079-121">Requirements</span></span>  

 <span data-ttu-id="9c079-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c079-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c079-123">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="9c079-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9c079-124">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c079-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c079-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c079-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c079-126">См. также</span><span class="sxs-lookup"><span data-stu-id="9c079-126">See also</span></span>

- [<span data-ttu-id="9c079-127">Метод StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="9c079-127">StrongNameSignatureVerificationEx Method</span></span>](iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="9c079-128">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9c079-128">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
