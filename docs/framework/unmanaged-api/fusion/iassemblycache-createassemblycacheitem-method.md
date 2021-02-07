---
description: 'Дополнительные сведения о методе: IAssemblyCache:: Креатеассембликачеитем'
title: Метод IAssemblyCache::CreateAssemblyCacheItem
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
ms.openlocfilehash: 3377901d358bcf643ce0d30336c1c0cd8089e50c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760983"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="343b2-103">Метод IAssemblyCache::CreateAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="343b2-103">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>

<span data-ttu-id="343b2-104">Возвращает ссылку на новый объект [IAssemblyCacheItem](iassemblycacheitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="343b2-104">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="343b2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="343b2-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="343b2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="343b2-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="343b2-107">окне Флаги, определенные в Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="343b2-107">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="343b2-108">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="343b2-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="343b2-109">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="343b2-109">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="343b2-110">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="343b2-110">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="343b2-111">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="343b2-111">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="343b2-112">`pvReserved` должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="343b2-112">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="343b2-113">заполняет Возвращаемый `IAssemblyCacheItem` указатель.</span><span class="sxs-lookup"><span data-stu-id="343b2-113">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="343b2-114">[входные, необязательные] Неканонические пары, разделенные запятыми `name=value` .</span><span class="sxs-lookup"><span data-stu-id="343b2-114">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="343b2-115">Требования</span><span class="sxs-lookup"><span data-stu-id="343b2-115">Requirements</span></span>  

 <span data-ttu-id="343b2-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="343b2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="343b2-117">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="343b2-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="343b2-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="343b2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343b2-119">См. также</span><span class="sxs-lookup"><span data-stu-id="343b2-119">See also</span></span>

- [<span data-ttu-id="343b2-120">Интерфейс IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="343b2-120">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="343b2-121">Интерфейс IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="343b2-121">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
