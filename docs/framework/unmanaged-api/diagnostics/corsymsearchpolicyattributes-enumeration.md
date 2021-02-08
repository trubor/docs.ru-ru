---
description: Дополнительные сведения о перечислении Корсимсеарчполициаттрибутес
title: Перечисление CorSymSearchPolicyAttributes
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
ms.openlocfilehash: a9af0e96809ec8eba5c03c2e372e818c74914baf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800478"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="a12a6-103">Перечисление CorSymSearchPolicyAttributes</span><span class="sxs-lookup"><span data-stu-id="a12a6-103">CorSymSearchPolicyAttributes Enumeration</span></span>

<span data-ttu-id="a12a6-104">Указывает политику, используемую при поиске средства чтения символов.</span><span class="sxs-lookup"><span data-stu-id="a12a6-104">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="a12a6-105">Эти константы используются методами [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) и [ISymUnmanagedBinder3:: жетреадерфромкаллбакк](isymunmanagedbinder3-getreaderfromcallback-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a12a6-105">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a12a6-106">При открытии файла базы данных программы (PDB) из ненадежного источника возникает угроза безопасности.</span><span class="sxs-lookup"><span data-stu-id="a12a6-106">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a12a6-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a12a6-107">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="a12a6-108">Члены</span><span class="sxs-lookup"><span data-stu-id="a12a6-108">Members</span></span>  
  
|<span data-ttu-id="a12a6-109">Член</span><span class="sxs-lookup"><span data-stu-id="a12a6-109">Member</span></span>|<span data-ttu-id="a12a6-110">Описание</span><span class="sxs-lookup"><span data-stu-id="a12a6-110">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="a12a6-111">Запрашивает пути поиска символов в реестре.</span><span class="sxs-lookup"><span data-stu-id="a12a6-111">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="a12a6-112">Обращается к серверу символов.</span><span class="sxs-lookup"><span data-stu-id="a12a6-112">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="a12a6-113">Выполняет поиск по пути, указанному в каталоге отладки.</span><span class="sxs-lookup"><span data-stu-id="a12a6-113">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="a12a6-114">Выполняет поиск PDB в месте, где находится EXE-файл.</span><span class="sxs-lookup"><span data-stu-id="a12a6-114">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a12a6-115">Требования</span><span class="sxs-lookup"><span data-stu-id="a12a6-115">Requirements</span></span>  

 <span data-ttu-id="a12a6-116">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="a12a6-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a12a6-117">См. также</span><span class="sxs-lookup"><span data-stu-id="a12a6-117">See also</span></span>

- [<span data-ttu-id="a12a6-118">Перечисления хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="a12a6-118">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
