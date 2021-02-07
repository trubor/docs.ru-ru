---
description: Дополнительные сведения о функции GetHashFromFile
title: Функция GetHashFromFile
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
ms.openlocfilehash: f91bfe8a3988b6aae563b5a852997d6fd3c309d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736600"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="a34db-103">Функция GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="a34db-103">GetHashFromFile Function</span></span>

<span data-ttu-id="a34db-104">Создает хэш содержимого указанного файла.</span><span class="sxs-lookup"><span data-stu-id="a34db-104">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="a34db-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="a34db-105">This function has been deprecated.</span></span> <span data-ttu-id="a34db-106">Используйте вместо этого метод [метод iclrstrongname:: GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a34db-106">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a34db-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a34db-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a34db-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="a34db-108">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="a34db-109">окне Имя файла для хэширования.</span><span class="sxs-lookup"><span data-stu-id="a34db-109">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="a34db-110">[вход, выход] Алгоритм, используемый при формировании хэша.</span><span class="sxs-lookup"><span data-stu-id="a34db-110">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="a34db-111">Допустимыми являются алгоритмы, определяемые интерфейсом Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="a34db-111">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="a34db-112">Если параметр `piHashAlg` имеет значение 0, используется алгоритм по умолчанию CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="a34db-112">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="a34db-113">заполняет Массив байтов, содержащий созданный хэш.</span><span class="sxs-lookup"><span data-stu-id="a34db-113">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="a34db-114">окне Максимальный размер буфера, `pbHash` на который указывает.</span><span class="sxs-lookup"><span data-stu-id="a34db-114">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="a34db-115">заполняет Размер возвращаемого объекта (в байтах) `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="a34db-115">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a34db-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="a34db-116">Remarks</span></span>  

 <span data-ttu-id="a34db-117">Эта функция аналогична [GetHashFromFileW](gethashfromfilew-function.md), за исключением того, что спецификация имени файла является ANSI, а не Unicode.</span><span class="sxs-lookup"><span data-stu-id="a34db-117">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a34db-118">Требования</span><span class="sxs-lookup"><span data-stu-id="a34db-118">Requirements</span></span>  

 <span data-ttu-id="a34db-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a34db-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a34db-120">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="a34db-120">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a34db-121">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a34db-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a34db-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a34db-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a34db-123">См. также</span><span class="sxs-lookup"><span data-stu-id="a34db-123">See also</span></span>

- [<span data-ttu-id="a34db-124">Метод GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="a34db-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="a34db-125">Метод GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="a34db-125">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="a34db-126">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a34db-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
