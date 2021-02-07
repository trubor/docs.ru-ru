---
description: 'Дополнительные сведения о методе: ISymUnmanagedReader:: UpdateSymbolStore'
title: Метод ISymUnmanagedReader::UpdateSymbolStore
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
ms.openlocfilehash: eb6ca01b7978b66d0a8674e5b83ce26ee341e890
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763752"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="d251c-103">Метод ISymUnmanagedReader::UpdateSymbolStore</span><span class="sxs-lookup"><span data-stu-id="d251c-103">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>

<span data-ttu-id="d251c-104">Обновляет существующее хранилище символов разностным хранилищем символов.</span><span class="sxs-lookup"><span data-stu-id="d251c-104">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="d251c-105">Этот метод используется в сценариях "изменить и продолжить" для обновления хранилища символов в соответствии с разностью с исходным переносимым исполняемым файлом (PE).</span><span class="sxs-lookup"><span data-stu-id="d251c-105">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d251c-106">Необходимо указать только один из `filename` `pIStream` параметров или, но не оба.</span><span class="sxs-lookup"><span data-stu-id="d251c-106">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="d251c-107">Если `filename` указан параметр, хранилище символов будет обновлено символами из этого файла.</span><span class="sxs-lookup"><span data-stu-id="d251c-107">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="d251c-108">Если `pIStream` указан параметр, хранилище будет обновляться данными из <xref:System.Runtime.InteropServices.ComTypes.IStream> .</span><span class="sxs-lookup"><span data-stu-id="d251c-108">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d251c-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d251c-109">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d251c-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="d251c-110">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="d251c-111">окне Имя файла, содержащего хранилище символов.</span><span class="sxs-lookup"><span data-stu-id="d251c-111">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="d251c-112">окне Файловый поток, используемый в качестве альтернативы `filename` параметру.</span><span class="sxs-lookup"><span data-stu-id="d251c-112">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d251c-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d251c-113">Return Value</span></span>  

 <span data-ttu-id="d251c-114">S_OK, если метод выполнен. в противном случае E_FAIL или другой код ошибки.</span><span class="sxs-lookup"><span data-stu-id="d251c-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d251c-115">Требования</span><span class="sxs-lookup"><span data-stu-id="d251c-115">Requirements</span></span>  

 <span data-ttu-id="d251c-116">**Заголовок:** Корсим. idl, Корсим. h</span><span class="sxs-lookup"><span data-stu-id="d251c-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d251c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d251c-117">See also</span></span>

- [<span data-ttu-id="d251c-118">Интерфейс ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="d251c-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
