---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetPermissionSetProps'
title: Метод IMetaDataImport::GetPermissionSetProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
ms.openlocfilehash: 9dc10b7bf531b6eec389334d80cf6a1cece20ee9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789194"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="5742f-103">Метод IMetaDataImport::GetPermissionSetProps</span><span class="sxs-lookup"><span data-stu-id="5742f-103">IMetaDataImport::GetPermissionSetProps Method</span></span>

<span data-ttu-id="5742f-104">Возвращает метаданные, связанные с <xref:System.Security.PermissionSet?displayProperty=nameWithType> объектом, представленным указанным маркером разрешений.</span><span class="sxs-lookup"><span data-stu-id="5742f-104">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5742f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5742f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5742f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5742f-106">Parameters</span></span>  

 `pm`  
 <span data-ttu-id="5742f-107">окне Маркер метаданных разрешения, представляющий набор разрешений, для которого необходимо получить свойства метаданных.</span><span class="sxs-lookup"><span data-stu-id="5742f-107">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="5742f-108">заполняет Указатель на набор разрешений.</span><span class="sxs-lookup"><span data-stu-id="5742f-108">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="5742f-109">заполняет Указатель на сигнатуру двоичных метаданных набора разрешений.</span><span class="sxs-lookup"><span data-stu-id="5742f-109">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="5742f-110">заполняет Размер в байтах для `ppvPermission` .</span><span class="sxs-lookup"><span data-stu-id="5742f-110">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5742f-111">Требования</span><span class="sxs-lookup"><span data-stu-id="5742f-111">Requirements</span></span>  

 <span data-ttu-id="5742f-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5742f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5742f-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="5742f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5742f-114">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5742f-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5742f-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5742f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5742f-116">См. также</span><span class="sxs-lookup"><span data-stu-id="5742f-116">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="5742f-117">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="5742f-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5742f-118">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="5742f-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
