---
description: Дополнительные сведения о функции GetHashFromAssemblyFileW
title: Функция GetHashFromAssemblyFileW
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
ms.openlocfilehash: 7f44106f12a2d21ea67acb874b577c5b303632b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736678"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="a5047-103">Функция GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="a5047-103">GetHashFromAssemblyFileW Function</span></span>

<span data-ttu-id="a5047-104">Получает хэш указанного файла сборки с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="a5047-104">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="a5047-105">Путь к файлу сборки должен быть указан в виде строки в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="a5047-105">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="a5047-106">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="a5047-106">This function has been deprecated.</span></span> <span data-ttu-id="a5047-107">Используйте вместо этого метод [метод iclrstrongname:: GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a5047-107">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5047-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a5047-108">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5047-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="a5047-109">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="a5047-110">окне Путь к файлу для хэширования.</span><span class="sxs-lookup"><span data-stu-id="a5047-110">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="a5047-111">Этот параметр должен быть строкой в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="a5047-111">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="a5047-112">[вход, выход] Константа, указывающая хэш-алгоритм.</span><span class="sxs-lookup"><span data-stu-id="a5047-112">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="a5047-113">Для алгоритма хэширования по умолчанию используется нуль.</span><span class="sxs-lookup"><span data-stu-id="a5047-113">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="a5047-114">заполняет Возвращаемый буфер хэша.</span><span class="sxs-lookup"><span data-stu-id="a5047-114">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="a5047-115">окне Запрошенный максимальный размер `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="a5047-115">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="a5047-116">заполняет Возвращаемый размер (в байтах) для `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="a5047-116">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5047-117">Требования</span><span class="sxs-lookup"><span data-stu-id="a5047-117">Requirements</span></span>  

 <span data-ttu-id="a5047-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5047-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5047-119">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="a5047-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a5047-120">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5047-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5047-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5047-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5047-122">См. также</span><span class="sxs-lookup"><span data-stu-id="a5047-122">See also</span></span>

- [<span data-ttu-id="a5047-123">Метод GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="a5047-123">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="a5047-124">Метод GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="a5047-124">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="a5047-125">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a5047-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
