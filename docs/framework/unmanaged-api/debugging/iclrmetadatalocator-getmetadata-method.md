---
description: 'Дополнительные сведения о методе: Иклрметадаталокатор:: with Metadata'
title: Метод ICLRMetadataLocator::GetMetadata
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
ms.openlocfilehash: 4a7e8b906b66c4295dd24800d260790526114701
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772627"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="0cde2-103">Метод ICLRMetadataLocator::GetMetadata</span><span class="sxs-lookup"><span data-stu-id="0cde2-103">ICLRMetadataLocator::GetMetadata Method</span></span>

<span data-ttu-id="0cde2-104">Вызывается службами доступа к данным среды CLR для получения метаданных изображения.</span><span class="sxs-lookup"><span data-stu-id="0cde2-104">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cde2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0cde2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cde2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0cde2-106">Parameters</span></span>  

 `imagePath`  
 <span data-ttu-id="0cde2-107">окне Строка, указывающая путь к файлу изображения.</span><span class="sxs-lookup"><span data-stu-id="0cde2-107">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="0cde2-108">окне Метка времени файла изображения.</span><span class="sxs-lookup"><span data-stu-id="0cde2-108">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="0cde2-109">окне Размер файла изображения.</span><span class="sxs-lookup"><span data-stu-id="0cde2-109">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="0cde2-110">окне Глобальный уникальный идентификатор изображения.</span><span class="sxs-lookup"><span data-stu-id="0cde2-110">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="0cde2-111">окне Относительный виртуальный адрес (RVA) метаданных.</span><span class="sxs-lookup"><span data-stu-id="0cde2-111">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="0cde2-112">Адрес отсчитывается относительно базового адреса образа.</span><span class="sxs-lookup"><span data-stu-id="0cde2-112">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="0cde2-113">[in] Зарезервирован для будущего использования.</span><span class="sxs-lookup"><span data-stu-id="0cde2-113">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="0cde2-114">окне Размер буфера, в который следует поместить метаданные.</span><span class="sxs-lookup"><span data-stu-id="0cde2-114">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="0cde2-115">заполняет Буфер для размещения метаданных.</span><span class="sxs-lookup"><span data-stu-id="0cde2-115">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="0cde2-116">заполняет Размер возвращаемых метаданных.</span><span class="sxs-lookup"><span data-stu-id="0cde2-116">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cde2-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="0cde2-117">Remarks</span></span>  

 <span data-ttu-id="0cde2-118">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="0cde2-118">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cde2-119">Требования</span><span class="sxs-lookup"><span data-stu-id="0cde2-119">Requirements</span></span>  

 <span data-ttu-id="0cde2-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cde2-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cde2-121">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="0cde2-121">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0cde2-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cde2-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cde2-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cde2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cde2-124">См. также</span><span class="sxs-lookup"><span data-stu-id="0cde2-124">See also</span></span>

- [<span data-ttu-id="0cde2-125">Интерфейс ICLRMetadataLocator</span><span class="sxs-lookup"><span data-stu-id="0cde2-125">ICLRMetadataLocator Interface</span></span>](iclrmetadatalocator-interface.md)
