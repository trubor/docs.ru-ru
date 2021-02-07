---
description: Дополнительные сведения о перечислении Корсериализатионтипе
title: Перечисление CorSerializationType
ms.date: 03/30/2017
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
ms.openlocfilehash: 86df23bf03037d329a3138798725058f1d24a450
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707388"
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="92651-103">Перечисление CorSerializationType</span><span class="sxs-lookup"><span data-stu-id="92651-103">CorSerializationType Enumeration</span></span>

<span data-ttu-id="92651-104">Указывает способ сериализации объекта средой CLR.</span><span class="sxs-lookup"><span data-stu-id="92651-104">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92651-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="92651-105">Syntax</span></span>  
  
```cpp  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a><span data-ttu-id="92651-106">Члены</span><span class="sxs-lookup"><span data-stu-id="92651-106">Members</span></span>  
  
|<span data-ttu-id="92651-107">Член</span><span class="sxs-lookup"><span data-stu-id="92651-107">Member</span></span>|<span data-ttu-id="92651-108">Описание</span><span class="sxs-lookup"><span data-stu-id="92651-108">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="92651-109">Сериализация объекта не определена.</span><span class="sxs-lookup"><span data-stu-id="92651-109">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="92651-110">Объект сериализуется как логический тип</span><span class="sxs-lookup"><span data-stu-id="92651-110">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="92651-111">Объект сериализуется как символьный тип.</span><span class="sxs-lookup"><span data-stu-id="92651-111">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="92651-112">Объект сериализуется как целое число со знаком длиной 1 байт.</span><span class="sxs-lookup"><span data-stu-id="92651-112">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="92651-113">Объект сериализуется как 1-байтовое целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="92651-113">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="92651-114">Объект сериализуется как 2-байтовое целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="92651-114">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="92651-115">Объект сериализуется как целое число без знака (2 байта).</span><span class="sxs-lookup"><span data-stu-id="92651-115">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="92651-116">Объект сериализуется как 4-байтовое целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="92651-116">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="92651-117">Объект сериализуется как 4-байтовое целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="92651-117">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="92651-118">Объект сериализуется как 8-байтовое целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="92651-118">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="92651-119">Объект сериализуется как 8-байтное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="92651-119">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="92651-120">Объект сериализуется как 4-байтовое значение с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="92651-120">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="92651-121">Объект сериализуется как 8-байтовое число с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="92651-121">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="92651-122">Объект сериализуется как тип System. String.</span><span class="sxs-lookup"><span data-stu-id="92651-122">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="92651-123">Объект сериализуется как одномерный массив с нулевой нижней границей.</span><span class="sxs-lookup"><span data-stu-id="92651-123">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="92651-124">Объект сериализуется как универсальный тип.</span><span class="sxs-lookup"><span data-stu-id="92651-124">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="92651-125">Объект сериализуется как объект с тегами.</span><span class="sxs-lookup"><span data-stu-id="92651-125">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="92651-126">Объект сериализуется как поле.</span><span class="sxs-lookup"><span data-stu-id="92651-126">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="92651-127">Объект сериализуется как свойство.</span><span class="sxs-lookup"><span data-stu-id="92651-127">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="92651-128">Объект сериализуется как перечисление.</span><span class="sxs-lookup"><span data-stu-id="92651-128">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92651-129">Требования</span><span class="sxs-lookup"><span data-stu-id="92651-129">Requirements</span></span>  

 <span data-ttu-id="92651-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92651-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92651-131">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="92651-131">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="92651-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92651-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92651-133">См. также</span><span class="sxs-lookup"><span data-stu-id="92651-133">See also</span></span>

- [<span data-ttu-id="92651-134">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="92651-134">Metadata Enumerations</span></span>](metadata-enumerations.md)
