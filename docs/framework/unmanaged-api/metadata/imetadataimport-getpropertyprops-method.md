---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetPropertyProps'
title: Метод IMetaDataImport::GetPropertyProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 25fae4488117a35d94479ce501154679b6b536ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789181"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="823ad-103">Метод IMetaDataImport::GetPropertyProps</span><span class="sxs-lookup"><span data-stu-id="823ad-103">IMetaDataImport::GetPropertyProps Method</span></span>

<span data-ttu-id="823ad-104">Возвращает метаданные для свойства, представленного указанным токеном.</span><span class="sxs-lookup"><span data-stu-id="823ad-104">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="823ad-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="823ad-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,
   [out] LPCWSTR           szProperty,
   [in]  ULONG             cchProperty,
   [out] ULONG             *pchProperty,
   [out] DWORD             *pdwPropFlags,
   [out] PCCOR_SIGNATURE   *ppvSig,
   [out] ULONG             *pbSig,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,
   [out] mdMethodDef       *pmdGetter,
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,
   [out] ULONG             *pcOtherMethod
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="823ad-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="823ad-106">Parameters</span></span>  

 `prop`  
 <span data-ttu-id="823ad-107">окне Токен, представляющий свойство, для которого необходимо вернуть метаданные.</span><span class="sxs-lookup"><span data-stu-id="823ad-107">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="823ad-108">заполняет Указатель на маркер TypeDef, представляющий тип, реализующий свойство.</span><span class="sxs-lookup"><span data-stu-id="823ad-108">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="823ad-109">заполняет Буфер для хранения имени свойства.</span><span class="sxs-lookup"><span data-stu-id="823ad-109">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="823ad-110">окне Размер в расширенных символах `szProperty` .</span><span class="sxs-lookup"><span data-stu-id="823ad-110">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="823ad-111">заполняет Число расширенных символов, возвращаемых в `szProperty` .</span><span class="sxs-lookup"><span data-stu-id="823ad-111">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="823ad-112">заполняет Указатель на любые флаги атрибутов, применяемые к свойству.</span><span class="sxs-lookup"><span data-stu-id="823ad-112">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="823ad-113">Это значение является битовой маской из перечисления [CorPropertyAttr](corpropertyattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="823ad-113">This value is a bitmask from the [CorPropertyAttr](corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="823ad-114">заполняет Указатель на сигнатуру метаданных свойства.</span><span class="sxs-lookup"><span data-stu-id="823ad-114">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="823ad-115">заполняет Число байтов, возвращенных в `ppvSig` .</span><span class="sxs-lookup"><span data-stu-id="823ad-115">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="823ad-116">заполняет Флаг, указывающий тип константы, которая является значением свойства по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="823ad-116">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="823ad-117">Это значение из перечисления Корелементтипе.</span><span class="sxs-lookup"><span data-stu-id="823ad-117">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="823ad-118">заполняет Указатель на байты, в которых хранится значение по умолчанию для этого свойства.</span><span class="sxs-lookup"><span data-stu-id="823ad-118">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="823ad-119">заполняет Размер в расширенных символах `ppDefaultValue` , если `pdwCPlusTypeFlag` имеет ELEMENT_TYPE_STRING; в противном случае это значение не является значимым.</span><span class="sxs-lookup"><span data-stu-id="823ad-119">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="823ad-120">В этом случае длина `ppDefaultValue` выводится из типа, заданного параметром `pdwCPlusTypeFlag` .</span><span class="sxs-lookup"><span data-stu-id="823ad-120">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="823ad-121">заполняет Указатель на токен MethodDef, представляющий метод доступа set для свойства.</span><span class="sxs-lookup"><span data-stu-id="823ad-121">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="823ad-122">заполняет Указатель на токен MethodDef, представляющий метод доступа get для свойства.</span><span class="sxs-lookup"><span data-stu-id="823ad-122">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="823ad-123">заполняет Массив токенов MethodDef, которые представляют другие методы, связанные со свойством.</span><span class="sxs-lookup"><span data-stu-id="823ad-123">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="823ad-124">[in] Максимальный размер массива `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="823ad-124">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="823ad-125">Если массив не является достаточно большим, чтобы вместить все методы, они пропускаются без предупреждения.</span><span class="sxs-lookup"><span data-stu-id="823ad-125">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="823ad-126">заполняет Число токенов MethodDef, возвращаемых в `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="823ad-126">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="823ad-127">Требования</span><span class="sxs-lookup"><span data-stu-id="823ad-127">Requirements</span></span>  

 <span data-ttu-id="823ad-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="823ad-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="823ad-129">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="823ad-129">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="823ad-130">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="823ad-130">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="823ad-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="823ad-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="823ad-132">См. также</span><span class="sxs-lookup"><span data-stu-id="823ad-132">See also</span></span>

- [<span data-ttu-id="823ad-133">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="823ad-133">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="823ad-134">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="823ad-134">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
