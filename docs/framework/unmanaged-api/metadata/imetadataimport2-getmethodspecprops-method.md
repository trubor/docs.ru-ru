---
description: 'Дополнительные сведения о методе: IMetaDataImport2:: Жетмесодспекпропс'
title: Метод IMetaDataImport2::GetMethodSpecProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
ms.openlocfilehash: 77f3f78905d1f7f44af0e9c7a75746b4e5b6e684
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688654"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="c57c0-103">Метод IMetaDataImport2::GetMethodSpecProps</span><span class="sxs-lookup"><span data-stu-id="c57c0-103">IMetaDataImport2::GetMethodSpecProps Method</span></span>

<span data-ttu-id="c57c0-104">Возвращает сигнатуру метаданных метода, на который ссылается указанный токен MethodSpec.</span><span class="sxs-lookup"><span data-stu-id="c57c0-104">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c57c0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c57c0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="c57c0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c57c0-106">Parameters</span></span>  

 `mi`  
 <span data-ttu-id="c57c0-107">окне Токен MethodSpec, представляющий создание экземпляра метода.</span><span class="sxs-lookup"><span data-stu-id="c57c0-107">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="c57c0-108">заполняет Указатель на токен MethodDef или Месодреф, представляющий определение метода.</span><span class="sxs-lookup"><span data-stu-id="c57c0-108">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="c57c0-109">заполняет Указатель на сигнатуру двоичных метаданных метода.</span><span class="sxs-lookup"><span data-stu-id="c57c0-109">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="c57c0-110">заполняет Размер (в байтах) `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="c57c0-110">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c57c0-111">Требования</span><span class="sxs-lookup"><span data-stu-id="c57c0-111">Requirements</span></span>  

 <span data-ttu-id="c57c0-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c57c0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c57c0-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c57c0-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c57c0-114">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c57c0-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c57c0-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c57c0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c57c0-116">См. также</span><span class="sxs-lookup"><span data-stu-id="c57c0-116">See also</span></span>

- [<span data-ttu-id="c57c0-117">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c57c0-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="c57c0-118">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c57c0-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
