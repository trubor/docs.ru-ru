---
description: Дополнительные сведения о функции StrongNameKeyDelete
title: Функция StrongNameKeyDelete
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
ms.openlocfilehash: 9314d961f79e673925125c2362308f9ab4533e75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781211"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="720f8-103">Функция StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="720f8-103">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="720f8-104">Удаляет указанный контейнер ключей.</span><span class="sxs-lookup"><span data-stu-id="720f8-104">Deletes the specified key container.</span></span>

<span data-ttu-id="720f8-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="720f8-105">This function has been deprecated.</span></span> <span data-ttu-id="720f8-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="720f8-106">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="720f8-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="720f8-107">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="720f8-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="720f8-108">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="720f8-109">окне Имя удаляемого контейнера ключей.</span><span class="sxs-lookup"><span data-stu-id="720f8-109">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="720f8-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="720f8-110">Return Value</span></span>

<span data-ttu-id="720f8-111">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="720f8-111">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="720f8-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="720f8-112">Remarks</span></span>

<span data-ttu-id="720f8-113">Используйте функцию [StrongNameKeyInstall](strongnamekeyinstall-function.md) для импорта пары открытого и закрытого ключей в контейнер.</span><span class="sxs-lookup"><span data-stu-id="720f8-113">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="720f8-114">Если `StrongNameKeyDelete` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="720f8-114">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="720f8-115">Требования</span><span class="sxs-lookup"><span data-stu-id="720f8-115">Requirements</span></span>

<span data-ttu-id="720f8-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="720f8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="720f8-117">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="720f8-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="720f8-118">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="720f8-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="720f8-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="720f8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="720f8-120">См. также</span><span class="sxs-lookup"><span data-stu-id="720f8-120">See also</span></span>

- [<span data-ttu-id="720f8-121">Метод StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="720f8-121">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="720f8-122">Метод StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="720f8-122">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="720f8-123">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="720f8-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
