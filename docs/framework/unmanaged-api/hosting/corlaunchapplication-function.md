---
description: Дополнительные сведения о функции Корлаунчаппликатион
title: Функция CorLaunchApplication
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
ms.openlocfilehash: 89f1f37ddde69fb5ecc24fd9dfd0d0c27d5fac40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716956"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="621b5-103">Функция CorLaunchApplication</span><span class="sxs-lookup"><span data-stu-id="621b5-103">CorLaunchApplication Function</span></span>

<span data-ttu-id="621b5-104">Запускает приложение по указанному сетевому пути, используя указанные манифесты и другие данные приложения.</span><span class="sxs-lookup"><span data-stu-id="621b5-104">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="621b5-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="621b5-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="621b5-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="621b5-106">Syntax</span></span>  
  
```cpp  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="621b5-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="621b5-107">Parameters</span></span>  

 `dwClickOnceHost`  
 <span data-ttu-id="621b5-108">окне Значение перечисления [HOST_TYPE](host-type-enumeration.md) , указывающее тип узла, запускающего приложение.</span><span class="sxs-lookup"><span data-stu-id="621b5-108">[in] A value of the [HOST_TYPE](host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="621b5-109">окне Полное имя запускаемого приложения.</span><span class="sxs-lookup"><span data-stu-id="621b5-109">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="621b5-110">окне Число путей манифеста для приложения.</span><span class="sxs-lookup"><span data-stu-id="621b5-110">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="621b5-111">окне Массив строк, каждый из которых указывает путь к манифесту запускаемого приложения.</span><span class="sxs-lookup"><span data-stu-id="621b5-111">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="621b5-112">окне Количество элементов данных активации для запускаемого приложения.</span><span class="sxs-lookup"><span data-stu-id="621b5-112">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="621b5-113">окне Массив строк, каждый из которых является элементом данных активации для запускаемого приложения.</span><span class="sxs-lookup"><span data-stu-id="621b5-113">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="621b5-114">заполняет Указатель на сведения о процессе, в котором было загружено приложение.</span><span class="sxs-lookup"><span data-stu-id="621b5-114">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="621b5-115">Требования</span><span class="sxs-lookup"><span data-stu-id="621b5-115">Requirements</span></span>  

 <span data-ttu-id="621b5-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="621b5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="621b5-117">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="621b5-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="621b5-118">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="621b5-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="621b5-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="621b5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="621b5-120">См. также</span><span class="sxs-lookup"><span data-stu-id="621b5-120">See also</span></span>

- [<span data-ttu-id="621b5-121">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="621b5-121">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
