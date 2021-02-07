---
description: Дополнительные сведения о методе Сетпекинд
title: Метод SetPEKind
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: 4154e9e80b7f88b6951c9aa8da5fc23d340c96dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662303"
---
# <a name="setpekind-method"></a><span data-ttu-id="476cf-103">Метод SetPEKind</span><span class="sxs-lookup"><span data-stu-id="476cf-103">SetPEKind Method</span></span>

<span data-ttu-id="476cf-104">Определяет тип переносимого исполняемого файла, который зависит от компьютера или компьютера.</span><span class="sxs-lookup"><span data-stu-id="476cf-104">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="476cf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="476cf-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="476cf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="476cf-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="476cf-107">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="476cf-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="476cf-108">Токен файла, для которого задается тип PE.</span><span class="sxs-lookup"><span data-stu-id="476cf-108">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="476cf-109">Может иметь значение NULL `AssemblyID` , если не указывает на непривязанный netmodule.</span><span class="sxs-lookup"><span data-stu-id="476cf-109">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="476cf-110">Тип PE, как указано в [перечислении CorPEKind](../metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="476cf-110">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="476cf-111">Архитектура целевого компьютера, как указано в заголовке NT.</span><span class="sxs-lookup"><span data-stu-id="476cf-111">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="476cf-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="476cf-112">Return Value</span></span>  

 <span data-ttu-id="476cf-113">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="476cf-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="476cf-114">Требования</span><span class="sxs-lookup"><span data-stu-id="476cf-114">Requirements</span></span>  

 <span data-ttu-id="476cf-115">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="476cf-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="476cf-116">См. также</span><span class="sxs-lookup"><span data-stu-id="476cf-116">See also</span></span>

- [<span data-ttu-id="476cf-117">Метод GetPEKind</span><span class="sxs-lookup"><span data-stu-id="476cf-117">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="476cf-118">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="476cf-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="476cf-119">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="476cf-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="476cf-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="476cf-120">ALink API</span></span>](index.md)
