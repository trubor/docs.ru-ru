---
description: Дополнительные сведения о методе EnumCustomAttributes
title: Метод EnumCustomAttributes
ms.date: 03/30/2017
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
ms.openlocfilehash: d5b537462745914903f0cdb1e9f4436f2c27a68d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638140"
---
# <a name="enumcustomattributes-method"></a><span data-ttu-id="1dd04-103">Метод EnumCustomAttributes</span><span class="sxs-lookup"><span data-stu-id="1dd04-103">EnumCustomAttributes Method</span></span>

<span data-ttu-id="1dd04-104">Извлекает настраиваемые атрибуты уровня сборки.</span><span class="sxs-lookup"><span data-stu-id="1dd04-104">Retrieves assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd04-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1dd04-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dd04-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1dd04-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="1dd04-107">Маркер перечислителя.</span><span class="sxs-lookup"><span data-stu-id="1dd04-107">Handle of enumerator.</span></span>  
  
 `tkType`  
 <span data-ttu-id="1dd04-108">Тип атрибутов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="1dd04-108">Type of attributes to be enumerated.</span></span> <span data-ttu-id="1dd04-109">Используется `mdTokenNill` для всех атрибутов.</span><span class="sxs-lookup"><span data-stu-id="1dd04-109">Use `mdTokenNill` for all attributes.</span></span>  
  
 `rCustomValues`  
 <span data-ttu-id="1dd04-110">Получает маркеры настраиваемых атрибутов.</span><span class="sxs-lookup"><span data-stu-id="1dd04-110">Receives custom attributes tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1dd04-111">Задает размер `rCustomValues` массива.</span><span class="sxs-lookup"><span data-stu-id="1dd04-111">Specifies size of `rCustomValues` array.</span></span>  
  
 `pcCustomValues`  
 <span data-ttu-id="1dd04-112">При необходимости получает число значений токена.</span><span class="sxs-lookup"><span data-stu-id="1dd04-112">Optionally receives count of token values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dd04-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1dd04-113">Return Value</span></span>  

 <span data-ttu-id="1dd04-114">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="1dd04-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd04-115">Требования</span><span class="sxs-lookup"><span data-stu-id="1dd04-115">Requirements</span></span>  

 <span data-ttu-id="1dd04-116">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="1dd04-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd04-117">См. также</span><span class="sxs-lookup"><span data-stu-id="1dd04-117">See also</span></span>

- [<span data-ttu-id="1dd04-118">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="1dd04-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="1dd04-119">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="1dd04-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="1dd04-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="1dd04-120">ALink API</span></span>](index.md)
