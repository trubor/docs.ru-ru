---
description: 'Дополнительные сведения о методе: IAssemblyCacheItem:: Креатестреам'
title: Метод IAssemblyCacheItem::CreateStream
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
ms.openlocfilehash: 89592d8fe1a7f43a7da20dd10883881c3339f088
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760879"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="5fa59-103">Метод IAssemblyCacheItem::CreateStream</span><span class="sxs-lookup"><span data-stu-id="5fa59-103">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="5fa59-104">Создает поток с указанными именем и форматом.</span><span class="sxs-lookup"><span data-stu-id="5fa59-104">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="5fa59-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5fa59-105">Syntax</span></span>

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a><span data-ttu-id="5fa59-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5fa59-106">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="5fa59-107">окне Флаги, определенные в Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="5fa59-107">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="5fa59-108">окне Имя создаваемого потока.</span><span class="sxs-lookup"><span data-stu-id="5fa59-108">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="5fa59-109">окне Формат файла для потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="5fa59-109">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="5fa59-110">окне Флаги формата, определенные в Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="5fa59-110">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="5fa59-111">заполняет Указатель на адрес возвращенного экземпляра [IStream](/windows/desktop/api/objidl/nn-objidl-istream) .</span><span class="sxs-lookup"><span data-stu-id="5fa59-111">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="5fa59-112">[входные, необязательные] Максимальный размер потока, на который ссылается `ppIStream` .</span><span class="sxs-lookup"><span data-stu-id="5fa59-112">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="5fa59-113">Требования</span><span class="sxs-lookup"><span data-stu-id="5fa59-113">Requirements</span></span>

<span data-ttu-id="5fa59-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fa59-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5fa59-115">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="5fa59-115">**Header:** Fusion.h</span></span>

<span data-ttu-id="5fa59-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fa59-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5fa59-117">См. также</span><span class="sxs-lookup"><span data-stu-id="5fa59-117">See also</span></span>

- [<span data-ttu-id="5fa59-118">Интерфейс IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="5fa59-118">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
