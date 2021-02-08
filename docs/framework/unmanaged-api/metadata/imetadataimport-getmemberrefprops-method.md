---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetMemberRefProps'
title: Метод IMetaDataImport::GetMemberRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
ms.openlocfilehash: b441f39d95c9af1e18d34a1a4d86d6cea33508c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783886"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="19c09-103">Метод IMetaDataImport::GetMemberRefProps</span><span class="sxs-lookup"><span data-stu-id="19c09-103">IMetaDataImport::GetMemberRefProps Method</span></span>

<span data-ttu-id="19c09-104">Возвращает метаданные, связанные с членом, на который ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="19c09-104">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19c09-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="19c09-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,
   [out] mdToken           *ptk,
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19c09-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="19c09-106">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="19c09-107">окне Токен MemberRef, для которого возвращаются связанные метаданные.</span><span class="sxs-lookup"><span data-stu-id="19c09-107">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="19c09-108">заполняет TypeDef или TypeRef, или TypeSpec-токен, представляющий класс, объявляющий член, или токен ModuleRef, представляющий класс Module, объявляющий элемент, или MethodDef, представляющий элемент.</span><span class="sxs-lookup"><span data-stu-id="19c09-108">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="19c09-109">заполняет Строковый буфер для имени члена.</span><span class="sxs-lookup"><span data-stu-id="19c09-109">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="19c09-110">окне Запрошенный размер в расширенных символах `szMember` .</span><span class="sxs-lookup"><span data-stu-id="19c09-110">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="19c09-111">заполняет Возвращаемый размер в расширенных символах `szMember` .</span><span class="sxs-lookup"><span data-stu-id="19c09-111">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="19c09-112">заполняет Указатель на сигнатуру двоичных метаданных для элемента.</span><span class="sxs-lookup"><span data-stu-id="19c09-112">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="19c09-113">заполняет Размер в байтах для `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="19c09-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19c09-114">Требования</span><span class="sxs-lookup"><span data-stu-id="19c09-114">Requirements</span></span>  

 <span data-ttu-id="19c09-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19c09-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19c09-116">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="19c09-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19c09-117">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19c09-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="19c09-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19c09-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19c09-119">См. также</span><span class="sxs-lookup"><span data-stu-id="19c09-119">See also</span></span>

- [<span data-ttu-id="19c09-120">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="19c09-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="19c09-121">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="19c09-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
