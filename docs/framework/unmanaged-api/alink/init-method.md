---
description: Дополнительные сведения о методе init
title: Метод Init
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
ms.openlocfilehash: 531e05a09cbecbfb67c8c004d1e4ba1deb7e59a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662563"
---
# <a name="init-method"></a><span data-ttu-id="f6313-103">Метод Init</span><span class="sxs-lookup"><span data-stu-id="f6313-103">Init Method</span></span>

<span data-ttu-id="f6313-104">Подготавливает объекты, реализующие [интерфейс иалинк](ialink-interface.md) для использования.</span><span class="sxs-lookup"><span data-stu-id="f6313-104">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6313-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f6313-105">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6313-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f6313-106">Parameters</span></span>  

 `pDispenser`  
 <span data-ttu-id="f6313-107">Указатель [интерфейса IMetaDataDispenserEx](../metadata/imetadatadispenserex-interface.md) на распределитель метаданных.</span><span class="sxs-lookup"><span data-stu-id="f6313-107">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="f6313-108">Указатель [интерфейса IMetaDataError](../metadata/imetadataerror-interface.md) на необязательный интерфейс обработки ошибок.</span><span class="sxs-lookup"><span data-stu-id="f6313-108">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6313-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f6313-109">Return Value</span></span>  

 <span data-ttu-id="f6313-110">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="f6313-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6313-111">Требования</span><span class="sxs-lookup"><span data-stu-id="f6313-111">Requirements</span></span>  

 <span data-ttu-id="f6313-112">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="f6313-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6313-113">См. также</span><span class="sxs-lookup"><span data-stu-id="f6313-113">See also</span></span>

- [<span data-ttu-id="f6313-114">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="f6313-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="f6313-115">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="f6313-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="f6313-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="f6313-116">ALink API</span></span>](index.md)
