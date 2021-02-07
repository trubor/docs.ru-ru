---
description: 'Дополнительные сведения о методе: ISymUnmanagedWriter:: Усингнамеспаце'
title: Метод ISymUnmanagedWriter::UsingNamespace
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
ms.openlocfilehash: e7d56cded125aac6154d4315c587f58f946a9a82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761958"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="8b42c-103">Метод ISymUnmanagedWriter::UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="8b42c-103">ISymUnmanagedWriter::UsingNamespace Method</span></span>

<span data-ttu-id="8b42c-104">Указывает, что данное полное имя пространства имен используется в открытой лексической области.</span><span class="sxs-lookup"><span data-stu-id="8b42c-104">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="8b42c-105">Пространство имен будет использоваться во всех областях, наследующих от текущей открытой области.</span><span class="sxs-lookup"><span data-stu-id="8b42c-105">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="8b42c-106">Закрытие текущей области также приведет к отмене использования пространства имен.</span><span class="sxs-lookup"><span data-stu-id="8b42c-106">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b42c-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8b42c-107">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b42c-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="8b42c-108">Parameters</span></span>  

 `fullName`  
 <span data-ttu-id="8b42c-109">окне Указатель на полное имя пространства имен.</span><span class="sxs-lookup"><span data-stu-id="8b42c-109">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b42c-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8b42c-110">Return Value</span></span>  

 <span data-ttu-id="8b42c-111">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="8b42c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b42c-112">Требования</span><span class="sxs-lookup"><span data-stu-id="8b42c-112">Requirements</span></span>  

 <span data-ttu-id="8b42c-113">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="8b42c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b42c-114">См. также</span><span class="sxs-lookup"><span data-stu-id="8b42c-114">See also</span></span>

- [<span data-ttu-id="8b42c-115">Интерфейс ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="8b42c-115">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
