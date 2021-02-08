---
description: 'Дополнительные сведения о методе: ICLRDataTarget:: GetImageBase'
title: Метод ICLRDataTarget::GetImageBase
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
ms.openlocfilehash: 34e8341b219aaa184b4894c631f854e0a31921d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794875"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="5bc48-103">Метод ICLRDataTarget::GetImageBase</span><span class="sxs-lookup"><span data-stu-id="5bc48-103">ICLRDataTarget::GetImageBase Method</span></span>

<span data-ttu-id="5bc48-104">Возвращает адрес базовой памяти указанного образа.</span><span class="sxs-lookup"><span data-stu-id="5bc48-104">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc48-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5bc48-105">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bc48-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5bc48-106">Parameters</span></span>  

 `imagePath`  
 <span data-ttu-id="5bc48-107">окне Имя файла образа, включая его путь.</span><span class="sxs-lookup"><span data-stu-id="5bc48-107">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="5bc48-108">заполняет Указатель на CLRDATA_ADDRESS, в котором хранится базовый адрес изображения.</span><span class="sxs-lookup"><span data-stu-id="5bc48-108">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bc48-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="5bc48-109">Remarks</span></span>  

 <span data-ttu-id="5bc48-110">Имя файла изображения может содержать или не иметь пути.</span><span class="sxs-lookup"><span data-stu-id="5bc48-110">The image file name may or may not have a path.</span></span> <span data-ttu-id="5bc48-111">Если указан путь, сопоставление выполняется по всему пути; в противном случае сопоставление выполняется только с именем файла.</span><span class="sxs-lookup"><span data-stu-id="5bc48-111">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bc48-112">Требования</span><span class="sxs-lookup"><span data-stu-id="5bc48-112">Requirements</span></span>  

 <span data-ttu-id="5bc48-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bc48-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bc48-114">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="5bc48-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5bc48-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bc48-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bc48-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bc48-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc48-117">См. также</span><span class="sxs-lookup"><span data-stu-id="5bc48-117">See also</span></span>

- [<span data-ttu-id="5bc48-118">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="5bc48-118">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
