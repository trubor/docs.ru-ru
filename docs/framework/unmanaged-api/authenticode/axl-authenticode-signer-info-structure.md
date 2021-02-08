---
description: 'Дополнительные сведения: структура AXL_AUTHENTICODE_SIGNER_INFO'
title: Структура AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
ms.openlocfilehash: 940652cf184e26f141df806b060c391333d1bb95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781965"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="8cfd8-103">Структура AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="8cfd8-103">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>

<span data-ttu-id="8cfd8-104">Определяет информацию о подписавшем Authenticode.</span><span class="sxs-lookup"><span data-stu-id="8cfd8-104">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cfd8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8cfd8-105">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="8cfd8-106">Члены</span><span class="sxs-lookup"><span data-stu-id="8cfd8-106">Members</span></span>  
  
|<span data-ttu-id="8cfd8-107">Член</span><span class="sxs-lookup"><span data-stu-id="8cfd8-107">Member</span></span>|<span data-ttu-id="8cfd8-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8cfd8-108">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="8cfd8-109">Размер этой структуры.</span><span class="sxs-lookup"><span data-stu-id="8cfd8-109">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="8cfd8-110">Код ошибки.</span><span class="sxs-lookup"><span data-stu-id="8cfd8-110">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="8cfd8-111">Хэш-алгоритм.</span><span class="sxs-lookup"><span data-stu-id="8cfd8-111">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="8cfd8-112">Хэш-код.</span><span class="sxs-lookup"><span data-stu-id="8cfd8-112">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="8cfd8-113">Описание.</span><span class="sxs-lookup"><span data-stu-id="8cfd8-113">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="8cfd8-114">URL-адрес описания.</span><span class="sxs-lookup"><span data-stu-id="8cfd8-114">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="8cfd8-115">Контекст цепочки подписавшего.</span><span class="sxs-lookup"><span data-stu-id="8cfd8-115">The chain context of the signer.</span></span> <span data-ttu-id="8cfd8-116">См. структуру [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="8cfd8-116">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cfd8-117">См. также</span><span class="sxs-lookup"><span data-stu-id="8cfd8-117">See also</span></span>

- [<span data-ttu-id="8cfd8-118">Authenticode</span><span class="sxs-lookup"><span data-stu-id="8cfd8-118">Authenticode</span></span>](index.md)
