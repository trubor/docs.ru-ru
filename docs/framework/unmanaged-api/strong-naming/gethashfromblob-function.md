---
description: Дополнительные сведения о функции GetHashFromBlob
title: Функция GetHashFromBlob
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
ms.openlocfilehash: dc5039e44440afa7a000bc61167faec0e5b6cc84
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736613"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="1a072-103">Функция GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="1a072-103">GetHashFromBlob Function</span></span>

<span data-ttu-id="1a072-104">Получает хэш сборки по указанному адресу памяти с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="1a072-104">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="1a072-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="1a072-105">This function has been deprecated.</span></span> <span data-ttu-id="1a072-106">Используйте вместо этого метод [метод iclrstrongname:: GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1a072-106">Use the [ICLRStrongName::GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="1a072-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1a072-107">Syntax</span></span>

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a><span data-ttu-id="1a072-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="1a072-108">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="1a072-109">окне Указатель на адрес блока памяти, который необходимо хэшировать.</span><span class="sxs-lookup"><span data-stu-id="1a072-109">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="1a072-110">окне Длина блока памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="1a072-110">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="1a072-111">[вход, выход] Константа, указывающая хэш-алгоритм.</span><span class="sxs-lookup"><span data-stu-id="1a072-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="1a072-112">Используйте нуль для алгоритма по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1a072-112">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="1a072-113">заполняет Возвращаемый буфер хэша.</span><span class="sxs-lookup"><span data-stu-id="1a072-113">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="1a072-114">окне Запрошенный максимальный размер `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="1a072-114">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="1a072-115">заполняет Размер возвращаемого объекта (в байтах) `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="1a072-115">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="1a072-116">Требования</span><span class="sxs-lookup"><span data-stu-id="1a072-116">Requirements</span></span>

<span data-ttu-id="1a072-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a072-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1a072-118">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="1a072-118">**Header:** StrongName.h</span></span>

<span data-ttu-id="1a072-119">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a072-119">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="1a072-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a072-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1a072-121">См. также</span><span class="sxs-lookup"><span data-stu-id="1a072-121">See also</span></span>

- [<span data-ttu-id="1a072-122">Метод GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="1a072-122">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="1a072-123">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="1a072-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
