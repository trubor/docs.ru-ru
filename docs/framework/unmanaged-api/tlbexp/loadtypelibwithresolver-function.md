---
description: Дополнительные сведения о функции LoadTypeLibWithResolver
title: Функция LoadTypeLibWithResolver
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
ms.openlocfilehash: 6747199364a549d922ad73bfac3e93b329d1172a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646222"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="01b87-103">Функция LoadTypeLibWithResolver</span><span class="sxs-lookup"><span data-stu-id="01b87-103">LoadTypeLibWithResolver Function</span></span>

<span data-ttu-id="01b87-104">Загружает библиотеку типов и использует предоставляемый [интерфейс итипелибресолвер](itypelibresolver-interface.md) для разрешения любых библиотек типов, на которые имеются ссылки.</span><span class="sxs-lookup"><span data-stu-id="01b87-104">Loads a type library and uses the supplied [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01b87-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="01b87-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01b87-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="01b87-106">Parameters</span></span>  

 `szFile`  
 <span data-ttu-id="01b87-107">окне Путь к файлу библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="01b87-107">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="01b87-108">окне Флаг [перечисления регкинд](/windows/win32/api/oleauto/ne-oleauto-regkind) , управляющий регистрацией библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="01b87-108">[in] A [REGKIND enumeration](/windows/win32/api/oleauto/ne-oleauto-regkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="01b87-109">Возможные значения:</span><span class="sxs-lookup"><span data-stu-id="01b87-109">Its possible values are:</span></span>  
  
- <span data-ttu-id="01b87-110">`REGKIND_DEFAULT`: Использовать поведение регистрации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="01b87-110">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
- <span data-ttu-id="01b87-111">`REGKIND_REGISTER`: Зарегистрируйте эту библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="01b87-111">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
- <span data-ttu-id="01b87-112">`REGKIND_NONE`: Не регистрировать эту библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="01b87-112">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="01b87-113">окне Указатель на реализацию [интерфейса итипелибресолвер](itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="01b87-113">[in] A pointer to the implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="01b87-114">заполняет Ссылка на загружаемую библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="01b87-114">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01b87-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="01b87-115">Return Value</span></span>  

 <span data-ttu-id="01b87-116">Одно из значений HRESULT, перечисленных в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="01b87-116">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="01b87-117">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="01b87-117">Return value</span></span>|<span data-ttu-id="01b87-118">Значение</span><span class="sxs-lookup"><span data-stu-id="01b87-118">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="01b87-119">Успешно.</span><span class="sxs-lookup"><span data-stu-id="01b87-119">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="01b87-120">Недостаточно памяти.</span><span class="sxs-lookup"><span data-stu-id="01b87-120">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="01b87-121">Один или несколько указателей являются недопустимыми.</span><span class="sxs-lookup"><span data-stu-id="01b87-121">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="01b87-122">Один или несколько аргументов являются недопустимыми.</span><span class="sxs-lookup"><span data-stu-id="01b87-122">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="01b87-123">Функции не удалось выполнить запись в файл.</span><span class="sxs-lookup"><span data-stu-id="01b87-123">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="01b87-124">Не удалось открыть базу данных регистрации системы.</span><span class="sxs-lookup"><span data-stu-id="01b87-124">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="01b87-125">Не удалось открыть библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="01b87-125">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="01b87-126">Не удалось загрузить библиотеку типов или библиотеку DLL.</span><span class="sxs-lookup"><span data-stu-id="01b87-126">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01b87-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="01b87-127">Remarks</span></span>  

 <span data-ttu-id="01b87-128">[Tlbexp.exe (программа экспорта библиотек типов)](../../tools/tlbexp-exe-type-library-exporter.md) вызывает `LoadTypeLibWithResolver` функцию во время преобразования сборки в библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="01b87-128">The [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="01b87-129">Эта функция загружает указанную библиотеку типов с минимальным доступом к реестру.</span><span class="sxs-lookup"><span data-stu-id="01b87-129">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="01b87-130">Затем функция проверяет библиотеку типов для внутренних ссылочных библиотек типов, каждая из которых должна быть загружена и добавлена в родительскую библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="01b87-130">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="01b87-131">Прежде чем можно будет загрузить библиотеку типов, на которую указывает ссылка, путь к файлу ссылки должен быть разрешаться в полный путь к файлу.</span><span class="sxs-lookup"><span data-stu-id="01b87-131">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="01b87-132">Это осуществляется с помощью [метода ресолветипелиб](resolvetypelib-method.md) , предоставляемого [интерфейсом итипелибресолвер](itypelibresolver-interface.md), который передается в `pTlbResolver` параметре.</span><span class="sxs-lookup"><span data-stu-id="01b87-132">This is accomplished through the [ResolveTypeLib method](resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="01b87-133">Если известен полный путь к файлу библиотеки типов, на которую указывает ссылка, `LoadTypeLibWithResolver` функция загружает и добавляет библиотеку типов, на которую указывает ссылка, в родительскую библиотеку типов, создавая объединенную библиотеку типов Master.</span><span class="sxs-lookup"><span data-stu-id="01b87-133">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="01b87-134">После того как функция разрешает и загружает все библиотеки типов, на которые имеются ссылки, она возвращает ссылку на библиотеку разрешенных шаблонов в `pptlib` параметре.</span><span class="sxs-lookup"><span data-stu-id="01b87-134">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="01b87-135">`LoadTypeLibWithResolver`Функция обычно вызывается [Tlbexp.exe (программа экспорта библиотек типов)](../../tools/tlbexp-exe-type-library-exporter.md), которая предоставляет собственную реализацию внутреннего [интерфейса итипелибресолвер](itypelibresolver-interface.md) в `pTlbResolver` параметре.</span><span class="sxs-lookup"><span data-stu-id="01b87-135">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="01b87-136">При вызове `LoadTypeLibWithResolver` напрямую необходимо предоставить собственную реализацию [интерфейса итипелибресолвер](itypelibresolver-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="01b87-136">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01b87-137">Требования</span><span class="sxs-lookup"><span data-stu-id="01b87-137">Requirements</span></span>  

 <span data-ttu-id="01b87-138">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01b87-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01b87-139">**Заголовок:** Тлбреф. h</span><span class="sxs-lookup"><span data-stu-id="01b87-139">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="01b87-140">**Библиотека:** Тлбреф. lib</span><span class="sxs-lookup"><span data-stu-id="01b87-140">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="01b87-141">**Версия платформа .NET Framework:** 3,5, 3,0, 2,0</span><span class="sxs-lookup"><span data-stu-id="01b87-141">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b87-142">См. также</span><span class="sxs-lookup"><span data-stu-id="01b87-142">See also</span></span>

- [<span data-ttu-id="01b87-143">Вспомогательные функции Tlbexp</span><span class="sxs-lookup"><span data-stu-id="01b87-143">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="01b87-144">Функция Лоадтипелибекс</span><span class="sxs-lookup"><span data-stu-id="01b87-144">LoadTypeLibEx Function</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
