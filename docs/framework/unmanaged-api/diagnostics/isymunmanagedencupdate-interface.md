---
description: 'Дополнительные сведения о: интерфейс ISymUnmanagedENCUpdate'
title: Интерфейс ISymUnmanagedENCUpdate
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
ms.openlocfilehash: 4527dfbba840be00cf87a80cdcef3cbde6f275df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721428"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="19b05-103">Интерфейс ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="19b05-103">ISymUnmanagedENCUpdate Interface</span></span>

<span data-ttu-id="19b05-104">Предоставляет функции для функции "изменить и продолжить".</span><span class="sxs-lookup"><span data-stu-id="19b05-104">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19b05-105">Методы</span><span class="sxs-lookup"><span data-stu-id="19b05-105">Methods</span></span>  
  
|<span data-ttu-id="19b05-106">Метод</span><span class="sxs-lookup"><span data-stu-id="19b05-106">Method</span></span>|<span data-ttu-id="19b05-107">Описание</span><span class="sxs-lookup"><span data-stu-id="19b05-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19b05-108">Метод GetLocalVariableCount</span><span class="sxs-lookup"><span data-stu-id="19b05-108">GetLocalVariableCount Method</span></span>](isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="19b05-109">Возвращает число локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="19b05-109">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="19b05-110">Метод GetLocalVariables</span><span class="sxs-lookup"><span data-stu-id="19b05-110">GetLocalVariables Method</span></span>](isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="19b05-111">Возвращает локальные переменные.</span><span class="sxs-lookup"><span data-stu-id="19b05-111">Gets the local variables.</span></span>|  
|[<span data-ttu-id="19b05-112">Метод InitializeForEnc</span><span class="sxs-lookup"><span data-stu-id="19b05-112">InitializeForEnc Method</span></span>](isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="19b05-113">Позволяет вычислять границы методов перед первым вызовом метода [ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="19b05-113">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="19b05-114">Метод UpdateMethodLines</span><span class="sxs-lookup"><span data-stu-id="19b05-114">UpdateMethodLines Method</span></span>](isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="19b05-115">Позволяет обновлять сведения о строке для метода, который не был перекомпилирован, но строки были перемещены независимо друг от друга.</span><span class="sxs-lookup"><span data-stu-id="19b05-115">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="19b05-116">Допускается использование разности для каждой инструкции.</span><span class="sxs-lookup"><span data-stu-id="19b05-116">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="19b05-117">Метод UpdateSymbolStore2</span><span class="sxs-lookup"><span data-stu-id="19b05-117">UpdateSymbolStore2 Method</span></span>](isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="19b05-118">Позволяет компилятору опускать функции, которые не были изменены из потока базы данных программы (PDB) при условии, что сведения о строке соответствуют требованиям.</span><span class="sxs-lookup"><span data-stu-id="19b05-118">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="19b05-119">Правильная информация о строке может быть определена со старыми сведениями о строке PDB и одной разностью для всех строк в функции.</span><span class="sxs-lookup"><span data-stu-id="19b05-119">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19b05-120">Требования</span><span class="sxs-lookup"><span data-stu-id="19b05-120">Requirements</span></span>  

 <span data-ttu-id="19b05-121">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="19b05-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b05-122">См. также</span><span class="sxs-lookup"><span data-stu-id="19b05-122">See also</span></span>

- [<span data-ttu-id="19b05-123">Интерфейсы хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="19b05-123">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
