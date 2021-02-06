---
description: Дополнительные сведения о методе Експортнестедтипефорвардер
title: Метод ExportNestedTypeForwarder
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
ms.openlocfilehash: fd791e3fea76338f191fcf924d56720d257d2e8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638110"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="54b8c-103">Метод ExportNestedTypeForwarder</span><span class="sxs-lookup"><span data-stu-id="54b8c-103">ExportNestedTypeForwarder Method</span></span>

<span data-ttu-id="54b8c-104">Добавляет сервер пересылки типа для вложенного типа в таблицу типов данной сборки.</span><span class="sxs-lookup"><span data-stu-id="54b8c-104">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54b8c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="54b8c-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="54b8c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="54b8c-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="54b8c-107">Идентификатор сборки, из которой необходимо выполнить экспорт.</span><span class="sxs-lookup"><span data-stu-id="54b8c-107">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="54b8c-108">Маркер файла или идентификатор сборки файла, который определяет тип.</span><span class="sxs-lookup"><span data-stu-id="54b8c-108">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="54b8c-109">Токен для типа.</span><span class="sxs-lookup"><span data-stu-id="54b8c-109">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="54b8c-110">Токен родительского типа.</span><span class="sxs-lookup"><span data-stu-id="54b8c-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="54b8c-111">Полное имя типа для экспорта.</span><span class="sxs-lookup"><span data-stu-id="54b8c-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="54b8c-112">`ComType` Флаги, такие как `tdPublic` или `tdNested` .</span><span class="sxs-lookup"><span data-stu-id="54b8c-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="54b8c-113">Получает маркер типа экспорта.</span><span class="sxs-lookup"><span data-stu-id="54b8c-113">Receives token of export type.</span></span> <span data-ttu-id="54b8c-114">Это необходимо только для выпуска вложенных типов.</span><span class="sxs-lookup"><span data-stu-id="54b8c-114">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54b8c-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="54b8c-115">Return Value</span></span>  

 <span data-ttu-id="54b8c-116">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="54b8c-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54b8c-117">Требования</span><span class="sxs-lookup"><span data-stu-id="54b8c-117">Requirements</span></span>  

 <span data-ttu-id="54b8c-118">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="54b8c-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54b8c-119">См. также</span><span class="sxs-lookup"><span data-stu-id="54b8c-119">See also</span></span>

- [<span data-ttu-id="54b8c-120">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="54b8c-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="54b8c-121">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="54b8c-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="54b8c-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="54b8c-122">ALink API</span></span>](index.md)
