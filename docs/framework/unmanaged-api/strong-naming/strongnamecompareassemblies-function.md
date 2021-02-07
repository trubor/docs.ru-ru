---
description: Дополнительные сведения о функции StrongNameCompareAssemblies
title: Функция StrongNameCompareAssemblies
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
ms.openlocfilehash: e59bb96a89dc1e1cf8b809c3e0d538aaffe83b8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736551"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="b3a0a-103">Функция StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="b3a0a-103">StrongNameCompareAssemblies Function</span></span>

<span data-ttu-id="b3a0a-104">Определяет, отличаются ли две сборки только подписями строгого имени.</span><span class="sxs-lookup"><span data-stu-id="b3a0a-104">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="b3a0a-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="b3a0a-105">This function has been deprecated.</span></span> <span data-ttu-id="b3a0a-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b3a0a-106">Use the [ICLRStrongName::StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3a0a-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b3a0a-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3a0a-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="b3a0a-108">Parameters</span></span>  

 `wszAssembly1`  
 <span data-ttu-id="b3a0a-109">окне Путь к первой сборке.</span><span class="sxs-lookup"><span data-stu-id="b3a0a-109">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="b3a0a-110">окне Путь к второй сборке.</span><span class="sxs-lookup"><span data-stu-id="b3a0a-110">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="b3a0a-111">заполняет Одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="b3a0a-111">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="b3a0a-112">`SN_CMP_DIFFERENT` (0) — указывает, что сборки содержат различные данные.</span><span class="sxs-lookup"><span data-stu-id="b3a0a-112">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="b3a0a-113">`SN_CMP_IDENTICAL` (1) — указывает, что сборки точно одинаковы, включая их подписи и контрольные суммы.</span><span class="sxs-lookup"><span data-stu-id="b3a0a-113">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="b3a0a-114">`SN_CMP_SIGONLY` (2) — указывает, что сборки отличаются только сигнатурой и контрольной суммой.</span><span class="sxs-lookup"><span data-stu-id="b3a0a-114">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3a0a-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b3a0a-115">Return Value</span></span>  

 <span data-ttu-id="b3a0a-116">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="b3a0a-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3a0a-117">Требования</span><span class="sxs-lookup"><span data-stu-id="b3a0a-117">Requirements</span></span>  

 <span data-ttu-id="b3a0a-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3a0a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3a0a-119">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="b3a0a-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b3a0a-120">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3a0a-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3a0a-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3a0a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3a0a-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="b3a0a-122">Remarks</span></span>  

 <span data-ttu-id="b3a0a-123">Подпись строгого имени сборки состоит из текстового имени, версии, языка и региональных параметров сборки, а также токена открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="b3a0a-123">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="b3a0a-124">Если `StrongNameCompareAssemblies` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="b3a0a-124">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a0a-125">См. также</span><span class="sxs-lookup"><span data-stu-id="b3a0a-125">See also</span></span>

- [<span data-ttu-id="b3a0a-126">Метод StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="b3a0a-126">StrongNameCompareAssemblies Method</span></span>](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="b3a0a-127">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="b3a0a-127">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
