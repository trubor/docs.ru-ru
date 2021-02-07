---
description: Дополнительные сведения о методе Сетассемблипропс
title: Метод SetAssemblyProps
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
ms.openlocfilehash: 212d8aad22ac1cb231db46f20ff65de2339a21aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662355"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="d9fc5-103">Метод SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="d9fc5-103">SetAssemblyProps Method</span></span>

<span data-ttu-id="d9fc5-104">Назначает свойства уровня сборки.</span><span class="sxs-lookup"><span data-stu-id="d9fc5-104">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9fc5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9fc5-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9fc5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d9fc5-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="d9fc5-107">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="d9fc5-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d9fc5-108">Файл, определяющий свойство.</span><span class="sxs-lookup"><span data-stu-id="d9fc5-108">File that defines the property.</span></span> <span data-ttu-id="d9fc5-109">Может иметь значение NULL `AssemblyID` , если не указывает на непривязанный netmodule.</span><span class="sxs-lookup"><span data-stu-id="d9fc5-109">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="d9fc5-110">Указывает изменяемый параметр.</span><span class="sxs-lookup"><span data-stu-id="d9fc5-110">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="d9fc5-111">Новое значение параметра.</span><span class="sxs-lookup"><span data-stu-id="d9fc5-111">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9fc5-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d9fc5-112">Return Value</span></span>  

 <span data-ttu-id="d9fc5-113">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="d9fc5-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9fc5-114">Требования</span><span class="sxs-lookup"><span data-stu-id="d9fc5-114">Requirements</span></span>  

 <span data-ttu-id="d9fc5-115">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="d9fc5-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9fc5-116">См. также</span><span class="sxs-lookup"><span data-stu-id="d9fc5-116">See also</span></span>

- [<span data-ttu-id="d9fc5-117">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="d9fc5-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d9fc5-118">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="d9fc5-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d9fc5-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="d9fc5-119">ALink API</span></span>](index.md)
