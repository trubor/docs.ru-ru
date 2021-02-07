---
description: Дополнительные сведения о функции StrongNameGetBlob
title: Функция StrongNameGetBlob
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
ms.openlocfilehash: 72f7ce50ce6170a23e5b24b68f911ff58bebe3bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736444"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="fd50c-103">Функция StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="fd50c-103">StrongNameGetBlob Function</span></span>

<span data-ttu-id="fd50c-104">Заполняет указанный буфер двоичным представлением исполняемого файла по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="fd50c-104">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="fd50c-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="fd50c-105">This function has been deprecated.</span></span> <span data-ttu-id="fd50c-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fd50c-106">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd50c-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fd50c-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd50c-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="fd50c-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="fd50c-109">окне Допустимый путь к исполняемому файлу для загрузки.</span><span class="sxs-lookup"><span data-stu-id="fd50c-109">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="fd50c-110">окне Буфер, в который загружается исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="fd50c-110">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="fd50c-111">[вход, выход] Запрошенный максимальный размер (в байтах) `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="fd50c-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="fd50c-112">При возврате фактический размер (в байтах) для `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="fd50c-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd50c-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fd50c-113">Return Value</span></span>  

 <span data-ttu-id="fd50c-114">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="fd50c-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd50c-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="fd50c-115">Remarks</span></span>  

 <span data-ttu-id="fd50c-116">Если `StrongNameGetBlob` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="fd50c-116">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd50c-117">Требования</span><span class="sxs-lookup"><span data-stu-id="fd50c-117">Requirements</span></span>  

 <span data-ttu-id="fd50c-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd50c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd50c-119">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="fd50c-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="fd50c-120">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fd50c-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd50c-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd50c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd50c-122">См. также</span><span class="sxs-lookup"><span data-stu-id="fd50c-122">See also</span></span>

- [<span data-ttu-id="fd50c-123">Метод StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="fd50c-123">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="fd50c-124">Метод StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="fd50c-124">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="fd50c-125">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="fd50c-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
