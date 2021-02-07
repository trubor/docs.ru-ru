---
description: Дополнительные сведения о функции StrongNameSignatureSize
title: Функция StrongNameSignatureSize
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: b3f22a6a4d5455af4dd17cb75edfd18befed7de3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670532"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="cb971-103">Функция StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="cb971-103">StrongNameSignatureSize Function</span></span>

<span data-ttu-id="cb971-104">Возвращает размер подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="cb971-104">Returns the size of the strong name signature.</span></span> <span data-ttu-id="cb971-105">`StrongNameSignatureSize` обычно используется компиляторами для определения объема пространства, резервируемого в файле при создании сборки с отложенной подписью.</span><span class="sxs-lookup"><span data-stu-id="cb971-105">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="cb971-106">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="cb971-106">This function has been deprecated.</span></span> <span data-ttu-id="cb971-107">Используйте вместо этого метод [метод iclrstrongname:: StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cb971-107">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb971-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cb971-108">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="cb971-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="cb971-109">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="cb971-110">окне Структура типа [публиккэйблоб](publickeyblob-structure.md) , содержащая открытую часть пары ключей, используемую для создания подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="cb971-110">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="cb971-111">окне Размер (в байтах) `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="cb971-111">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="cb971-112">окне Число байтов, необходимое для хранения подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="cb971-112">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb971-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cb971-113">Return Value</span></span>  

 <span data-ttu-id="cb971-114">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="cb971-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb971-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="cb971-115">Remarks</span></span>  

 <span data-ttu-id="cb971-116">Если `StrongNameSignatureSize` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="cb971-116">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb971-117">Требования</span><span class="sxs-lookup"><span data-stu-id="cb971-117">Requirements</span></span>  

 <span data-ttu-id="cb971-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb971-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb971-119">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="cb971-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cb971-120">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb971-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb971-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb971-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb971-122">См. также</span><span class="sxs-lookup"><span data-stu-id="cb971-122">See also</span></span>

- [<span data-ttu-id="cb971-123">Метод StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="cb971-123">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="cb971-124">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="cb971-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
