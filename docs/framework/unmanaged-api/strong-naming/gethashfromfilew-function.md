---
description: Дополнительные сведения о функции GetHashFromFileW
title: Функция GetHashFromFileW
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
ms.openlocfilehash: daebd06de02dfe936f1bdeb8697de4fe6524dce3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736571"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="2fdf7-103">Функция GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="2fdf7-103">GetHashFromFileW Function</span></span>

<span data-ttu-id="2fdf7-104">Создает хэш содержимого файла, указанного строкой Юникода.</span><span class="sxs-lookup"><span data-stu-id="2fdf7-104">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="2fdf7-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="2fdf7-105">This function has been deprecated.</span></span> <span data-ttu-id="2fdf7-106">Используйте вместо этого метод [метод iclrstrongname:: GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2fdf7-106">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fdf7-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2fdf7-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="2fdf7-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="2fdf7-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="2fdf7-109">окне Имя файла в Юникоде для хэширования.</span><span class="sxs-lookup"><span data-stu-id="2fdf7-109">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2fdf7-110">[вход, выход] Алгоритм, используемый при формировании хэша.</span><span class="sxs-lookup"><span data-stu-id="2fdf7-110">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="2fdf7-111">Допустимыми являются алгоритмы, определяемые интерфейсом Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="2fdf7-111">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="2fdf7-112">Если параметр `piHashAlg` имеет значение 0, используется алгоритм по умолчанию CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="2fdf7-112">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2fdf7-113">заполняет Массив байтов, содержащий созданный хэш.</span><span class="sxs-lookup"><span data-stu-id="2fdf7-113">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2fdf7-114">окне Максимальный размер буфера, на который указывает `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="2fdf7-114">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2fdf7-115">заполняет Размер (в байтах) `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="2fdf7-115">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fdf7-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="2fdf7-116">Remarks</span></span>  

 <span data-ttu-id="2fdf7-117">Эта функция аналогична [GetHashFromFile](gethashfromfile-function.md), за исключением того, что спецификация имени файла имеет кодировку Unicode, а не ANSI.</span><span class="sxs-lookup"><span data-stu-id="2fdf7-117">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fdf7-118">Требования</span><span class="sxs-lookup"><span data-stu-id="2fdf7-118">Requirements</span></span>  

 <span data-ttu-id="2fdf7-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fdf7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fdf7-120">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="2fdf7-120">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2fdf7-121">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2fdf7-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2fdf7-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fdf7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fdf7-123">См. также</span><span class="sxs-lookup"><span data-stu-id="2fdf7-123">See also</span></span>

- [<span data-ttu-id="2fdf7-124">Метод GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="2fdf7-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="2fdf7-125">Метод GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="2fdf7-125">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="2fdf7-126">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="2fdf7-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
