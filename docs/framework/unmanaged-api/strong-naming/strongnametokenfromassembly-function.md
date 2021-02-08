---
description: Дополнительные сведения о функции StrongNameTokenFromAssembly
title: Функция StrongNameTokenFromAssembly
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
ms.openlocfilehash: 3646d441da4885624c15d5e53670a8dd8db45160
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794485"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="f0c39-103">Функция StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="f0c39-103">StrongNameTokenFromAssembly Function</span></span>

<span data-ttu-id="f0c39-104">Создает маркер строгого имени из указанного файла сборки.</span><span class="sxs-lookup"><span data-stu-id="f0c39-104">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="f0c39-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="f0c39-105">This function has been deprecated.</span></span> <span data-ttu-id="f0c39-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f0c39-106">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0c39-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f0c39-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0c39-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="f0c39-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="f0c39-109">окне Путь к переносимому исполняемому файлу (PE) для сборки.</span><span class="sxs-lookup"><span data-stu-id="f0c39-109">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="f0c39-110">заполняет Возвращенный маркер строгого имени.</span><span class="sxs-lookup"><span data-stu-id="f0c39-110">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="f0c39-111">заполняет Размер (в байтах) маркера строгого имени.</span><span class="sxs-lookup"><span data-stu-id="f0c39-111">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0c39-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f0c39-112">Return Value</span></span>  

 <span data-ttu-id="f0c39-113">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="f0c39-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0c39-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="f0c39-114">Remarks</span></span>  

 <span data-ttu-id="f0c39-115">Маркер строгого имени — это сокращенная форма открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="f0c39-115">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="f0c39-116">Маркер представляет собой 64-разрядный хэш, созданный из открытого ключа, используемого для подписания сборки.</span><span class="sxs-lookup"><span data-stu-id="f0c39-116">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="f0c39-117">Токен является частью строгого имени сборки и может быть считан из метаданных сборки.</span><span class="sxs-lookup"><span data-stu-id="f0c39-117">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="f0c39-118">После создания маркера необходимо вызвать функцию [StrongNameFreeBuffer](strongnamefreebuffer-function.md) , чтобы освободить выделенную память.</span><span class="sxs-lookup"><span data-stu-id="f0c39-118">After the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="f0c39-119">Если `StrongNameTokenFromAssembly` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="f0c39-119">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0c39-120">Требования</span><span class="sxs-lookup"><span data-stu-id="f0c39-120">Requirements</span></span>  

 <span data-ttu-id="f0c39-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0c39-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0c39-122">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="f0c39-122">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f0c39-123">**Библиотека:** Включается в качестве ресурса в mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f0c39-123">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="f0c39-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0c39-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c39-125">См. также</span><span class="sxs-lookup"><span data-stu-id="f0c39-125">See also</span></span>

- [<span data-ttu-id="f0c39-126">Метод StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="f0c39-126">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="f0c39-127">Метод StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="f0c39-127">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="f0c39-128">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="f0c39-128">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
