---
description: Дополнительные сведения о функции StrongNameGetBlobFromImage
title: Функция StrongNameGetBlobFromImage
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
ms.openlocfilehash: c68d6914d47fbb711c49c1e8432cae1bf33e771f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636355"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="17a48-103">Функция StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="17a48-103">StrongNameGetBlobFromImage Function</span></span>

<span data-ttu-id="17a48-104">Получает двоичное представление образа сборки по указанному адресу памяти.</span><span class="sxs-lookup"><span data-stu-id="17a48-104">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="17a48-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="17a48-105">This function has been deprecated.</span></span> <span data-ttu-id="17a48-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) .</span><span class="sxs-lookup"><span data-stu-id="17a48-106">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17a48-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17a48-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17a48-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="17a48-108">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="17a48-109">окне Адрес сопоставленного манифеста сборки в памяти.</span><span class="sxs-lookup"><span data-stu-id="17a48-109">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="17a48-110">окне Размер изображения в байтах в `pbBase` .</span><span class="sxs-lookup"><span data-stu-id="17a48-110">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="17a48-111">окне Буфер для хранения двоичного представления изображения.</span><span class="sxs-lookup"><span data-stu-id="17a48-111">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="17a48-112">[вход, выход] Запрошенный максимальный размер (в байтах) `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="17a48-112">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="17a48-113">При возврате фактический размер (в байтах) для `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="17a48-113">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17a48-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="17a48-114">Return Value</span></span>  

 <span data-ttu-id="17a48-115">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="17a48-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17a48-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="17a48-116">Remarks</span></span>  

 <span data-ttu-id="17a48-117">Если `StrongNameGetBlobFromImage` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="17a48-117">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17a48-118">Требования</span><span class="sxs-lookup"><span data-stu-id="17a48-118">Requirements</span></span>  

 <span data-ttu-id="17a48-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17a48-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17a48-120">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="17a48-120">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="17a48-121">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17a48-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17a48-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17a48-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a48-123">См. также</span><span class="sxs-lookup"><span data-stu-id="17a48-123">See also</span></span>

- [<span data-ttu-id="17a48-124">Метод StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="17a48-124">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="17a48-125">Метод StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="17a48-125">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="17a48-126">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="17a48-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
