---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameSignatureSize'
title: Метод ICLRStrongName::StrongNameSignatureSize
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
ms.openlocfilehash: 4c3804eea5b7c6325519b19546f25585af649866
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781861"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="bab82-103">Метод ICLRStrongName::StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="bab82-103">ICLRStrongName::StrongNameSignatureSize Method</span></span>

<span data-ttu-id="bab82-104">Возвращает размер подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="bab82-104">Returns the size of the strong name signature.</span></span> <span data-ttu-id="bab82-105">Этот метод обычно используется компиляторами для определения объема пространства, резервируемого в файле при создании сборки с отложенной подписью.</span><span class="sxs-lookup"><span data-stu-id="bab82-105">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bab82-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bab82-106">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="bab82-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="bab82-107">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="bab82-108">окне Структура типа [публиккэйблоб](../strong-naming/publickeyblob-structure.md) , содержащая открытую часть пары ключей, используемую для создания подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="bab82-108">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="bab82-109">окне Размер (в байтах) `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="bab82-109">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="bab82-110">окне Число байтов, необходимое для хранения подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="bab82-110">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bab82-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="bab82-111">Return Value</span></span>  

 <span data-ttu-id="bab82-112">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="bab82-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bab82-113">Требования</span><span class="sxs-lookup"><span data-stu-id="bab82-113">Requirements</span></span>  

 <span data-ttu-id="bab82-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bab82-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bab82-115">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="bab82-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bab82-116">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bab82-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bab82-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bab82-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab82-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="bab82-118">See also</span></span>

- [<span data-ttu-id="bab82-119">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="bab82-119">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
