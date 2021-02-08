---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинеусерстринг'
title: Метод IMetaDataEmit::DefineUserString
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
ms.openlocfilehash: 0d1c376e3f121d35cb9f6c08d7013a3913a8bd49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784006"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="aadca-103">Метод IMetaDataEmit::DefineUserString</span><span class="sxs-lookup"><span data-stu-id="aadca-103">IMetaDataEmit::DefineUserString Method</span></span>

<span data-ttu-id="aadca-104">Возвращает токен метаданных для указанной литеральной строки.</span><span class="sxs-lookup"><span data-stu-id="aadca-104">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aadca-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aadca-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aadca-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="aadca-106">Parameters</span></span>  

 `szString`  
 <span data-ttu-id="aadca-107">окне Пользовательская строка для хранения.</span><span class="sxs-lookup"><span data-stu-id="aadca-107">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="aadca-108">окне Число расширенных символов в `szString` .</span><span class="sxs-lookup"><span data-stu-id="aadca-108">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="aadca-109">заполняет Назначенный токен строки.</span><span class="sxs-lookup"><span data-stu-id="aadca-109">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aadca-110">Требования</span><span class="sxs-lookup"><span data-stu-id="aadca-110">Requirements</span></span>  

 <span data-ttu-id="aadca-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aadca-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aadca-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="aadca-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aadca-113">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aadca-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aadca-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aadca-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aadca-115">См. также</span><span class="sxs-lookup"><span data-stu-id="aadca-115">See also</span></span>

- [<span data-ttu-id="aadca-116">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="aadca-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="aadca-117">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="aadca-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
