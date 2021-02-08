---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameGetBlobFromImage'
title: Метод ICLRStrongName::StrongNameGetBlobFromImage
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
ms.openlocfilehash: 32f04e21f1f08f3872ccdd27a64f39ea29d7e060
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799620"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="83a15-103">Метод ICLRStrongName::StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="83a15-103">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>

<span data-ttu-id="83a15-104">Получает двоичное представление образа сборки по указанному адресу памяти.</span><span class="sxs-lookup"><span data-stu-id="83a15-104">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83a15-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83a15-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83a15-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="83a15-106">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="83a15-107">окне Адрес сопоставленного манифеста сборки в памяти.</span><span class="sxs-lookup"><span data-stu-id="83a15-107">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="83a15-108">окне Размер изображения в байтах в `pbBase` .</span><span class="sxs-lookup"><span data-stu-id="83a15-108">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="83a15-109">окне Буфер для хранения двоичного представления изображения.</span><span class="sxs-lookup"><span data-stu-id="83a15-109">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="83a15-110">[вход, выход] Запрошенный максимальный размер (в байтах) `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="83a15-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="83a15-111">При возврате фактический размер (в байтах) для `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="83a15-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83a15-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="83a15-112">Return Value</span></span>  

 <span data-ttu-id="83a15-113">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="83a15-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83a15-114">Требования</span><span class="sxs-lookup"><span data-stu-id="83a15-114">Requirements</span></span>  

 <span data-ttu-id="83a15-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83a15-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83a15-116">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="83a15-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="83a15-117">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83a15-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83a15-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83a15-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a15-119">См. также</span><span class="sxs-lookup"><span data-stu-id="83a15-119">See also</span></span>

- [<span data-ttu-id="83a15-120">Метод StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="83a15-120">StrongNameGetBlob Method</span></span>](iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="83a15-121">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="83a15-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
