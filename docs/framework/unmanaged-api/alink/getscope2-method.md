---
description: Дополнительные сведения о методе GetScope2
title: Метод GetScope2
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
ms.openlocfilehash: 9a68f02a638b58e7a70207d8610607bf24b2b96b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718347"
---
# <a name="getscope2-method"></a><span data-ttu-id="13c83-103">Метод GetScope2</span><span class="sxs-lookup"><span data-stu-id="13c83-103">GetScope2 Method</span></span>

<span data-ttu-id="13c83-104">Возвращает область импорта.</span><span class="sxs-lookup"><span data-stu-id="13c83-104">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c83-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="13c83-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="13c83-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="13c83-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="13c83-107">Идентификатор целевой сборки.</span><span class="sxs-lookup"><span data-stu-id="13c83-107">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="13c83-108">Идентификатор файла, из которого необходимо выполнить импорт.</span><span class="sxs-lookup"><span data-stu-id="13c83-108">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="13c83-109">Отсчитываемая от нуля область для импорта.</span><span class="sxs-lookup"><span data-stu-id="13c83-109">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="13c83-110">Получает указатель на интерфейс интерфейса [IMetaDataImport2](../metadata/imetadataimport2-interface.md) для указанной области.</span><span class="sxs-lookup"><span data-stu-id="13c83-110">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13c83-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="13c83-111">Return Value</span></span>  

 <span data-ttu-id="13c83-112">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="13c83-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c83-113">Требования</span><span class="sxs-lookup"><span data-stu-id="13c83-113">Requirements</span></span>  

 <span data-ttu-id="13c83-114">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="13c83-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c83-115">См. также</span><span class="sxs-lookup"><span data-stu-id="13c83-115">See also</span></span>

- [<span data-ttu-id="13c83-116">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="13c83-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="13c83-117">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="13c83-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="13c83-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="13c83-118">ALink API</span></span>](index.md)
