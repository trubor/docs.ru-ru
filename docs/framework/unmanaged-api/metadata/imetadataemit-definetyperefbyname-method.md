---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинетиперефбинаме'
title: Метод IMetaDataEmit::DefineTypeRefByName
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
ms.openlocfilehash: 836516e06105bb8ebc7c9bacf7b7d3837bf89eec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784019"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="e3aa4-103">Метод IMetaDataEmit::DefineTypeRefByName</span><span class="sxs-lookup"><span data-stu-id="e3aa4-103">IMetaDataEmit::DefineTypeRefByName Method</span></span>

<span data-ttu-id="e3aa4-104">Возвращает токен метаданных для типа, определенного в заданной области, которая находится за пределами текущей области.</span><span class="sxs-lookup"><span data-stu-id="e3aa4-104">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3aa4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e3aa4-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3aa4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e3aa4-106">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="e3aa4-107">окне Токен, указывающий область разрешения.</span><span class="sxs-lookup"><span data-stu-id="e3aa4-107">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="e3aa4-108">Допустимы следующие типы токенов:</span><span class="sxs-lookup"><span data-stu-id="e3aa4-108">The following token types are valid:</span></span>  
  
- <span data-ttu-id="e3aa4-109">`mdModuleRef`значение, если тип определен в той же сборке, в которой определен вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="e3aa4-109">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="e3aa4-110">`mdAssemblyRef`значение, если тип определен в сборке, отличной от той, в которой определен вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="e3aa4-110">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="e3aa4-111">`mdTypeRef`, если тип является вложенным типом.</span><span class="sxs-lookup"><span data-stu-id="e3aa4-111">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="e3aa4-112">`mdModule`, если тип определен в том же модуле, в котором определен вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="e3aa4-112">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="e3aa4-113">Значение null, если тип определен глобально.</span><span class="sxs-lookup"><span data-stu-id="e3aa4-113">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="e3aa4-114">окне Имя типа целевого объекта в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="e3aa4-114">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="e3aa4-115">заполняет Указатель на `mdTypeRef` токен, назначенный типу.</span><span class="sxs-lookup"><span data-stu-id="e3aa4-115">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3aa4-116">Требования</span><span class="sxs-lookup"><span data-stu-id="e3aa4-116">Requirements</span></span>  

 <span data-ttu-id="e3aa4-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3aa4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3aa4-118">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="e3aa4-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3aa4-119">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3aa4-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3aa4-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3aa4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3aa4-121">См. также</span><span class="sxs-lookup"><span data-stu-id="e3aa4-121">See also</span></span>

- [<span data-ttu-id="e3aa4-122">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="e3aa4-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e3aa4-123">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="e3aa4-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
