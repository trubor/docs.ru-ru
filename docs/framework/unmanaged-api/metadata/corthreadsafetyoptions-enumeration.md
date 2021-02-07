---
description: Дополнительные сведения о перечислении CorThreadSafetyOptions
title: Перечисление CorThreadSafetyOptions
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 7915bcf5e7b71fa84ea83642467c1600cd38712d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707323"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="8eaec-103">Перечисление CorThreadSafetyOptions</span><span class="sxs-lookup"><span data-stu-id="8eaec-103">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="8eaec-104">Задает флаги для выбора параметров безопасности потока.</span><span class="sxs-lookup"><span data-stu-id="8eaec-104">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="8eaec-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8eaec-105">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="8eaec-106">Члены</span><span class="sxs-lookup"><span data-stu-id="8eaec-106">Members</span></span>

|<span data-ttu-id="8eaec-107">Член</span><span class="sxs-lookup"><span data-stu-id="8eaec-107">Member</span></span>|<span data-ttu-id="8eaec-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8eaec-108">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="8eaec-109">Значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8eaec-109">Default value.</span></span> <span data-ttu-id="8eaec-110">Эквивалентно `MDThreadSafetyOff`.</span><span class="sxs-lookup"><span data-stu-id="8eaec-110">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="8eaec-111">Указывает, что невозможно установить блокировку потоков чтения/записи.</span><span class="sxs-lookup"><span data-stu-id="8eaec-111">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="8eaec-112">Указывает, что можно задать блокировку потоков чтения/записи.</span><span class="sxs-lookup"><span data-stu-id="8eaec-112">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="8eaec-113">Требования</span><span class="sxs-lookup"><span data-stu-id="8eaec-113">Requirements</span></span>

<span data-ttu-id="8eaec-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eaec-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="8eaec-115">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="8eaec-115">**Header:** CorHdr.h</span></span>

<span data-ttu-id="8eaec-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eaec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8eaec-117">См. также</span><span class="sxs-lookup"><span data-stu-id="8eaec-117">See also</span></span>

- [<span data-ttu-id="8eaec-118">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="8eaec-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
