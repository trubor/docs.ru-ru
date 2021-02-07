---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: ReplaceSymbolStore'
title: Метод ISymUnmanagedReader::ReplaceSymbolStore
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
ms.openlocfilehash: e05344ee0b14d40d735ca3e557c319998daf7849
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763767"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="85abe-103">Метод ISymUnmanagedReader::ReplaceSymbolStore</span><span class="sxs-lookup"><span data-stu-id="85abe-103">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>

<span data-ttu-id="85abe-104">Заменяет имеющееся хранилище символов разностным хранилищем символов.</span><span class="sxs-lookup"><span data-stu-id="85abe-104">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="85abe-105">Этот метод аналогичен методу [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) , за исключением того, что данная Дельта действует как полная замена, а не как обновление.</span><span class="sxs-lookup"><span data-stu-id="85abe-105">This method is similar to the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85abe-106">Необходимо указать только один из `filename` `pIStream` параметров или, но не оба.</span><span class="sxs-lookup"><span data-stu-id="85abe-106">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="85abe-107">Если `filename` указан параметр, хранилище символов будет обновлено символами из этого файла.</span><span class="sxs-lookup"><span data-stu-id="85abe-107">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="85abe-108">Если `pIStream` указан параметр, хранилище будет обновляться данными из <xref:System.Runtime.InteropServices.ComTypes.IStream> .</span><span class="sxs-lookup"><span data-stu-id="85abe-108">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85abe-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="85abe-109">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85abe-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="85abe-110">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="85abe-111">окне Имя файла, содержащего хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="85abe-111">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="85abe-112">окне Файловый поток, используемый в качестве альтернативы `filename` параметру.</span><span class="sxs-lookup"><span data-stu-id="85abe-112">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85abe-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="85abe-113">Return Value</span></span>  

 <span data-ttu-id="85abe-114">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="85abe-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85abe-115">Требования</span><span class="sxs-lookup"><span data-stu-id="85abe-115">Requirements</span></span>  

 <span data-ttu-id="85abe-116">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="85abe-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85abe-117">См. также</span><span class="sxs-lookup"><span data-stu-id="85abe-117">See also</span></span>

- [<span data-ttu-id="85abe-118">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="85abe-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
