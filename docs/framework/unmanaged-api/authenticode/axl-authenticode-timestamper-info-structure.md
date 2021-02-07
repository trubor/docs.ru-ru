---
description: 'Дополнительные сведения: структура AXL_AUTHENTICODE_TIMESTAMPER_INFO'
title: Структура AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
ms.openlocfilehash: 35e30241c3c3b5747e247c57183e28e726c0cae3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747417"
---
# <a name="axl_authenticode_timestamper_info-structure"></a><span data-ttu-id="4a55e-103">Структура AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="4a55e-103">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>

<span data-ttu-id="4a55e-104">Определяет информацию об отметке времени Authenticode.</span><span class="sxs-lookup"><span data-stu-id="4a55e-104">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a55e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a55e-105">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="4a55e-106">Члены</span><span class="sxs-lookup"><span data-stu-id="4a55e-106">Members</span></span>  
  
|<span data-ttu-id="4a55e-107">Член</span><span class="sxs-lookup"><span data-stu-id="4a55e-107">Member</span></span>|<span data-ttu-id="4a55e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="4a55e-108">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="4a55e-109">Размер этой структуры.</span><span class="sxs-lookup"><span data-stu-id="4a55e-109">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="4a55e-110">Код ошибки.</span><span class="sxs-lookup"><span data-stu-id="4a55e-110">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="4a55e-111">Хэш-алгоритм.</span><span class="sxs-lookup"><span data-stu-id="4a55e-111">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="4a55e-112">Время отметки времени.</span><span class="sxs-lookup"><span data-stu-id="4a55e-112">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="4a55e-113">Контекст цепочки отметки времени.</span><span class="sxs-lookup"><span data-stu-id="4a55e-113">The time stamper’s chain context.</span></span>  <span data-ttu-id="4a55e-114">См. структуру [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="4a55e-114">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a55e-115">См. также</span><span class="sxs-lookup"><span data-stu-id="4a55e-115">See also</span></span>

- [<span data-ttu-id="4a55e-116">Authenticode</span><span class="sxs-lookup"><span data-stu-id="4a55e-116">Authenticode</span></span>](index.md)
