---
description: 'Дополнительные сведения о: интерфейс IInstallReferenceEnum'
title: Интерфейс IInstallReferenceEnum
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
ms.openlocfilehash: 496bd508b95b51cb23949f32f8390c7cb733b37e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800110"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="b5b0f-103">Интерфейс IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="b5b0f-103">IInstallReferenceEnum Interface</span></span>

<span data-ttu-id="b5b0f-104">Представляет перечислитель для сборок, на которые имеются ссылки, установленных в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="b5b0f-104">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5b0f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b5b0f-105">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b5b0f-106">Методы</span><span class="sxs-lookup"><span data-stu-id="b5b0f-106">Methods</span></span>  
  
|<span data-ttu-id="b5b0f-107">Метод</span><span class="sxs-lookup"><span data-stu-id="b5b0f-107">Method</span></span>|<span data-ttu-id="b5b0f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b5b0f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5b0f-109">Метод GetNextInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="b5b0f-109">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="b5b0f-110">Возвращает указатель на следующий объект, `IInstallReferenceItem` содержащийся в этом `IInstallReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="b5b0f-110">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5b0f-111">Требования</span><span class="sxs-lookup"><span data-stu-id="b5b0f-111">Requirements</span></span>  

 <span data-ttu-id="b5b0f-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5b0f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5b0f-113">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b5b0f-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b5b0f-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5b0f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5b0f-115">См. также</span><span class="sxs-lookup"><span data-stu-id="b5b0f-115">See also</span></span>

- [<span data-ttu-id="b5b0f-116">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="b5b0f-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="b5b0f-117">Интерфейс IInstallReferenceItem</span><span class="sxs-lookup"><span data-stu-id="b5b0f-117">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
