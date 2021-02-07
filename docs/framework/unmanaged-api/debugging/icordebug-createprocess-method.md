---
description: 'Дополнительные сведения: метод ICorDebug:: CreateProcess'
title: Метод ICorDebug::CreateProcess
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
ms.openlocfilehash: b504b5f7a60fd0fd4a8f8f1c5d8e3c3b8dcfd858
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712120"
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="1ad3c-103">Метод ICorDebug::CreateProcess</span><span class="sxs-lookup"><span data-stu-id="1ad3c-103">ICorDebug::CreateProcess Method</span></span>

<span data-ttu-id="1ad3c-104">Запускает процесс и его основной поток под управлением отладчика.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-104">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ad3c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1ad3c-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ad3c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ad3c-106">Parameters</span></span>  

 `lpApplicationName`  
 <span data-ttu-id="1ad3c-107">окне Указатель на строку, завершающуюся нулем, которая указывает модуль, выполняемый запущенным процессом.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-107">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="1ad3c-108">Модуль выполняется в контексте безопасности вызывающего процесса.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-108">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="1ad3c-109">окне Указатель на строку, завершающуюся нулем, которая указывает командную строку, выполняемую запущенным процессом.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-109">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="1ad3c-110">Имя приложения (например, "SomeApp.exe") должно быть первым аргументом.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-110">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="1ad3c-111">окне Указатель на структуру Win32 `SECURITY_ATTRIBUTES` , указывающую дескриптор безопасности для процесса.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-111">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="1ad3c-112">Если значение `lpProcessAttributes` равно null, процесс получает дескриптор безопасности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-112">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="1ad3c-113">окне Указатель на структуру Win32 `SECURITY_ATTRIBUTES` , указывающую дескриптор безопасности для основного потока процесса.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-113">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="1ad3c-114">Если значение `lpThreadAttributes` равно null, то поток получает дескриптор безопасности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-114">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="1ad3c-115">окне Задайте значение, `true` чтобы указать, что каждый наследуемый дескриптор в вызывающем процессе наследуется запущенным процессом, или `false` чтобы указать, что дескрипторы не наследуются.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-115">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="1ad3c-116">Унаследованные дескрипторы имеют те же значения и права доступа, что и исходные дескрипторы.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-116">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="1ad3c-117">окне Побитовое сочетание [флагов создания процесса Win32](/windows/win32/procthread/process-creation-flags) , управляющих классом приоритета и поведением запущенного процесса.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-117">[in] A bitwise combination of the [Win32 Process Creation Flags](/windows/win32/procthread/process-creation-flags) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="1ad3c-118">окне Указатель на блок среды для нового процесса.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-118">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="1ad3c-119">окне Указатель на строку, завершающуюся нулем, которая указывает полный путь к текущему каталогу для процесса.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-119">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="1ad3c-120">Если этот параметр имеет значение null, то новый процесс будет иметь тот же текущий диск и каталог, что и вызывающий процесс.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-120">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="1ad3c-121">окне Указатель на структуру Win32 `STARTUPINFOW` , указывающую станцию окон, Рабочий стол, стандартные маркеры и внешний вид главного окна для запущенного процесса.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-121">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="1ad3c-122">окне Указатель на структуру Win32 `PROCESS_INFORMATION` , указывающую идентификационную информацию о процессе, который необходимо запустить.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-122">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="1ad3c-123">окне Значение перечисления Кордебугкреатепроцессфлагс, определяющее параметры отладки.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-123">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="1ad3c-124">заполняет Указатель на адрес объекта ICorDebugProcess, который представляет процесс.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-124">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ad3c-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="1ad3c-125">Remarks</span></span>  

 <span data-ttu-id="1ad3c-126">Параметры этого метода совпадают с параметрами `CreateProcess` метода Win32.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-126">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="1ad3c-127">Чтобы включить неуправляемую отладку в смешанном режиме, задайте для параметра значение `dwCreationFlags` DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-127">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="1ad3c-128">Если вы хотите использовать только управляемую отладку, не устанавливайте эти флаги.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-128">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="1ad3c-129">Если отладчик и отлаживаемый процесс (присоединенный процесс) совместно используют одну консоль, и если используется отладка взаимодействия, то присоединенный процесс может содержать блокировки консоли и останавливать при отладке события.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-129">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="1ad3c-130">Отладчик будет блокировать любые попытки использования консоли.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-130">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="1ad3c-131">Чтобы избежать этой проблемы, установите флаг CREATE_NEW_CONSOLE в `dwCreationFlags` параметре.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-131">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="1ad3c-132">Отладка взаимодействия не поддерживается на платформах Win9x и на платформе, отличной от x86, например на платформах на основе IA-64 и AMD64.</span><span class="sxs-lookup"><span data-stu-id="1ad3c-132">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ad3c-133">Требования</span><span class="sxs-lookup"><span data-stu-id="1ad3c-133">Requirements</span></span>  

 <span data-ttu-id="1ad3c-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ad3c-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ad3c-135">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ad3c-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ad3c-136">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ad3c-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ad3c-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ad3c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad3c-138">См. также</span><span class="sxs-lookup"><span data-stu-id="1ad3c-138">See also</span></span>

- [<span data-ttu-id="1ad3c-139">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="1ad3c-139">ICorDebug Interface</span></span>](icordebug-interface.md)
