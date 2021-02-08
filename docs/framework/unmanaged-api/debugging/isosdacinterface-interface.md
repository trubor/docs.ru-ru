---
description: 'Дополнительные сведения о: интерфейс ИсосдаЦинтерфаце'
title: Интерфейс ISOSDacInterface
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ddb99b7c6fca6870024f04933861d01e4b31ea9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790403"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="ba2e3-103">Интерфейс ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="ba2e3-103">ISOSDacInterface Interface</span></span>

<span data-ttu-id="ba2e3-104">Предоставляет вспомогательные методы для доступа к данным из `SOS` .</span><span class="sxs-lookup"><span data-stu-id="ba2e3-104">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="ba2e3-105">Методы</span><span class="sxs-lookup"><span data-stu-id="ba2e3-105">Methods</span></span>

| <span data-ttu-id="ba2e3-106">Метод</span><span class="sxs-lookup"><span data-stu-id="ba2e3-106">Method</span></span>                                                                                                               | <span data-ttu-id="ba2e3-107">Описание</span><span class="sxs-lookup"><span data-stu-id="ba2e3-107">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="ba2e3-108">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="ba2e3-108">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="ba2e3-109">Возвращает данные для заданного указателя MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="ba2e3-109">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="ba2e3-110">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="ba2e3-110">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="ba2e3-111">Получает указатель MethodDesc, соответствующий методу, содержащему указанный адрес собственной инструкции.</span><span class="sxs-lookup"><span data-stu-id="ba2e3-111">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="ba2e3-112">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="ba2e3-112">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="ba2e3-113">Извлекает данные, соответствующие модулю, загруженному по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="ba2e3-113">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ba2e3-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="ba2e3-114">Remarks</span></span>

<span data-ttu-id="ba2e3-115">Этот интерфейс находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="ba2e3-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ba2e3-116">Однако это COM-интерфейс, производный от `IUnknown` GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` , который можно получить с помощью стандартных механизмов com.</span><span class="sxs-lookup"><span data-stu-id="ba2e3-116">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba2e3-117">Требования</span><span class="sxs-lookup"><span data-stu-id="ba2e3-117">Requirements</span></span>

<span data-ttu-id="ba2e3-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba2e3-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ba2e3-119">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="ba2e3-119">**Header:** None</span></span>  
<span data-ttu-id="ba2e3-120">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="ba2e3-120">**Library:** None</span></span>  
<span data-ttu-id="ba2e3-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ba2e3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ba2e3-122">См. также</span><span class="sxs-lookup"><span data-stu-id="ba2e3-122">See also</span></span>

- [<span data-ttu-id="ba2e3-123">Отладка</span><span class="sxs-lookup"><span data-stu-id="ba2e3-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="ba2e3-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="ba2e3-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
