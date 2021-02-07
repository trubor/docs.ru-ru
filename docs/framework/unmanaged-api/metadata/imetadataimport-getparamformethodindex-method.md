---
description: 'Дополнительные сведения: метод IMetaDataImport:: Жетпарамформесодиндекс'
title: Метод IMetaDataImport::GetParamForMethodIndex
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
ms.openlocfilehash: d84b26f1239e548b6cf96d1e6b38791eb6ecddff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728162"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="233cf-103">Метод IMetaDataImport::GetParamForMethodIndex</span><span class="sxs-lookup"><span data-stu-id="233cf-103">IMetaDataImport::GetParamForMethodIndex Method</span></span>

<span data-ttu-id="233cf-104">Возвращает токен, представляющий указанный параметр метода, представленного указанным токеном MethodDef.</span><span class="sxs-lookup"><span data-stu-id="233cf-104">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="233cf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="233cf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="233cf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="233cf-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="233cf-107">окне Токен, представляющий метод, для которого возвращается токен параметра.</span><span class="sxs-lookup"><span data-stu-id="233cf-107">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="233cf-108">окне Порядковый номер в списке параметров, в котором выполняется запрошенный параметр.</span><span class="sxs-lookup"><span data-stu-id="233cf-108">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="233cf-109">Параметры нумеруются начиная с единицы, а возвращаемое значение метода в нулевом положении.</span><span class="sxs-lookup"><span data-stu-id="233cf-109">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="233cf-110">заполняет Указатель на токен Парамдеф, представляющий запрошенный параметр.</span><span class="sxs-lookup"><span data-stu-id="233cf-110">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="233cf-111">Требования</span><span class="sxs-lookup"><span data-stu-id="233cf-111">Requirements</span></span>  

 <span data-ttu-id="233cf-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="233cf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="233cf-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="233cf-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="233cf-114">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="233cf-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="233cf-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="233cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="233cf-116">См. также</span><span class="sxs-lookup"><span data-stu-id="233cf-116">See also</span></span>

- [<span data-ttu-id="233cf-117">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="233cf-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="233cf-118">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="233cf-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
