---
description: Дополнительные сведения о методе LinkResource
title: Метод LinkResource
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
ms.openlocfilehash: ff12138433577eccbb313b8e64a329be1358ba70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662550"
---
# <a name="linkresource-method"></a><span data-ttu-id="41fe7-103">Метод LinkResource</span><span class="sxs-lookup"><span data-stu-id="41fe7-103">LinkResource Method</span></span>

<span data-ttu-id="41fe7-104">Ссылки в ресурсе.</span><span class="sxs-lookup"><span data-stu-id="41fe7-104">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41fe7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="41fe7-105">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="41fe7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="41fe7-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="41fe7-107">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="41fe7-107">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="41fe7-108">Имя файла.</span><span class="sxs-lookup"><span data-stu-id="41fe7-108">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="41fe7-109">Необязательное новое имя файла.</span><span class="sxs-lookup"><span data-stu-id="41fe7-109">Optional new file name.</span></span> <span data-ttu-id="41fe7-110">Если значение не равно NULL, `pszFileName` будет скопировано в псзневлокатион.</span><span class="sxs-lookup"><span data-stu-id="41fe7-110">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="41fe7-111">Имя ресурса.</span><span class="sxs-lookup"><span data-stu-id="41fe7-111">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="41fe7-112">Флаги специальных возможностей, такие как `mrPublic` и `mrPrivate` .</span><span class="sxs-lookup"><span data-stu-id="41fe7-112">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="41fe7-113">Этот параметр может быть передан [методу DefineManifestResource](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="41fe7-113">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41fe7-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="41fe7-114">Return Value</span></span>  

 <span data-ttu-id="41fe7-115">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="41fe7-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41fe7-116">Требования</span><span class="sxs-lookup"><span data-stu-id="41fe7-116">Requirements</span></span>  

 <span data-ttu-id="41fe7-117">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="41fe7-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41fe7-118">См. также</span><span class="sxs-lookup"><span data-stu-id="41fe7-118">See also</span></span>

- [<span data-ttu-id="41fe7-119">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="41fe7-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="41fe7-120">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="41fe7-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="41fe7-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="41fe7-121">ALink API</span></span>](index.md)
