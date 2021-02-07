---
description: 'Дополнительные сведения о методе: ICorDebugFunction2:: Енумератенативекоде'
title: Метод ICorDebugFunction2::EnumerateNativeCode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.EnumerateNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::EnumerateNativeCode
helpviewer_keywords:
- ICorDebugFunction2::EnumerateNativeCode method [.NET Framework debugging]
- EnumerateNativeCode method [.NET Framework debugging]
ms.assetid: d383f5cc-1144-4b6d-b57a-db34d9134ab2
topic_type:
- apiref
ms.openlocfilehash: 617d6dbfdb596df192e2722a47d81517ae57ac1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692255"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="11fa3-103">Метод ICorDebugFunction2::EnumerateNativeCode</span><span class="sxs-lookup"><span data-stu-id="11fa3-103">ICorDebugFunction2::EnumerateNativeCode Method</span></span>

<span data-ttu-id="11fa3-104">Возвращает указатель интерфейса на объект Икордебугкодинум, содержащий операторы машинного кода в функции, на которую ссылается этот объект ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="11fa3-104">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11fa3-105">`EnumerateNativeCode` не реализован в текущей версии платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11fa3-105">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11fa3-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="11fa3-106">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="11fa3-107">Требования</span><span class="sxs-lookup"><span data-stu-id="11fa3-107">Requirements</span></span>  

 <span data-ttu-id="11fa3-108">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11fa3-108">**Header:** CorDebug.idl, CorDebug.h</span></span>
