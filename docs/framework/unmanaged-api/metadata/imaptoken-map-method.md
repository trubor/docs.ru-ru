---
description: 'Дополнительные сведения о методе: IMapToken:: Map'
title: Метод IMapToken::Map
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
ms.openlocfilehash: da78f22e944a0e4ec25adcd7cdf97b69131a6612
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706740"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="ee668-103">Метод IMapToken::Map</span><span class="sxs-lookup"><span data-stu-id="ee668-103">IMapToken::Map Method</span></span>

<span data-ttu-id="ee668-104">Сопоставляет связь между сборками, используя подписи метаданных.</span><span class="sxs-lookup"><span data-stu-id="ee668-104">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee668-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ee668-105">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee668-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ee668-106">Parameters</span></span>  

 `tkImp`  
 <span data-ttu-id="ee668-107">окне Токен метаданных, представляющий импортированный объект кода.</span><span class="sxs-lookup"><span data-stu-id="ee668-107">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="ee668-108">окне Токен метаданных, представляющий созданный объект кода.</span><span class="sxs-lookup"><span data-stu-id="ee668-108">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee668-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="ee668-109">Remarks</span></span>  

 <span data-ttu-id="ee668-110">Когда повторное отображение токена происходит во время слияния, исходный маркер ограничивается в импортированной (исходной) области метаданных, а новый маркер — в области исрожденных (целевых) метаданных.</span><span class="sxs-lookup"><span data-stu-id="ee668-110">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee668-111">Требования</span><span class="sxs-lookup"><span data-stu-id="ee668-111">Requirements</span></span>  

 <span data-ttu-id="ee668-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee668-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee668-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="ee668-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee668-114">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ee668-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ee668-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee668-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee668-116">См. также</span><span class="sxs-lookup"><span data-stu-id="ee668-116">See also</span></span>

- [<span data-ttu-id="ee668-117">Интерфейс IMapToken</span><span class="sxs-lookup"><span data-stu-id="ee668-117">IMapToken Interface</span></span>](imaptoken-interface.md)
