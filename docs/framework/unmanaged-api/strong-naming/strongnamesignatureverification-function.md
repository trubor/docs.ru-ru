---
description: Дополнительные сведения о функции StrongNameSignatureVerification
title: Функция StrongNameSignatureVerification
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
ms.openlocfilehash: 74130cda96f38218d2fd296ff8804f86a9a18cd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636269"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="01217-103">Функция StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="01217-103">StrongNameSignatureVerification Function</span></span>

<span data-ttu-id="01217-104">Получает значение, указывающее, содержит ли находящийся по указанному пути манифест сборки подпись строгого имени, которая проверяется в соответствии с заданными флагами.</span><span class="sxs-lookup"><span data-stu-id="01217-104">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="01217-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="01217-105">This function has been deprecated.</span></span> <span data-ttu-id="01217-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="01217-106">Use the [ICLRStrongName::StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01217-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="01217-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01217-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="01217-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="01217-109">окне Путь к переносимому исполняемому файлу (DLL или exe), для которого проверяется сборка.</span><span class="sxs-lookup"><span data-stu-id="01217-109">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="01217-110">окне Флаги для изменения поведения проверки.</span><span class="sxs-lookup"><span data-stu-id="01217-110">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="01217-111">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="01217-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="01217-112">`SN_INFLAG_FORCE_VER` (0x00000001) — принудительная проверка, даже если необходимо переопределить параметры реестра.</span><span class="sxs-lookup"><span data-stu-id="01217-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="01217-113">`SN_INFLAG_INSTALL` (0x00000002) — указывает, что это первый раз при проверке манифеста.</span><span class="sxs-lookup"><span data-stu-id="01217-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="01217-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) — указывает, что кэш будет разрешать доступ только тем пользователям, у которых есть права администратора.</span><span class="sxs-lookup"><span data-stu-id="01217-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="01217-115">`SN_INFLAG_USER_ACCESS` (0x00000008) — указывает, что сборка будет доступна только текущему пользователю.</span><span class="sxs-lookup"><span data-stu-id="01217-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="01217-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) — указывает, что кэш не предоставляет никаких гарантий ограничения доступа.</span><span class="sxs-lookup"><span data-stu-id="01217-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="01217-117">`SN_INFLAG_RUNTIME` (0x80000000) — зарезервировано для внутренней отладки.</span><span class="sxs-lookup"><span data-stu-id="01217-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="01217-118">заполняет Флаги, указывающие, была ли проверена подпись строгого имени.</span><span class="sxs-lookup"><span data-stu-id="01217-118">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="01217-119">Поддерживается следующее значение:</span><span class="sxs-lookup"><span data-stu-id="01217-119">The following value is supported:</span></span>  
  
- <span data-ttu-id="01217-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — это значение `false` указывает, что проверка прошла удачно из-за параметров реестра.</span><span class="sxs-lookup"><span data-stu-id="01217-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01217-121">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="01217-121">Return Value</span></span>  

 <span data-ttu-id="01217-122">`true` значение, если проверка прошла успешно; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="01217-122">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01217-123">Требования</span><span class="sxs-lookup"><span data-stu-id="01217-123">Requirements</span></span>  

 <span data-ttu-id="01217-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01217-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01217-125">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="01217-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="01217-126">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="01217-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="01217-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01217-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01217-128">См. также</span><span class="sxs-lookup"><span data-stu-id="01217-128">See also</span></span>

- [<span data-ttu-id="01217-129">Метод StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="01217-129">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="01217-130">Метод StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="01217-130">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="01217-131">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="01217-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
