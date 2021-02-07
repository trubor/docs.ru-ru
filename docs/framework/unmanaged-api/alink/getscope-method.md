---
description: Дополнительные сведения о методе "superscope"
title: Метод GetScope
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
ms.openlocfilehash: cdebda457573e70755b49798ae86eae8f076216b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718365"
---
# <a name="getscope-method"></a><span data-ttu-id="0e949-103">Метод GetScope</span><span class="sxs-lookup"><span data-stu-id="0e949-103">GetScope Method</span></span>

<span data-ttu-id="0e949-104">Возвращает область импорта.</span><span class="sxs-lookup"><span data-stu-id="0e949-104">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e949-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0e949-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e949-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0e949-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="0e949-107">Уникальный идентификатор сборки для импорта.</span><span class="sxs-lookup"><span data-stu-id="0e949-107">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="0e949-108">Уникальный идентификатор файла для импорта.</span><span class="sxs-lookup"><span data-stu-id="0e949-108">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="0e949-109">Отсчитываемая от нуля область для импорта.</span><span class="sxs-lookup"><span data-stu-id="0e949-109">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="0e949-110">Получает интерфейс [интерфейса IMetaDataImport](../metadata/imetadataimport-interface.md) для области.</span><span class="sxs-lookup"><span data-stu-id="0e949-110">Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e949-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0e949-111">Return Value</span></span>  

 <span data-ttu-id="0e949-112">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="0e949-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e949-113">Требования</span><span class="sxs-lookup"><span data-stu-id="0e949-113">Requirements</span></span>  

 <span data-ttu-id="0e949-114">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="0e949-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e949-115">См. также</span><span class="sxs-lookup"><span data-stu-id="0e949-115">See also</span></span>

- [<span data-ttu-id="0e949-116">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="0e949-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0e949-117">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="0e949-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0e949-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="0e949-118">ALink API</span></span>](index.md)
