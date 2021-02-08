---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameGetBlob'
title: Метод ICLRStrongName::StrongNameGetBlob
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
ms.openlocfilehash: 2b63ebd9c48ad18eef60f83c68fe412a4bd0d94f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799633"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="b19e9-103">Метод ICLRStrongName::StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="b19e9-103">ICLRStrongName::StrongNameGetBlob Method</span></span>

<span data-ttu-id="b19e9-104">Заполняет указанный буфер двоичным представлением исполняемого файла по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="b19e9-104">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b19e9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b19e9-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b19e9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b19e9-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="b19e9-107">окне Допустимый путь к исполняемому файлу для загрузки.</span><span class="sxs-lookup"><span data-stu-id="b19e9-107">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="b19e9-108">окне Буфер, в который загружается исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="b19e9-108">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="b19e9-109">[вход, выход] Запрошенный максимальный размер (в байтах) `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="b19e9-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="b19e9-110">При возврате фактический размер (в байтах) для `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="b19e9-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b19e9-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b19e9-111">Return Value</span></span>  

 <span data-ttu-id="b19e9-112">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="b19e9-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b19e9-113">Требования</span><span class="sxs-lookup"><span data-stu-id="b19e9-113">Requirements</span></span>  

 <span data-ttu-id="b19e9-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b19e9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b19e9-115">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="b19e9-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b19e9-116">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b19e9-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b19e9-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b19e9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b19e9-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b19e9-118">See also</span></span>

- [<span data-ttu-id="b19e9-119">Метод StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="b19e9-119">StrongNameGetBlobFromImage Method</span></span>](iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="b19e9-120">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="b19e9-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
