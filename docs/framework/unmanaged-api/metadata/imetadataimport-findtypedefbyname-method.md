---
description: 'Дополнительные сведения: метод IMetaDataImport:: Финдтипедефбинаме'
title: Метод IMetaDataImport::FindTypeDefByName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
ms.openlocfilehash: 083f786cc03b83cda54497937e376baa4a2cbee3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789233"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="1b90e-103">Метод IMetaDataImport::FindTypeDefByName</span><span class="sxs-lookup"><span data-stu-id="1b90e-103">IMetaDataImport::FindTypeDefByName Method</span></span>

<span data-ttu-id="1b90e-104">Возвращает указатель на маркер метаданных TypeDef для <xref:System.Type> с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="1b90e-104">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b90e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1b90e-105">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b90e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1b90e-106">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="1b90e-107">окне Имя типа, для которого требуется получить маркер TypeDef.</span><span class="sxs-lookup"><span data-stu-id="1b90e-107">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="1b90e-108">окне Токен TypeDef или TypeRef, представляющий включающий класс.</span><span class="sxs-lookup"><span data-stu-id="1b90e-108">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="1b90e-109">Если искомый тип не является вложенным классом, присвойте этому параметру значение NULL.</span><span class="sxs-lookup"><span data-stu-id="1b90e-109">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="1b90e-110">заполняет Указатель на соответствующий маркер TypeDef.</span><span class="sxs-lookup"><span data-stu-id="1b90e-110">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b90e-111">Требования</span><span class="sxs-lookup"><span data-stu-id="1b90e-111">Requirements</span></span>  

 <span data-ttu-id="1b90e-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b90e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b90e-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="1b90e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b90e-114">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b90e-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b90e-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b90e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b90e-116">См. также</span><span class="sxs-lookup"><span data-stu-id="1b90e-116">See also</span></span>

- [<span data-ttu-id="1b90e-117">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="1b90e-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1b90e-118">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="1b90e-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
