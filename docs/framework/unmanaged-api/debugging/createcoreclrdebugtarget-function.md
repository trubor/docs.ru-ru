---
description: Дополнительные сведения о функции Креатекореклрдебугтаржет
title: Функция CreateCoreClrDebugTarget
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
ms.openlocfilehash: 30a6af29e6e1a6ee2c827049a3c792f2d663a702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661580"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="ddbae-103">Функция CreateCoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="ddbae-103">CreateCoreClrDebugTarget Function</span></span>

<span data-ttu-id="ddbae-104">Создает подключение к прокси-серверу отладчика, запущенному на удаленном компьютере, и возвращает объект [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) , который можно использовать для запроса выполняющихся процессов и загрузки сред выполнения на удаленном компьютере.</span><span class="sxs-lookup"><span data-stu-id="ddbae-104">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddbae-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ddbae-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddbae-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ddbae-106">Parameters</span></span>  

 `dwAddress`  
 <span data-ttu-id="ddbae-107">[in] IPv4-адрес удаленного целевого компьютера.</span><span class="sxs-lookup"><span data-stu-id="ddbae-107">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="ddbae-108">заполняет Указатель на указатель на объект [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) , который будет создан.</span><span class="sxs-lookup"><span data-stu-id="ddbae-108">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddbae-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ddbae-109">Return Value</span></span>  

 <span data-ttu-id="ddbae-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ddbae-110">S_OK</span></span>  
 <span data-ttu-id="ddbae-111">Количество сред CLR в процессе успешно определено, и соответствующие массивы дескрипторов и путей заполнены должным образом.</span><span class="sxs-lookup"><span data-stu-id="ddbae-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="ddbae-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ddbae-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="ddbae-113">Не удается выделить достаточно памяти для `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="ddbae-113">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="ddbae-114">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="ddbae-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ddbae-115">Прочие сбои.</span><span class="sxs-lookup"><span data-stu-id="ddbae-115">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddbae-116">Требования</span><span class="sxs-lookup"><span data-stu-id="ddbae-116">Requirements</span></span>  

 <span data-ttu-id="ddbae-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddbae-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddbae-118">**Заголовок:** Кореклрремотедебуггингинтерфацес. h</span><span class="sxs-lookup"><span data-stu-id="ddbae-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="ddbae-119">**Библиотека:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="ddbae-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="ddbae-120">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="ddbae-120">**.NET Framework Versions:** 3.5 SP1</span></span>
