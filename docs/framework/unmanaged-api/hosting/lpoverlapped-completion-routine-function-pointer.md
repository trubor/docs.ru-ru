---
description: 'Дополнительные сведения: указатель функции LPOVERLAPPED_COMPLETION_ROUTINE'
title: Указатель функции LPOVERLAPPED_COMPLETION_ROUTINE
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
ms.openlocfilehash: 6645e6a9746404a4ae355a22cf16e6d164c63bed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679840"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a><span data-ttu-id="db5b8-103">Указатель функции LPOVERLAPPED_COMPLETION_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="db5b8-103">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>

<span data-ttu-id="db5b8-104">Указывает на функцию, которая уведомляет узел при завершении перекрытия (асинхронного) ввода-вывода на устройство.</span><span class="sxs-lookup"><span data-stu-id="db5b8-104">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="db5b8-105">Этот указатель функции является устаревшим в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="db5b8-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db5b8-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="db5b8-106">Syntax</span></span>  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db5b8-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="db5b8-107">Parameters</span></span>  

 `dwErrorCode`  
 <span data-ttu-id="db5b8-108">окне Значение, которое является кодом ошибки, если устройство было закрыто; в противном случае это значение равно нулю.</span><span class="sxs-lookup"><span data-stu-id="db5b8-108">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="db5b8-109">Закрытие устройства приводит к немедленному завершению операций ввода-вывода на устройстве.</span><span class="sxs-lookup"><span data-stu-id="db5b8-109">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="db5b8-110">окне Число байтов, передаваемых операцией ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="db5b8-110">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="db5b8-111">окне Указатель на структуру, содержащую сведения, используемые для завершения запроса ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="db5b8-111">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db5b8-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="db5b8-112">Remarks</span></span>  

 <span data-ttu-id="db5b8-113">Функция, к которой `LPOVERLAPPED_COMPLETION_ROUTINE` points является функцией обратного вызова и должна быть реализована модулем записи размещающего приложения.</span><span class="sxs-lookup"><span data-stu-id="db5b8-113">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="db5b8-114">Функция обратного вызова позволяет узлу обработать завершенный запрос ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="db5b8-114">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db5b8-115">Требования</span><span class="sxs-lookup"><span data-stu-id="db5b8-115">Requirements</span></span>  

 <span data-ttu-id="db5b8-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db5b8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db5b8-117">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="db5b8-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db5b8-118">**Библиотека:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="db5b8-118">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="db5b8-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db5b8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db5b8-120">См. также</span><span class="sxs-lookup"><span data-stu-id="db5b8-120">See also</span></span>

- [<span data-ttu-id="db5b8-121">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="db5b8-121">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
