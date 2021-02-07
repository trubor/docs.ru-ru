---
description: Дополнительные сведения о функции Лоадлибраришим
title: Функция LoadLibraryShim
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
ms.openlocfilehash: 829d64b5215fc21b2d8c8b753f5ad99212267b6a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680009"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="9e26f-103">Функция LoadLibraryShim</span><span class="sxs-lookup"><span data-stu-id="9e26f-103">LoadLibraryShim Function</span></span>

<span data-ttu-id="9e26f-104">Загружает указанную версию библиотеки DLL, которая входит в состав распространяемого пакета платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e26f-104">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="9e26f-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9e26f-105">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="9e26f-106">Используйте вместо этого метод [ICLRRuntimeInfo:: LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9e26f-106">Use the [ICLRRuntimeInfo::LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e26f-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9e26f-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e26f-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="9e26f-108">Parameters</span></span>  

 `szDllName`  
 <span data-ttu-id="9e26f-109">окне Строка, завершающаяся нулем, которая представляет имя библиотеки DLL, загружаемой из библиотеки платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e26f-109">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="9e26f-110">окне Строка, заканчивающаяся нулем и представляющая версию загружаемой библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="9e26f-110">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="9e26f-111">Если `szVersion` параметр имеет значение null, версия, выбранная для загрузки, является последней версией указанной библиотеки DLL, которая меньше версии 4.</span><span class="sxs-lookup"><span data-stu-id="9e26f-111">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="9e26f-112">То есть все версии, равные или больше версии 4, игнорируются `szVersion` , если имеет значение null, и если не установлена версия, отличная от версии 4, то не удается загрузить библиотеку DLL.</span><span class="sxs-lookup"><span data-stu-id="9e26f-112">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="9e26f-113">Это необходимо для того, чтобы установка платформа .NET Framework 4 не влияла на существующие приложения или компоненты.</span><span class="sxs-lookup"><span data-stu-id="9e26f-113">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="9e26f-114">См. запись [In-Proc SxS и Migration быстрое начало](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) в блоге команды разработчиков CLR.</span><span class="sxs-lookup"><span data-stu-id="9e26f-114">See the entry [In-Proc SxS and Migration Quick Start](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="9e26f-115">Зарезервировано для будущего использования.</span><span class="sxs-lookup"><span data-stu-id="9e26f-115">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="9e26f-116">заполняет Указатель на маркер модуля.</span><span class="sxs-lookup"><span data-stu-id="9e26f-116">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e26f-117">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9e26f-117">Return Value</span></span>  

 <span data-ttu-id="9e26f-118">Этот метод возвращает коды стандартных ошибок модели COM, как определено в файле WinError. h, в дополнение к следующим значениям.</span><span class="sxs-lookup"><span data-stu-id="9e26f-118">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="9e26f-119">Код возврата</span><span class="sxs-lookup"><span data-stu-id="9e26f-119">Return code</span></span>|<span data-ttu-id="9e26f-120">Описание</span><span class="sxs-lookup"><span data-stu-id="9e26f-120">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9e26f-121">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e26f-121">S_OK</span></span>|<span data-ttu-id="9e26f-122">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="9e26f-122">The method completed successfully.</span></span>|  
|<span data-ttu-id="9e26f-123">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="9e26f-123">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="9e26f-124">`szDllName`Для загрузки требуется загрузка среды CLR, и необходимая версия CLR не может быть загружена.</span><span class="sxs-lookup"><span data-stu-id="9e26f-124">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e26f-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="9e26f-125">Remarks</span></span>  

 <span data-ttu-id="9e26f-126">Эта функция используется для загрузки библиотек DLL, включенных в распространяемый пакет платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e26f-126">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="9e26f-127">Он не загружает создаваемые пользователем библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="9e26f-127">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e26f-128">Начиная с версии платформа .NET Framework 2,0, Загрузка Fusion.dll приводит к загрузке среды CLR.</span><span class="sxs-lookup"><span data-stu-id="9e26f-128">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="9e26f-129">Это обусловлено тем, что функции в Fusion.dll теперь являются оболочками, реализации которых предоставляются средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="9e26f-129">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e26f-130">Требования</span><span class="sxs-lookup"><span data-stu-id="9e26f-130">Requirements</span></span>  

 <span data-ttu-id="9e26f-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e26f-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e26f-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9e26f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e26f-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e26f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e26f-134">См. также</span><span class="sxs-lookup"><span data-stu-id="9e26f-134">See also</span></span>

- [<span data-ttu-id="9e26f-135">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="9e26f-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
