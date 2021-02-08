---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинепермиссионсет'
title: Метод IMetaDataEmit::DefinePermissionSet
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
ms.openlocfilehash: f5c3f1466217713cb3970c805079d8f65fd429c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784084"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="16ad5-103">Метод IMetaDataEmit::DefinePermissionSet</span><span class="sxs-lookup"><span data-stu-id="16ad5-103">IMetaDataEmit::DefinePermissionSet Method</span></span>

<span data-ttu-id="16ad5-104">Создает определение для набора разрешений с указанной сигнатурой метаданных и получает маркер для этого определения набора разрешений.</span><span class="sxs-lookup"><span data-stu-id="16ad5-104">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16ad5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="16ad5-105">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16ad5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="16ad5-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="16ad5-107">окне Объект для декорирования.</span><span class="sxs-lookup"><span data-stu-id="16ad5-107">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="16ad5-108">окне Значение [кордеклсекурити](cordeclsecurity-enumeration.md) , указывающее тип используемой декларативной безопасности.</span><span class="sxs-lookup"><span data-stu-id="16ad5-108">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="16ad5-109">окне Большой двоичный объект разрешений.</span><span class="sxs-lookup"><span data-stu-id="16ad5-109">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="16ad5-110">окне Размер (в байтах) `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="16ad5-110">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="16ad5-111">заполняет Возвращаемый маркер разрешения.</span><span class="sxs-lookup"><span data-stu-id="16ad5-111">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16ad5-112">Требования</span><span class="sxs-lookup"><span data-stu-id="16ad5-112">Requirements</span></span>  

 <span data-ttu-id="16ad5-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16ad5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16ad5-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="16ad5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16ad5-115">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16ad5-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16ad5-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16ad5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16ad5-117">См. также</span><span class="sxs-lookup"><span data-stu-id="16ad5-117">See also</span></span>

- [<span data-ttu-id="16ad5-118">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="16ad5-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="16ad5-119">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="16ad5-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
