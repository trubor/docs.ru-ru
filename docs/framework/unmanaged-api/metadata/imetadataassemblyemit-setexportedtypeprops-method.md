---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyEmit:: Сетекспортедтипепропс'
title: Метод IMetaDataAssemblyEmit::SetExportedTypeProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: 61032abd7b049af29c583e9aee126184af3c78f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678111"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="385b4-103">Метод IMetaDataAssemblyEmit::SetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="385b4-103">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>

<span data-ttu-id="385b4-104">Изменяет указанную структуру метаданных `ExportedType`.</span><span class="sxs-lookup"><span data-stu-id="385b4-104">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="385b4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="385b4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="385b4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="385b4-106">Parameters</span></span>  

 `ct`  
 <span data-ttu-id="385b4-107">окне Токен метаданных, указывающий `ExportedType` структуру метаданных, которую необходимо изменить.</span><span class="sxs-lookup"><span data-stu-id="385b4-107">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="385b4-108">окне Токен типа `File` , `AssemblyRef` или, `ExportedType` который указывает, как этот тип реализуется.</span><span class="sxs-lookup"><span data-stu-id="385b4-108">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="385b4-109">окне `TypeDef` Токен, на который ссылается файл кода.</span><span class="sxs-lookup"><span data-stu-id="385b4-109">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="385b4-110">окне Побитовое сочетание значений, определяющих атрибуты типа.</span><span class="sxs-lookup"><span data-stu-id="385b4-110">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="385b4-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="385b4-111">Remarks</span></span>  

 <span data-ttu-id="385b4-112">Чтобы создать `ExportedType` структуру метаданных, используйте метод [IMetaDataAssemblyEmit::D ефиникспортедтипе](imetadataassemblyemit-defineexportedtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="385b4-112">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="385b4-113">Требования</span><span class="sxs-lookup"><span data-stu-id="385b4-113">Requirements</span></span>  

 <span data-ttu-id="385b4-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="385b4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="385b4-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="385b4-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="385b4-116">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="385b4-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="385b4-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="385b4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="385b4-118">См. также</span><span class="sxs-lookup"><span data-stu-id="385b4-118">See also</span></span>

- [<span data-ttu-id="385b4-119">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="385b4-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
