---
description: Дополнительные сведения о функции GetHashFromAssemblyFile
title: Функция GetHashFromAssemblyFile
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
ms.openlocfilehash: 79cc6289ebcf33f5a9ea8b4ef139c4b2a67e55e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736782"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="2760d-103">Функция GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="2760d-103">GetHashFromAssemblyFile Function</span></span>

<span data-ttu-id="2760d-104">Получает хэш указанного файла сборки с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="2760d-104">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="2760d-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="2760d-105">This function has been deprecated.</span></span> <span data-ttu-id="2760d-106">Используйте вместо этого метод [метод iclrstrongname:: GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2760d-106">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2760d-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2760d-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2760d-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="2760d-108">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="2760d-109">окне Путь к файлу для хэширования.</span><span class="sxs-lookup"><span data-stu-id="2760d-109">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2760d-110">[вход, выход] Константа, указывающая хэш-алгоритм.</span><span class="sxs-lookup"><span data-stu-id="2760d-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="2760d-111">Для алгоритма хэширования по умолчанию используется нуль.</span><span class="sxs-lookup"><span data-stu-id="2760d-111">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2760d-112">заполняет Возвращаемый буфер хэша.</span><span class="sxs-lookup"><span data-stu-id="2760d-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2760d-113">окне Запрошенный максимальный размер `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="2760d-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2760d-114">заполняет Возвращаемый размер (в байтах) для `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="2760d-114">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2760d-115">Требования</span><span class="sxs-lookup"><span data-stu-id="2760d-115">Requirements</span></span>  

 <span data-ttu-id="2760d-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2760d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2760d-117">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="2760d-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2760d-118">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2760d-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2760d-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2760d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2760d-120">См. также</span><span class="sxs-lookup"><span data-stu-id="2760d-120">See also</span></span>

- [<span data-ttu-id="2760d-121">Метод GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="2760d-121">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="2760d-122">Метод GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="2760d-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="2760d-123">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="2760d-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
