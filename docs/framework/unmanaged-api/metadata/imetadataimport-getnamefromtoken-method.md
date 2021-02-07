---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetNameFromToken'
title: Метод IMetaDataImport::GetNameFromToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
ms.openlocfilehash: 6195020a2b291a47e908b257896bdba64b0a40d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720856"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="d8286-103">Метод IMetaDataImport::GetNameFromToken</span><span class="sxs-lookup"><span data-stu-id="d8286-103">IMetaDataImport::GetNameFromToken Method</span></span>

<span data-ttu-id="d8286-104">Возвращает имя объекта, на который ссылается указанный токен метаданных, в формате UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d8286-104">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="d8286-105">Этот метод устарел.</span><span class="sxs-lookup"><span data-stu-id="d8286-105">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8286-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d8286-106">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8286-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="d8286-107">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="d8286-108">окне Токен, представляющий объект, для которого возвращается имя.</span><span class="sxs-lookup"><span data-stu-id="d8286-108">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="d8286-109">заполняет Указатель на имя объекта UTF-8 в куче.</span><span class="sxs-lookup"><span data-stu-id="d8286-109">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8286-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="d8286-110">Remarks</span></span>  

 <span data-ttu-id="d8286-111">`GetNameFromToken` устарел.</span><span class="sxs-lookup"><span data-stu-id="d8286-111">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="d8286-112">В качестве альтернативы можно вызвать метод, чтобы получить свойства требуемого типа токена, например `GetFieldProps` для поля или `GetMethodProps` для метода.</span><span class="sxs-lookup"><span data-stu-id="d8286-112">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8286-113">Требования</span><span class="sxs-lookup"><span data-stu-id="d8286-113">Requirements</span></span>  

 <span data-ttu-id="d8286-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8286-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8286-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="d8286-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8286-116">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d8286-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8286-117">**Платформа .NET Framework версии:** 1,0</span><span class="sxs-lookup"><span data-stu-id="d8286-117">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8286-118">См. также</span><span class="sxs-lookup"><span data-stu-id="d8286-118">See also</span></span>

- [<span data-ttu-id="d8286-119">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d8286-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d8286-120">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d8286-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
