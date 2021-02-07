---
description: 'Дополнительные сведения о методе: IMetaDataTables:: GetUserString'
title: Метод IMetaDataTables::GetUserString
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
ms.openlocfilehash: 0909bfb2dbf4e6a34b746da7397a82845c2129c2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687692"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="ac007-103">Метод IMetaDataTables::GetUserString</span><span class="sxs-lookup"><span data-stu-id="ac007-103">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="ac007-104">Получает жестко заданную строку по указанному индексу в строковом столбце текущей области.</span><span class="sxs-lookup"><span data-stu-id="ac007-104">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="ac007-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ac007-105">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="ac007-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ac007-106">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="ac007-107">окне Значение индекса, из которого будет извлечена жестко заданная строка.</span><span class="sxs-lookup"><span data-stu-id="ac007-107">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="ac007-108">заполняет Указатель на размер `ppData` .</span><span class="sxs-lookup"><span data-stu-id="ac007-108">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="ac007-109">заполняет Указатель на указатель на возвращаемую строку.</span><span class="sxs-lookup"><span data-stu-id="ac007-109">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="ac007-110">Требования</span><span class="sxs-lookup"><span data-stu-id="ac007-110">Requirements</span></span>

<span data-ttu-id="ac007-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac007-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ac007-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="ac007-112">**Header:** Cor.h</span></span>

<span data-ttu-id="ac007-113">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac007-113">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="ac007-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac007-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ac007-115">См. также</span><span class="sxs-lookup"><span data-stu-id="ac007-115">See also</span></span>

- [<span data-ttu-id="ac007-116">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="ac007-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="ac007-117">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="ac007-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
