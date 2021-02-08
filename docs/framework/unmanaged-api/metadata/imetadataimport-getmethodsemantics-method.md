---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetMethodSemantics'
title: Метод IMetaDataImport::GetMethodSemantics
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
ms.openlocfilehash: 2b17e2ffaeef3a451850ce2cc9c4861d68df3a81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783863"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="32604-103">Метод IMetaDataImport::GetMethodSemantics</span><span class="sxs-lookup"><span data-stu-id="32604-103">IMetaDataImport::GetMethodSemantics Method</span></span>

<span data-ttu-id="32604-104">Получает флаги, указывающие связь между методом, на который ссылается указанный токен MethodDef, и связанным свойством и событием, на которые ссылается указанный токен Евентпроп.</span><span class="sxs-lookup"><span data-stu-id="32604-104">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32604-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="32604-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32604-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="32604-106">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="32604-107">окне Токен MethodDef, представляющий метод, для которого необходимо получить сведения о семантической роли.</span><span class="sxs-lookup"><span data-stu-id="32604-107">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="32604-108">окне Токен, представляющий парное свойство и событие, для которого необходимо получить роль метода.</span><span class="sxs-lookup"><span data-stu-id="32604-108">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="32604-109">заполняет Указатель на соответствующие флаги семантики.</span><span class="sxs-lookup"><span data-stu-id="32604-109">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="32604-110">Это значение является битовой маской из перечисления [кормесодсемантиксаттр](cormethodsemanticsattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="32604-110">This value is a bitmask from the [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32604-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="32604-111">Remarks</span></span>  

 <span data-ttu-id="32604-112">Метод [IMetaDataEmit::D ефинепроперти](imetadataemit-defineproperty-method.md) задает флаги семантики метода.</span><span class="sxs-lookup"><span data-stu-id="32604-112">The [IMetaDataEmit::DefineProperty](imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32604-113">Требования</span><span class="sxs-lookup"><span data-stu-id="32604-113">Requirements</span></span>  

 <span data-ttu-id="32604-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32604-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32604-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="32604-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32604-116">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32604-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32604-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32604-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32604-118">См. также</span><span class="sxs-lookup"><span data-stu-id="32604-118">See also</span></span>

- [<span data-ttu-id="32604-119">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="32604-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="32604-120">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="32604-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
