---
description: Дополнительные сведения о перечислении Корсимаддркинд
title: Перечисление CorSymAddrKind
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
ms.openlocfilehash: 94ee9f3da63a33a9f4a80289dbf9b03969d37b3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800504"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="2b2ea-103">Перечисление CorSymAddrKind</span><span class="sxs-lookup"><span data-stu-id="2b2ea-103">CorSymAddrKind Enumeration</span></span>

<span data-ttu-id="2b2ea-104">Указывает тип адреса памяти.</span><span class="sxs-lookup"><span data-stu-id="2b2ea-104">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b2ea-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2b2ea-105">Syntax</span></span>  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a><span data-ttu-id="2b2ea-106">Члены</span><span class="sxs-lookup"><span data-stu-id="2b2ea-106">Members</span></span>  
  
|<span data-ttu-id="2b2ea-107">Член</span><span class="sxs-lookup"><span data-stu-id="2b2ea-107">Member</span></span>|<span data-ttu-id="2b2ea-108">Описание</span><span class="sxs-lookup"><span data-stu-id="2b2ea-108">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="2b2ea-109">Указывает локальную переменную или индекс параметра промежуточного языка MSIL.</span><span class="sxs-lookup"><span data-stu-id="2b2ea-109">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="2b2ea-110">Указывает относительный виртуальный адрес в модуле.</span><span class="sxs-lookup"><span data-stu-id="2b2ea-110">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="2b2ea-111">Указывает регистр ЦП.</span><span class="sxs-lookup"><span data-stu-id="2b2ea-111">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="2b2ea-112">Указывает, что первый адрес является регистром, а второй — смещением.</span><span class="sxs-lookup"><span data-stu-id="2b2ea-112">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="2b2ea-113">Указывает смещение от базового адреса.</span><span class="sxs-lookup"><span data-stu-id="2b2ea-113">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="2b2ea-114">Указывает, что первый адрес является нижней частью регистра, а второй адрес — верхней частью.</span><span class="sxs-lookup"><span data-stu-id="2b2ea-114">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="2b2ea-115">Указывает, что первый адрес является нижней частью регистра, второй — верхней частью, а третья — смещением.</span><span class="sxs-lookup"><span data-stu-id="2b2ea-115">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="2b2ea-116">Указывает, что первый адрес является регистром, второй — смещением, а третье — старшая часть регистра.</span><span class="sxs-lookup"><span data-stu-id="2b2ea-116">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="2b2ea-117">Указывает, что первым адресом является начало поля, а вторым адресом является длина поля.</span><span class="sxs-lookup"><span data-stu-id="2b2ea-117">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="2b2ea-118">Указывает, что первый адрес является разделом, а второй — смещением.</span><span class="sxs-lookup"><span data-stu-id="2b2ea-118">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2b2ea-119">Требования</span><span class="sxs-lookup"><span data-stu-id="2b2ea-119">Requirements</span></span>  

 <span data-ttu-id="2b2ea-120">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="2b2ea-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b2ea-121">См. также</span><span class="sxs-lookup"><span data-stu-id="2b2ea-121">See also</span></span>

- [<span data-ttu-id="2b2ea-122">Перечисления хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="2b2ea-122">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
