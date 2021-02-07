---
description: 'Дополнительные сведения о методе: IMetaDataTables:: Жеткодедтокенинфо'
title: Метод IMetaDataTables::GetCodedTokenInfo
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
ms.openlocfilehash: 982a13636d8b4572113038eaa658158e6c2ca966
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688290"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="c628c-103">Метод IMetaDataTables::GetCodedTokenInfo</span><span class="sxs-lookup"><span data-stu-id="c628c-103">IMetaDataTables::GetCodedTokenInfo Method</span></span>

<span data-ttu-id="c628c-104">Возвращает указатель на массив токенов, связанных с указанным индексом строки.</span><span class="sxs-lookup"><span data-stu-id="c628c-104">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c628c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c628c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c628c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c628c-106">Parameters</span></span>  

 `ixCdTkn`  
 <span data-ttu-id="c628c-107">окне Тип возвращаемого закодированного токена.</span><span class="sxs-lookup"><span data-stu-id="c628c-107">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c628c-108">заполняет Указатель на длину `ppTokens` .</span><span class="sxs-lookup"><span data-stu-id="c628c-108">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="c628c-109">заполняет Указатель на указатель на массив, содержащий список возвращенных токенов.</span><span class="sxs-lookup"><span data-stu-id="c628c-109">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="c628c-110">заполняет Указатель на указатель на имя маркера в `ixCdTkn` .</span><span class="sxs-lookup"><span data-stu-id="c628c-110">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c628c-111">Требования</span><span class="sxs-lookup"><span data-stu-id="c628c-111">Requirements</span></span>  

 <span data-ttu-id="c628c-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c628c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c628c-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c628c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c628c-114">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c628c-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c628c-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c628c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c628c-116">См. также</span><span class="sxs-lookup"><span data-stu-id="c628c-116">See also</span></span>

- [<span data-ttu-id="c628c-117">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="c628c-117">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="c628c-118">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="c628c-118">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
