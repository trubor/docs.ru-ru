---
description: Дополнительные сведения о методе StrongNameSignatureVerificationEx2
title: Метод StrongNameSignatureVerificationEx2
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
ms.openlocfilehash: d79491744ce1a930693d2901544ad80bf8049544
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679281"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="a3a53-103">Метод StrongNameSignatureVerificationEx2</span><span class="sxs-lookup"><span data-stu-id="a3a53-103">StrongNameSignatureVerificationEx2 Method</span></span>

<span data-ttu-id="a3a53-104">Проверяет подпись сборки со строгим именем и обеспечивает сопоставление ключа ECMA с реальным ключом.</span><span class="sxs-lookup"><span data-stu-id="a3a53-104">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3a53-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a3a53-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3a53-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a3a53-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="a3a53-107">окне Путь к переносимому исполняемому файлу (exe или DLL) для проверяемой сборки.</span><span class="sxs-lookup"><span data-stu-id="a3a53-107">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="a3a53-108">[входные] `true` для выполнения проверки, даже если необходимо переопределить параметры реестра; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="a3a53-108">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="a3a53-109">окне Указатель на сопоставление открытого ключа ECMA с реальным ключом, используемым для проверки.</span><span class="sxs-lookup"><span data-stu-id="a3a53-109">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="a3a53-110">окне Длина действительного открытого ключа ECMA.</span><span class="sxs-lookup"><span data-stu-id="a3a53-110">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="a3a53-111">[out] `true` значение, если подпись строгого имени проверена; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="a3a53-111">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="a3a53-112">Этот параметр также устанавливается в значение, `false` Если проверка прошла успешно из-за параметров реестра.</span><span class="sxs-lookup"><span data-stu-id="a3a53-112">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3a53-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a3a53-113">Return Value</span></span>  

 <span data-ttu-id="a3a53-114">`S_OK` значение, если проверка прошла успешно; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="a3a53-114">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3a53-115">Требования</span><span class="sxs-lookup"><span data-stu-id="a3a53-115">Requirements</span></span>  

 <span data-ttu-id="a3a53-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3a53-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3a53-117">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="a3a53-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a3a53-118">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3a53-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3a53-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3a53-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a53-120">См. также</span><span class="sxs-lookup"><span data-stu-id="a3a53-120">See also</span></span>

- [<span data-ttu-id="a3a53-121">Метод StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="a3a53-121">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="a3a53-122">Метод StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="a3a53-122">StrongNameSignatureVerificationEx Method</span></span>](iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="a3a53-123">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a3a53-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
