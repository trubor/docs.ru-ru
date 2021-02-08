---
description: 'Дополнительные сведения о: интерфейс IIdentityAuthority'
title: Интерфейс IIdentityAuthority
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
ms.openlocfilehash: 3064a3d95ebe9a098a7cac0766f18654c6fab8b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800141"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="d646c-103">Интерфейс IIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="d646c-103">IIdentityAuthority Interface</span></span>

<span data-ttu-id="d646c-104">Управляет ключами удостоверений для объектов кода.</span><span class="sxs-lookup"><span data-stu-id="d646c-104">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="d646c-105">Методы</span><span class="sxs-lookup"><span data-stu-id="d646c-105">Methods</span></span>

|<span data-ttu-id="d646c-106">Метод</span><span class="sxs-lookup"><span data-stu-id="d646c-106">Method</span></span>|<span data-ttu-id="d646c-107">Описание</span><span class="sxs-lookup"><span data-stu-id="d646c-107">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="d646c-108">Возвращает значение, указывающее, равны ли два указанных экземпляра [идефинитионидентити](idefinitionidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d646c-108">Gets a value that indicates whether the two specified [IDefinitionIdentity](idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="d646c-109">Возвращает значение, указывающее, равны ли два указанных экземпляра [иреференцеидентити](ireferenceidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d646c-109">Gets a value that indicates whether the two specified [IReferenceIdentity](ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="d646c-110">Возвращает значение, указывающее, равны ли два указанных представления идентификаторов определения строки.</span><span class="sxs-lookup"><span data-stu-id="d646c-110">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="d646c-111">Возвращает значение, указывающее, равны ли два указанных строковых представления идентификаторов ссылки.</span><span class="sxs-lookup"><span data-stu-id="d646c-111">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="d646c-112">Возвращает указатель на новый `IDefinitionIdentity` экземпляр, представляющий объект кода в текущей области.</span><span class="sxs-lookup"><span data-stu-id="d646c-112">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="d646c-113">Возвращает указатель на новый `IReferenceIdentity` экземпляр, представляющий объект кода в текущей области.</span><span class="sxs-lookup"><span data-stu-id="d646c-113">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="d646c-114">Возвращает форматированную строковую версию указанного `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="d646c-114">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="d646c-115">Заполняет указанный буфер расширенных символов строковой версией указанного `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="d646c-115">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="d646c-116">Возвращает значение, указывающее, ссылаются ли указанные `IDefinitionIdentity` экземпляры и на один и тот `IReferenceIdentity` же объект кода.</span><span class="sxs-lookup"><span data-stu-id="d646c-116">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="d646c-117">Возвращает значение, указывающее, ссылаются ли указанные строки на один и тот же объект кода.</span><span class="sxs-lookup"><span data-stu-id="d646c-117">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="d646c-118">Возвращает указатель на вновь созданный строковый ключ для указанного `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="d646c-118">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="d646c-119">Возвращает указатель на вновь созданный строковый ключ для указанного `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="d646c-119">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="d646c-120">Возвращает значение хэша для указанного `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="d646c-120">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="d646c-121">Возвращает значение хэша для указанного `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="d646c-121">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="d646c-122">Возвращает форматированную строковую версию указанного `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="d646c-122">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="d646c-123">Заполняет указанный буфер расширенных символов строковой версией указанного `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="d646c-123">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="d646c-124">Возвращает указатель интерфейса на экземпляр, `IDefinitionIdentity` созданный из указанной форматируемой строки.</span><span class="sxs-lookup"><span data-stu-id="d646c-124">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="d646c-125">Возвращает указатель интерфейса на экземпляр, `IReferenceIdentity` созданный из указанной форматируемой строки.</span><span class="sxs-lookup"><span data-stu-id="d646c-125">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="d646c-126">Требования</span><span class="sxs-lookup"><span data-stu-id="d646c-126">Requirements</span></span>

<span data-ttu-id="d646c-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d646c-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="d646c-128">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="d646c-128">**Header:** Isolation.h</span></span>

<span data-ttu-id="d646c-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d646c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d646c-130">См. также</span><span class="sxs-lookup"><span data-stu-id="d646c-130">See also</span></span>

- [<span data-ttu-id="d646c-131">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="d646c-131">Fusion Interfaces</span></span>](fusion-interfaces.md)
