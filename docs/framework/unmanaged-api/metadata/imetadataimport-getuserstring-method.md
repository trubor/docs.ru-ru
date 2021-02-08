---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetUserString'
title: Метод IMetaDataImport::GetUserString
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
ms.openlocfilehash: 074d196c74be30f5879410ad44b9bb5c096eb153
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789103"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="683c9-103">Метод IMetaDataImport::GetUserString</span><span class="sxs-lookup"><span data-stu-id="683c9-103">IMetaDataImport::GetUserString Method</span></span>

<span data-ttu-id="683c9-104">Получает строку литералов, представленную указанным токеном метаданных.</span><span class="sxs-lookup"><span data-stu-id="683c9-104">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="683c9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="683c9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="683c9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="683c9-106">Parameters</span></span>  

 `stk`  
 <span data-ttu-id="683c9-107">окне Токен строки, для которого возвращается связанная строка.</span><span class="sxs-lookup"><span data-stu-id="683c9-107">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="683c9-108">заполняет Копия запрошенной строки.</span><span class="sxs-lookup"><span data-stu-id="683c9-108">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="683c9-109">окне Максимальный размер запрашиваемого значения в расширенных символах `szString` .</span><span class="sxs-lookup"><span data-stu-id="683c9-109">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="683c9-110">заполняет Размер в расширенных символах возвращаемого объекта `szString` .</span><span class="sxs-lookup"><span data-stu-id="683c9-110">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="683c9-111">Требования</span><span class="sxs-lookup"><span data-stu-id="683c9-111">Requirements</span></span>  

 <span data-ttu-id="683c9-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="683c9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="683c9-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="683c9-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="683c9-114">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="683c9-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="683c9-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="683c9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="683c9-116">См. также</span><span class="sxs-lookup"><span data-stu-id="683c9-116">See also</span></span>

- [<span data-ttu-id="683c9-117">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="683c9-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="683c9-118">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="683c9-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
