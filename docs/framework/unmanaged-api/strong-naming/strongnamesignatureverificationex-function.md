---
description: Дополнительные сведения о функции StrongNameSignatureVerificationEx
title: Функция StrongNameSignatureVerificationEx
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
ms.openlocfilehash: 9e20044e9c3caef8c2276ac5f390269ee978d55b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794537"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="930e7-103">Функция StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="930e7-103">StrongNameSignatureVerificationEx Function</span></span>

<span data-ttu-id="930e7-104">Получает значение, указывающее, содержит ли находящийся по указанному пути манифест сборки подпись строгого имени.</span><span class="sxs-lookup"><span data-stu-id="930e7-104">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="930e7-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="930e7-105">This function has been deprecated.</span></span> <span data-ttu-id="930e7-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="930e7-106">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="930e7-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="930e7-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="930e7-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="930e7-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="930e7-109">окне Путь к переносимому исполняемому файлу (exe или DLL) для проверяемой сборки.</span><span class="sxs-lookup"><span data-stu-id="930e7-109">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="930e7-110">[входные] `true` для выполнения проверки, даже если необходимо переопределить параметры реестра; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="930e7-110">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="930e7-111">[out] `true` значение, если подпись строгого имени проверена; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="930e7-111">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="930e7-112">`pfWasVerified` также имеет значение, `false` Если проверка прошла успешно из-за параметров реестра.</span><span class="sxs-lookup"><span data-stu-id="930e7-112">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="930e7-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="930e7-113">Return Value</span></span>  

 <span data-ttu-id="930e7-114">`true` значение, если проверка прошла успешно; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="930e7-114">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="930e7-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="930e7-115">Remarks</span></span>  

 <span data-ttu-id="930e7-116">`StrongNameSignatureVerificationEx` предоставляет такую возможность, как функция [StrongNameSignatureVerification](strongnamesignatureverification-function.md) .</span><span class="sxs-lookup"><span data-stu-id="930e7-116">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="930e7-117">Однако второй входной параметр и выходной параметр для `StrongNameSignatureVerificationEx` имеют тип, `BOOLEAN` а не `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="930e7-117">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="930e7-118">Требования</span><span class="sxs-lookup"><span data-stu-id="930e7-118">Requirements</span></span>  

 <span data-ttu-id="930e7-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="930e7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="930e7-120">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="930e7-120">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="930e7-121">**Библиотека:** Включается в качестве ресурса в mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="930e7-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="930e7-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="930e7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="930e7-123">См. также</span><span class="sxs-lookup"><span data-stu-id="930e7-123">See also</span></span>

- [<span data-ttu-id="930e7-124">Метод StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="930e7-124">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="930e7-125">Метод StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="930e7-125">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="930e7-126">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="930e7-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
