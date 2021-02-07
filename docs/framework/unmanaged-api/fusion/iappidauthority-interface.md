---
description: 'Дополнительные сведения о: интерфейс Иаппидаусорити'
title: Интерфейс IAppIdAuthority
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
ms.openlocfilehash: 238885c7f080571b414511c24f9772dbc19b4683
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761009"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="b1f6a-103">Интерфейс IAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="b1f6a-103">IAppIdAuthority Interface</span></span>

<span data-ttu-id="b1f6a-104">Предоставляет методы, создающие и сравнивающие ключи для удостоверений приложений и ссылок.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-104">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1f6a-105">Методы</span><span class="sxs-lookup"><span data-stu-id="b1f6a-105">Methods</span></span>  
  
|<span data-ttu-id="b1f6a-106">Метод</span><span class="sxs-lookup"><span data-stu-id="b1f6a-106">Method</span></span>|<span data-ttu-id="b1f6a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="b1f6a-107">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="b1f6a-108">Возвращает значение, указывающее, равны ли два указанных экземпляра [IDefinitionAppId](idefinitionappid-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b1f6a-108">Gets a value that indicates whether the two specified [IDefinitionAppId](idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="b1f6a-109">Можно передать значение флага IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION, чтобы игнорировать соответствующие сведения о версии.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-109">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="b1f6a-110">Возвращает значение, указывающее, равны ли два указанных экземпляра [иреференцеаппид](ireferenceappid-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b1f6a-110">Gets a value that indicates whether the two specified [IReferenceAppId](ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="b1f6a-111">Можно передать значение флага IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION, чтобы игнорировать соответствующие сведения о версии.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-111">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="b1f6a-112">Возвращает значение, указывающее, равны ли два указанных строковые определения.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-112">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="b1f6a-113">Можно передать значение флага IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION, чтобы игнорировать соответствующие сведения о версии.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-113">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="b1f6a-114">Возвращает значение, указывающее, равны ли две указанные строковые ссылки.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-114">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="b1f6a-115">Можно передать значение флага IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION, чтобы игнорировать соответствующие сведения о версии.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-115">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="b1f6a-116">Возвращает указатель интерфейса на вновь созданный `IDefinitionAppId` экземпляр, представляющий сборку в текущей области.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-116">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="b1f6a-117">Возвращает указатель интерфейса на только что созданный объект `IReferenceAppId` , представляющий сборку в текущей области.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-117">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="b1f6a-118">Возвращает строковую версию указанного объекта `IDefinitionAppId` , используя указанные значения флага.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-118">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="b1f6a-119">Возвращает значение, указывающее, представляет ли заданную `IDefinitionAppId` и одну и ту `IReferenceAppId` же сборку.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-119">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="b1f6a-120">Возвращает значение, указывающее, представляет ли указанная строка определения и ссылочную строку одну и ту же сборку.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-120">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="b1f6a-121">Возвращает строковый ключ, представляющий указанный `IDefinitionAppId` экземпляр.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-121">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="b1f6a-122">Возвращает строковый ключ, представляющий указанный `IReferenceAppId` экземпляр.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-122">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="b1f6a-123">Возвращает хэш-ключ для указанного `IDefinitionAppId` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-123">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="b1f6a-124">Возвращает хэш-ключ для указанного `IReferenceAppId` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-124">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="b1f6a-125">Возвращает строковую версию указанного объекта `IReferenceAppId` , используя указанные значения флага.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-125">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="b1f6a-126">Возвращает указатель интерфейса на `IDefinitionAppId` экземпляр, представляющий сборку, на которую ссылается указанный ключ строки.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-126">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="b1f6a-127">Возвращает указатель интерфейса на `IReferenceAppId` экземпляр, представляющий сборку, на которую ссылается указанный ключ строки.</span><span class="sxs-lookup"><span data-stu-id="b1f6a-127">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1f6a-128">Требования</span><span class="sxs-lookup"><span data-stu-id="b1f6a-128">Requirements</span></span>  

 <span data-ttu-id="b1f6a-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1f6a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1f6a-130">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="b1f6a-130">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b1f6a-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1f6a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1f6a-132">См. также</span><span class="sxs-lookup"><span data-stu-id="b1f6a-132">See also</span></span>

- [<span data-ttu-id="b1f6a-133">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="b1f6a-133">Fusion Interfaces</span></span>](fusion-interfaces.md)
