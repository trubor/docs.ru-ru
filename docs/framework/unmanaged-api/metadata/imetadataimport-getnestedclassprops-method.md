---
description: 'Дополнительные сведения: метод IMetaDataImport:: Жетнестедкласспропс'
title: Метод IMetaDataImport::GetNestedClassProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
ms.openlocfilehash: 5fd812bf9b7725d520b14284db400bb50e82c25b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677542"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="e4314-103">Метод IMetaDataImport::GetNestedClassProps</span><span class="sxs-lookup"><span data-stu-id="e4314-103">IMetaDataImport::GetNestedClassProps Method</span></span>

<span data-ttu-id="e4314-104">Возвращает маркер TypeDef для родителя <xref:System.Type> указанного вложенного типа.</span><span class="sxs-lookup"><span data-stu-id="e4314-104">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4314-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e4314-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4314-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e4314-106">Parameters</span></span>  

 `tdNestedClass`  
 <span data-ttu-id="e4314-107">окне Токен TypeDef, представляющий объект, <xref:System.Type> для которого возвращается маркер родительского класса.</span><span class="sxs-lookup"><span data-stu-id="e4314-107">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="e4314-108">заполняет Указатель на маркер TypeDef для <xref:System.Type> , `tdNestedClass` вложенный в.</span><span class="sxs-lookup"><span data-stu-id="e4314-108">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4314-109">Требования</span><span class="sxs-lookup"><span data-stu-id="e4314-109">Requirements</span></span>  

 <span data-ttu-id="e4314-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4314-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4314-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="e4314-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4314-112">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4314-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e4314-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4314-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4314-114">См. также</span><span class="sxs-lookup"><span data-stu-id="e4314-114">See also</span></span>

- [<span data-ttu-id="e4314-115">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e4314-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e4314-116">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e4314-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
