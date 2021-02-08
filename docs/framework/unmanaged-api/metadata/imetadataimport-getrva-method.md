---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetRVA'
title: Метод IMetaDataImport::GetRVA
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 8d6439bcad50a6311e7bb1408f4c86144a5026ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789168"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="3fbed-103">Метод IMetaDataImport::GetRVA</span><span class="sxs-lookup"><span data-stu-id="3fbed-103">IMetaDataImport::GetRVA Method</span></span>

<span data-ttu-id="3fbed-104">Возвращает относительный виртуальный адрес (RVA) и флаги реализации метода или поля, представленного указанным токеном.</span><span class="sxs-lookup"><span data-stu-id="3fbed-104">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fbed-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3fbed-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fbed-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3fbed-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="3fbed-107">окне Токен метаданных MethodDef или FieldDef, представляющий объект кода, для которого возвращается RVA.</span><span class="sxs-lookup"><span data-stu-id="3fbed-107">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="3fbed-108">Если токен является FieldDef, поле должно быть глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="3fbed-108">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="3fbed-109">заполняет Указатель на относительный виртуальный адрес объекта кода, представленного токеном.</span><span class="sxs-lookup"><span data-stu-id="3fbed-109">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="3fbed-110">заполняет Указатель на флаги реализации для метода.</span><span class="sxs-lookup"><span data-stu-id="3fbed-110">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="3fbed-111">Это значение является битовой маской из перечисления [кормесодимпл](cormethodimpl-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="3fbed-111">This value is a bitmask from the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="3fbed-112">Значение `pdwImplFlags` допустимо только в том случае `tk` , если является токеном MethodDef.</span><span class="sxs-lookup"><span data-stu-id="3fbed-112">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fbed-113">Требования</span><span class="sxs-lookup"><span data-stu-id="3fbed-113">Requirements</span></span>  

 <span data-ttu-id="3fbed-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fbed-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fbed-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="3fbed-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fbed-116">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3fbed-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fbed-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fbed-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fbed-118">См. также</span><span class="sxs-lookup"><span data-stu-id="3fbed-118">See also</span></span>

- [<span data-ttu-id="3fbed-119">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="3fbed-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3fbed-120">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="3fbed-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
