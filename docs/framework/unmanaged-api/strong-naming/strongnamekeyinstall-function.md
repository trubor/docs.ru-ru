---
description: Дополнительные сведения о функции StrongNameKeyInstall
title: Функция StrongNameKeyInstall
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
ms.openlocfilehash: 0a5d3971ac0927dda7066405adc01a5c80b7faca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670558"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="13007-103">Функция StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="13007-103">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="13007-104">Импортирует пару открытого и закрытого ключей в контейнер.</span><span class="sxs-lookup"><span data-stu-id="13007-104">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="13007-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="13007-105">This function has been deprecated.</span></span> <span data-ttu-id="13007-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) .</span><span class="sxs-lookup"><span data-stu-id="13007-106">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="13007-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="13007-107">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="13007-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="13007-108">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="13007-109">окне Имя контейнера ключей.</span><span class="sxs-lookup"><span data-stu-id="13007-109">[in] The name of the key container.</span></span> <span data-ttu-id="13007-110">`wszKeyContainer` значение должно быть непустой строкой.</span><span class="sxs-lookup"><span data-stu-id="13007-110">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="13007-111">окне Пара двоичных ключей.</span><span class="sxs-lookup"><span data-stu-id="13007-111">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="13007-112">окне Размер (в байтах) `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="13007-112">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="13007-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="13007-113">Return Value</span></span>

<span data-ttu-id="13007-114">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="13007-114">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="13007-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="13007-115">Remarks</span></span>

<span data-ttu-id="13007-116">Чтобы удалить контейнер ключей, используйте функцию [StrongNameKeyDelete](strongnamekeydelete-function.md) .</span><span class="sxs-lookup"><span data-stu-id="13007-116">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="13007-117">Если `StrongNameKeyInstall` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="13007-117">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="13007-118">Требования</span><span class="sxs-lookup"><span data-stu-id="13007-118">Requirements</span></span>

<span data-ttu-id="13007-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13007-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="13007-120">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="13007-120">**Header:** StrongName.h</span></span>

<span data-ttu-id="13007-121">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13007-121">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="13007-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13007-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="13007-123">См. также</span><span class="sxs-lookup"><span data-stu-id="13007-123">See also</span></span>

- [<span data-ttu-id="13007-124">Метод StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="13007-124">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="13007-125">Метод StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="13007-125">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="13007-126">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="13007-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
