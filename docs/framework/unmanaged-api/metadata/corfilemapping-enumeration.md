---
description: Дополнительные сведения о перечислении CorFileMapping
title: Перечисление CorFileMapping
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 0fc3916e75c576a6b133ba8a49c00eec6c9bac19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784474"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="b026d-103">Перечисление CorFileMapping</span><span class="sxs-lookup"><span data-stu-id="b026d-103">CorFileMapping Enumeration</span></span>

<span data-ttu-id="b026d-104">Содержит значения, описывающие тип сопоставления файлов, возвращаемого при вызове метода [иметадатаинфо:: GetFileMapping](imetadatainfo-getfilemapping-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b026d-104">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b026d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b026d-105">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="b026d-106">Члены</span><span class="sxs-lookup"><span data-stu-id="b026d-106">Members</span></span>  
  
|<span data-ttu-id="b026d-107">Член</span><span class="sxs-lookup"><span data-stu-id="b026d-107">Member</span></span>|<span data-ttu-id="b026d-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b026d-108">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="b026d-109">Файл сопоставляется как файл данных.</span><span class="sxs-lookup"><span data-stu-id="b026d-109">The file is mapped as a data file.</span></span> <span data-ttu-id="b026d-110">То есть `SEC_IMAGE` флаг не был передан функции Microsoft Win32 `CreateFileMapping` .</span><span class="sxs-lookup"><span data-stu-id="b026d-110">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="b026d-111">Файл сопоставляется для выполнения с помощью `LoadLibrary` функции или `CreateFileMapping` функции с `SEC_IMAGE` флагом.</span><span class="sxs-lookup"><span data-stu-id="b026d-111">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b026d-112">Требования</span><span class="sxs-lookup"><span data-stu-id="b026d-112">Requirements</span></span>  

 <span data-ttu-id="b026d-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b026d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b026d-114">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="b026d-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b026d-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b026d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b026d-116">См. также</span><span class="sxs-lookup"><span data-stu-id="b026d-116">See also</span></span>

- [<span data-ttu-id="b026d-117">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="b026d-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="b026d-118">Метод GetFileMapping</span><span class="sxs-lookup"><span data-stu-id="b026d-118">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)
