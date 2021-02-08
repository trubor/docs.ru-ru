---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: SetPermissionSetProps'
title: Метод IMetaDataEmit::SetPermissionSetProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: 1e2786a21a1024f32328e36878a1a2427af54f51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771890"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="3312e-103">Метод IMetaDataEmit::SetPermissionSetProps</span><span class="sxs-lookup"><span data-stu-id="3312e-103">IMetaDataEmit::SetPermissionSetProps Method</span></span>

<span data-ttu-id="3312e-104">Задает или обновляет функции сигнатуры метаданных набора разрешений, определенного при предыдущем вызове метода [IMetaDataEmit::D ефинепермиссионсет](imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="3312e-104">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3312e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3312e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3312e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3312e-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="3312e-107">окне Токен метаданных, представляющий объект для декорирования.</span><span class="sxs-lookup"><span data-stu-id="3312e-107">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="3312e-108">окне Значение [кордеклсекурити](cordeclsecurity-enumeration.md) , указывающее тип используемой декларативной безопасности.</span><span class="sxs-lookup"><span data-stu-id="3312e-108">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="3312e-109">окне Большой двоичный объект разрешений.</span><span class="sxs-lookup"><span data-stu-id="3312e-109">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="3312e-110">окне Размер (в байтах) `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="3312e-110">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="3312e-111">заполняет `mdPermission` Токен метаданных, представляющий обновленные разрешения.</span><span class="sxs-lookup"><span data-stu-id="3312e-111">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3312e-112">Требования</span><span class="sxs-lookup"><span data-stu-id="3312e-112">Requirements</span></span>  

 <span data-ttu-id="3312e-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3312e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3312e-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="3312e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3312e-115">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3312e-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3312e-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3312e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3312e-117">См. также</span><span class="sxs-lookup"><span data-stu-id="3312e-117">See also</span></span>

- [<span data-ttu-id="3312e-118">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="3312e-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3312e-119">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="3312e-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
