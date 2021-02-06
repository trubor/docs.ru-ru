---
description: Дополнительные сведения о методе Ембедресаурце
title: Метод EmbedResource
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
ms.openlocfilehash: f7896172e7416048352788caf7e092096924b7af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638357"
---
# <a name="embedresource-method"></a><span data-ttu-id="078bf-103">Метод EmbedResource</span><span class="sxs-lookup"><span data-stu-id="078bf-103">EmbedResource Method</span></span>

<span data-ttu-id="078bf-104">Объявляет внедренный ресурс.</span><span class="sxs-lookup"><span data-stu-id="078bf-104">Declares an embedded resource.</span></span> <span data-ttu-id="078bf-105">Этот метод фактически не внедряет ресурс.</span><span class="sxs-lookup"><span data-stu-id="078bf-105">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="078bf-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="078bf-106">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="078bf-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="078bf-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="078bf-108">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="078bf-108">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="078bf-109">Маркер файла или идентификатор сборки файла, содержащего ресурс.</span><span class="sxs-lookup"><span data-stu-id="078bf-109">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="078bf-110">Имя ресурса.</span><span class="sxs-lookup"><span data-stu-id="078bf-110">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="078bf-111">Смещение ресурса от RVA.</span><span class="sxs-lookup"><span data-stu-id="078bf-111">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="078bf-112">Флаги специальных возможностей, такие как `mrPublic` и `mrPrivate` .</span><span class="sxs-lookup"><span data-stu-id="078bf-112">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="078bf-113">Эти флаги можно передать в [метод дефиникспортедтипе](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="078bf-113">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="078bf-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="078bf-114">Return Value</span></span>  

 <span data-ttu-id="078bf-115">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="078bf-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="078bf-116">Требования</span><span class="sxs-lookup"><span data-stu-id="078bf-116">Requirements</span></span>  

 <span data-ttu-id="078bf-117">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="078bf-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="078bf-118">См. также</span><span class="sxs-lookup"><span data-stu-id="078bf-118">See also</span></span>

- [<span data-ttu-id="078bf-119">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="078bf-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="078bf-120">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="078bf-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="078bf-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="078bf-121">ALink API</span></span>](index.md)
