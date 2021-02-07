---
description: Дополнительные сведения о функции _CorDllMain
title: Функция _CorDllMain
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
ms.openlocfilehash: 442afae3a627eb684a86c02fbc6e546aa804b7a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717155"
---
# <a name="_cordllmain-function"></a><span data-ttu-id="a09dd-103">\_Функция Кордллмаин</span><span class="sxs-lookup"><span data-stu-id="a09dd-103">\_CorDllMain Function</span></span>

<span data-ttu-id="a09dd-104">Инициализирует среду CLR, находит управляемую точку входа в заголовке CLR сборки DLL и начинает выполнение.</span><span class="sxs-lookup"><span data-stu-id="a09dd-104">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a09dd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a09dd-105">Syntax</span></span>  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a09dd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a09dd-106">Parameters</span></span>  

 `hInst`  
 <span data-ttu-id="a09dd-107">окне Экземпляр загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="a09dd-107">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="a09dd-108">окне Указывает, почему вызывается функция точки входа DLL.</span><span class="sxs-lookup"><span data-stu-id="a09dd-108">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="a09dd-109">Этот параметр может принимать одно из следующих значений: DLL \_ PROCESS_ATTACH, присоединение потока DLL, присоединение \_ потока DLL \_ \_ \_ или \_ Отключение процесса DLL \_ .</span><span class="sxs-lookup"><span data-stu-id="a09dd-109">This parameter can be one of the following values: DLL\_PROCESS_ATTACH, DLL\_THREAD\_ATTACH, DLL\_THREAD\_ATTACH, or DLL\_PROCESS\_DETACH.</span></span> <span data-ttu-id="a09dd-110">Описание этих значений см. в документации по `DllMain` Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="a09dd-110">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="a09dd-111">[in] Не используется.</span><span class="sxs-lookup"><span data-stu-id="a09dd-111">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a09dd-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a09dd-112">Return Value</span></span>  

 <span data-ttu-id="a09dd-113">Этот метод возвращает значение `true` для успешного выполнения и `false` при возникновении ошибки.</span><span class="sxs-lookup"><span data-stu-id="a09dd-113">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a09dd-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="a09dd-114">Remarks</span></span>  

 <span data-ttu-id="a09dd-115">Эта функция вызывается загрузчиком операционной системы для сборок DLL.</span><span class="sxs-lookup"><span data-stu-id="a09dd-115">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="a09dd-116">Для исполняемых сборок загрузчик вызывает функцию [ \_ корексемаин](corexemain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="a09dd-116">For executable assemblies, the loader calls the [\_CorExeMain](corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="a09dd-117">Загрузчик операционной системы вызывает этот метод независимо от точки входа, указанной в файле DLL.</span><span class="sxs-lookup"><span data-stu-id="a09dd-117">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
<span data-ttu-id="a09dd-118">`_CorDllMain`Функция вызывается непосредственно загрузчиком операционной системы.</span><span class="sxs-lookup"><span data-stu-id="a09dd-118">The `_CorDllMain` function is called directly by the operating system loader.</span></span>
  
 <span data-ttu-id="a09dd-119">Дополнительные сведения см. в подразделе "Примечания" раздела [ \_ корвалидатеимаже](corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="a09dd-119">For additional information, see the Remarks section in the [\_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a09dd-120">Требования</span><span class="sxs-lookup"><span data-stu-id="a09dd-120">Requirements</span></span>  

 <span data-ttu-id="a09dd-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a09dd-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a09dd-122">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a09dd-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a09dd-123">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a09dd-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a09dd-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a09dd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09dd-125">См. также</span><span class="sxs-lookup"><span data-stu-id="a09dd-125">See also</span></span>

- [<span data-ttu-id="a09dd-126">Глобальные статические функции метаданных</span><span class="sxs-lookup"><span data-stu-id="a09dd-126">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
