---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyEmit:: Сетманифестресаурцепропс'
title: Метод IMetaDataAssemblyEmit::SetManifestResourceProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
ms.openlocfilehash: 0d5022c4acc562f9e77cec4ba080815db410862b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721034"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="991ba-103">Метод IMetaDataAssemblyEmit::SetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="991ba-103">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>

<span data-ttu-id="991ba-104">Изменяет указанную структуру метаданных `ManifestResource`.</span><span class="sxs-lookup"><span data-stu-id="991ba-104">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="991ba-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="991ba-105">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="991ba-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="991ba-106">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="991ba-107">окне Токен, указывающий `ManifestResource` структуру метаданных для изменения.</span><span class="sxs-lookup"><span data-stu-id="991ba-107">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="991ba-108">окне Токен типа `File` или `AssemblyRef` , который сопоставляется с поставщиком ресурсов.</span><span class="sxs-lookup"><span data-stu-id="991ba-108">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="991ba-109">окне Смещение в начале ресурса в файле.</span><span class="sxs-lookup"><span data-stu-id="991ba-109">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="991ba-110">окне Побитовое сочетание значений флагов, задающих атрибуты ресурса.</span><span class="sxs-lookup"><span data-stu-id="991ba-110">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="991ba-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="991ba-111">Remarks</span></span>  

 <span data-ttu-id="991ba-112">Чтобы создать `ManifestResource` структуру метаданных, используйте метод [IMetaDataAssemblyEmit::D ефинеманифестресаурце](imetadataassemblyemit-definemanifestresource-method.md) .</span><span class="sxs-lookup"><span data-stu-id="991ba-112">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="991ba-113">Требования</span><span class="sxs-lookup"><span data-stu-id="991ba-113">Requirements</span></span>  

 <span data-ttu-id="991ba-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="991ba-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="991ba-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="991ba-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="991ba-116">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="991ba-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="991ba-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="991ba-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="991ba-118">См. также</span><span class="sxs-lookup"><span data-stu-id="991ba-118">See also</span></span>

- [<span data-ttu-id="991ba-119">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="991ba-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
