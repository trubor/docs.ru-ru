---
description: 'Дополнительные сведения: метод IMetaDataImport:: Жеткустоматтрибутебинаме'
title: Метод IMetaDataImport::GetCustomAttributeByName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
ms.openlocfilehash: 1a9ca5f7fe13243c01c5dbcb9f49955e9ce05c26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745493"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="8794c-103">Метод IMetaDataImport::GetCustomAttributeByName</span><span class="sxs-lookup"><span data-stu-id="8794c-103">IMetaDataImport::GetCustomAttributeByName Method</span></span>

<span data-ttu-id="8794c-104">Возвращает настраиваемый атрибут по его имени и владельцу.</span><span class="sxs-lookup"><span data-stu-id="8794c-104">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8794c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8794c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8794c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8794c-106">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="8794c-107">окне Токен метаданных, представляющий объект, которому принадлежит настраиваемый атрибут.</span><span class="sxs-lookup"><span data-stu-id="8794c-107">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="8794c-108">окне Имя настраиваемого атрибута.</span><span class="sxs-lookup"><span data-stu-id="8794c-108">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="8794c-109">заполняет Указатель на массив данных, являющийся значением настраиваемого атрибута.</span><span class="sxs-lookup"><span data-stu-id="8794c-109">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="8794c-110">заполняет Размер в байтах данных, возвращаемых в \* `ppData` .</span><span class="sxs-lookup"><span data-stu-id="8794c-110">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8794c-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="8794c-111">Remarks</span></span>  

 <span data-ttu-id="8794c-112">Допускается определение нескольких пользовательских атрибутов для одного и того же владельца; они даже могут иметь одно и то же имя.</span><span class="sxs-lookup"><span data-stu-id="8794c-112">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="8794c-113">Однако `GetCustomAttributeByName` возвращает только один экземпляр.</span><span class="sxs-lookup"><span data-stu-id="8794c-113">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="8794c-114">( `GetCustomAttributeByName` возвращает первый обнаруженный экземпляр.) Чтобы найти все экземпляры настраиваемого атрибута, вызовите метод [IMetaDataImport:: EnumCustomAttributes](imetadataimport-enumcustomattributes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8794c-114">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8794c-115">Требования</span><span class="sxs-lookup"><span data-stu-id="8794c-115">Requirements</span></span>  

 <span data-ttu-id="8794c-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8794c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8794c-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="8794c-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8794c-118">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8794c-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8794c-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8794c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8794c-120">См. также</span><span class="sxs-lookup"><span data-stu-id="8794c-120">See also</span></span>

- [<span data-ttu-id="8794c-121">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="8794c-121">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8794c-122">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="8794c-122">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
