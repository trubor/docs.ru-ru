---
description: 'Дополнительные сведения: метод IMetaDataImport:: Финдтипереф'
title: Метод IMetaDataImport::FindTypeRef
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
ms.openlocfilehash: 11e966256b5e75c1acff0bf1e6de0c96dc03e6aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745571"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="6c6d3-103">Метод IMetaDataImport::FindTypeRef</span><span class="sxs-lookup"><span data-stu-id="6c6d3-103">IMetaDataImport::FindTypeRef Method</span></span>

<span data-ttu-id="6c6d3-104">Возвращает указатель на маркер TypeRef для <xref:System.Type> ссылки, наданной в указанной области и имеющей указанное имя.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-104">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c6d3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6c6d3-105">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c6d3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6c6d3-106">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="6c6d3-107">окне Токен ModuleRef, AssemblyRef или TypeRef, указывающий модуль, сборку или тип соответственно, в котором определена ссылка на тип.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-107">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="6c6d3-108">окне Имя искомой ссылки на тип.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-108">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="6c6d3-109">заполняет Указатель на соответствующий токен TypeRef.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-109">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c6d3-110">Требования</span><span class="sxs-lookup"><span data-stu-id="6c6d3-110">Requirements</span></span>  

 <span data-ttu-id="6c6d3-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c6d3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c6d3-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="6c6d3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c6d3-113">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c6d3-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c6d3-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c6d3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c6d3-115">См. также</span><span class="sxs-lookup"><span data-stu-id="6c6d3-115">See also</span></span>

- [<span data-ttu-id="6c6d3-116">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="6c6d3-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6c6d3-117">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="6c6d3-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
