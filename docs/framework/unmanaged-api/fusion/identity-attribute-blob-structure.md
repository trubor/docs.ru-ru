---
description: 'Дополнительные сведения: структура IDENTITY_ATTRIBUTE_BLOB'
title: Структура IDENTITY_ATTRIBUTE_BLOB
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IDENTITY_ATTRIBUTE_BLOB
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE_BLOB
helpviewer_keywords:
- IDENTITY_ATTRIBUTE_BLOB structure [.NET Framework fusion]
ms.assetid: af14ae5f-d226-47dd-ba90-8fc6e6605d4d
topic_type:
- apiref
ms.openlocfilehash: e89294397287cb5751196b563b1576bb4f1c0f12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800192"
---
# <a name="identity_attribute_blob-structure"></a><span data-ttu-id="7309a-103">Структура IDENTITY_ATTRIBUTE_BLOB</span><span class="sxs-lookup"><span data-stu-id="7309a-103">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>

<span data-ttu-id="7309a-104">Содержит сведения об отдельном атрибуте в сборке и состоит из трех элементов `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="7309a-104">Contains information about a single attribute in an assembly, and consists of three `DWORD`s.</span></span> <span data-ttu-id="7309a-105">Каждое из них `DWORD` является смещением в символьном буфере, созданном `CurrentIntoBuffer` методом интерфейса [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md)</span><span class="sxs-lookup"><span data-stu-id="7309a-105">Each `DWORD` is an offset into a character buffer produced by the `CurrentIntoBuffer` method of the [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) interface</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7309a-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7309a-106">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE_BLOB {  
    DWORD  ofsNamespace;  
    DWORD  ofsName;  
    DWORD  ofsValue;  
}   IDENTITY_ATTRIBUTE_BLOB;  
```  
  
## <a name="members"></a><span data-ttu-id="7309a-107">Члены</span><span class="sxs-lookup"><span data-stu-id="7309a-107">Members</span></span>  
  
|<span data-ttu-id="7309a-108">Член</span><span class="sxs-lookup"><span data-stu-id="7309a-108">Member</span></span>|<span data-ttu-id="7309a-109">Описание</span><span class="sxs-lookup"><span data-stu-id="7309a-109">Description</span></span>|  
|------------|-----------------|  
|`ofsNamespace`|<span data-ttu-id="7309a-110">Первое смещение в символьном буфере.</span><span class="sxs-lookup"><span data-stu-id="7309a-110">The first offset into the character buffer.</span></span> <span data-ttu-id="7309a-111">За этим смещением не следует пространство имен атрибута, а набор символов NULL.</span><span class="sxs-lookup"><span data-stu-id="7309a-111">This offset is not followed by the attribute's namespace, but by a series of null characters.</span></span> <span data-ttu-id="7309a-112">Поэтому он не используется.</span><span class="sxs-lookup"><span data-stu-id="7309a-112">Therefore, it is not used.</span></span>|  
|`ofsName`|<span data-ttu-id="7309a-113">Второе смещение в символьном буфере.</span><span class="sxs-lookup"><span data-stu-id="7309a-113">The second offset into the character buffer.</span></span> <span data-ttu-id="7309a-114">Это расположение отмечает начало имени атрибута.</span><span class="sxs-lookup"><span data-stu-id="7309a-114">This location marks the start of the attribute's name.</span></span>|  
|`ofsValue`|<span data-ttu-id="7309a-115">Третье смещение в символьном буфере.</span><span class="sxs-lookup"><span data-stu-id="7309a-115">The third offset into the character buffer.</span></span> <span data-ttu-id="7309a-116">Это расположение отмечает начало значения атрибута.</span><span class="sxs-lookup"><span data-stu-id="7309a-116">This location marks the start of the attribute's value.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="7309a-117">Пример</span><span class="sxs-lookup"><span data-stu-id="7309a-117">Sample</span></span>  

 <span data-ttu-id="7309a-118">В следующем примере показано несколько основных шагов, которые в итоге приводят к заполненной `IDENTITY_ATTRIBUTE_BLOB` структуре:</span><span class="sxs-lookup"><span data-stu-id="7309a-118">The following example illustrates several basic steps, which eventually result in a populated `IDENTITY_ATTRIBUTE_BLOB` structure:</span></span>  
  
1. <span data-ttu-id="7309a-119">Получите [иреференцеидентити](ireferenceidentity-interface.md) для сборки.</span><span class="sxs-lookup"><span data-stu-id="7309a-119">Obtain an [IReferenceIdentity](ireferenceidentity-interface.md) for the assembly.</span></span>  
  
2. <span data-ttu-id="7309a-120">Вызовите `IReferenceIdentity::EnumAttributes` метод и получите [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7309a-120">Call the `IReferenceIdentity::EnumAttributes` method, and obtain an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md).</span></span>  
  
3. <span data-ttu-id="7309a-121">Создайте символьный буфер и приведите его как `IDENTITY_ATTRIBUTE_BLOB` структуру.</span><span class="sxs-lookup"><span data-stu-id="7309a-121">Create a character buffer, and cast it as an `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
4. <span data-ttu-id="7309a-122">Вызовите `CurrentIntoBuffer` метод `IEnumIDENTITY_ATTRIBUTE` интерфейса.</span><span class="sxs-lookup"><span data-stu-id="7309a-122">Call the `CurrentIntoBuffer` method of the `IEnumIDENTITY_ATTRIBUTE` interface.</span></span> <span data-ttu-id="7309a-123">Этот метод копирует атрибуты `Namespace` , `Name` и `Value` в буфер символов.</span><span class="sxs-lookup"><span data-stu-id="7309a-123">This method copies the attributes `Namespace`, `Name`, and `Value` into the character buffer.</span></span> <span data-ttu-id="7309a-124">Три смещения для этих строк станут доступными в `IDENTITY_ATTRIBUTE_BLOB` структуре.</span><span class="sxs-lookup"><span data-stu-id="7309a-124">The three offsets to those strings will become available in the `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
```cpp  
// EnumAssemblyAttributes.cpp : main project file.  
  
#include "stdafx.h"  
  
#include "fusion.h"  
#include "windows.h"  
#include "stdio.h"  
#include "mscoree.h"  
#include "isolation.h"  
  
typedef HRESULT (__stdcall *PFNGETREF)(LPCWSTR pwzFile, REFIID riid, IUnknown **ppUnk);  
typedef HRESULT (__stdcall *PFNGETAUTH)(IIdentityAuthority **ppIIdentityAuthority);  
  
PFNGETREF                   g_pfnGetAssemblyIdentityFromFile = NULL;  
PFNGETAUTH                  g_pfnGetIdentityAuthority = NULL;  
IUnknown                    *g_pUnk = NULL;  
  
bool Init()  
{  
    HRESULT     hr = S_OK;  
    DWORD       dwSize = 0;  
    bool        bRC = false;  
  
    hr = CorBindToRuntimeEx(NULL, L"wks", 0, CLSID_CorRuntimeHost,  
                           IID_ICorRuntimeHost, (void **)&g_pUnk);  
    if(FAILED(hr)) {  
        printf("Error: Failed to initialize CLR runtime! hr = 0x%0x\n",  
                hr);  
        goto Exit;  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetAssemblyIdentityFromFile",  
                         (VOID **)&g_pfnGetAssemblyIdentityFromFile);  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetIdentityAuthority",  
                                (VOID **)&g_pfnGetIdentityAuthority);  
    }  
  
    if (!g_pfnGetAssemblyIdentityFromFile ||
        !g_pfnGetIdentityAuthority)  
    {  
        printf("Error: Cannot get required APIs from fusion.dll!\n");  
        goto Exit;  
    }  
  
    bRC = true;  
  
Exit:  
    return bRC;  
}  
  
void Shutdown()  
{  
    if(g_pUnk) {  
        g_pUnk->Release();  
        g_pUnk = NULL;  
    }  
}  
  
void Usage()  
{  
    printf("EnumAssemblyAttributes: A tool to enumerate the identity
            attributes of a given assembly.\n\n");  
    printf("Usage: EnumAssemblyAttributes AssemblyFilePath\n");  
    printf("\n");  
}  
  
int _cdecl wmain(int argc, LPCWSTR argv[])  
{  
    int     iResult = 1;  
    IUnknown                    *pUnk  = NULL;  
    IReferenceIdentity          *pRef  = NULL;  
    HRESULT                     hr     = S_OK;
    IEnumIDENTITY_ATTRIBUTE     *pEnum = NULL;  
    BYTE                        abData[1024];  
    DWORD                       cbAvailable;  
    DWORD                       cbUsed;  
    IDENTITY_ATTRIBUTE_BLOB     *pBlob;  
  
    if(argc != 2) {  
        Usage();  
        goto Exit;  
    }  
  
    if(!Init()) {  
        printf("Failure initializing EnumIdAttr.\n");  
        goto Exit;  
    }  
  
    hr = g_pfnGetAssemblyIdentityFromFile(argv[1],
                            __uuidof(IReferenceIdentity), &pUnk);  
  
    if (FAILED(hr)) {  
        printf("GetAssemblyIdentityFromFile failed with hr = 0x%x",
                hr);  
        goto Exit;  
    }  
  
    hr = pUnk->QueryInterface(__uuidof(IReferenceIdentity),
                              (void**)&pRef);  
    if (FAILED(hr)) {  
        goto Exit;  
    }  
  
    hr = pRef->EnumAttributes(&pEnum);  
    if (FAILED(hr)) {  
        printf("IReferenceIdentity::EnumAttributes failed with hr =
                0x%x", hr);  
        goto Exit;  
    }  
  
    pBlob = (IDENTITY_ATTRIBUTE_BLOB *)(abData);  
    while (1) {  
        cbAvailable = sizeof(abData);  
        hr = pEnum->CurrentIntoBuffer(cbAvailable, abData, &cbUsed);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer failed
                    with hr = 0x%x", hr);  
            goto Exit;  
        }  
  
        if (! cbUsed) {  
            break;  
        }  
  
        LPWSTR pwzNameSpace = (LPWSTR)(abData + pBlob->ofsNamespace);  
        LPWSTR pwzName      = (LPWSTR)(abData + pBlob->ofsName);  
        LPWSTR pwzValue     = (LPWSTR)(abData + pBlob->ofsValue);  
        printf("%ws: %ws = %ws\n", pwzNameSpace, pwzName, pwzValue);  
  
        hr = pEnum->Skip(1);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::Skip failed with hr =
                    0x%x", hr);  
            goto Exit;  
        }  
    }  
  
    iResult = 0;  
  
Exit:  
  
    Shutdown();  
  
    if (pUnk) {  
        pUnk->Release();  
    }  
  
    if (pRef) {  
        pRef->Release();  
    }  
  
    if (pEnum) {  
        pEnum->Release();  
    }  
  
    return iResult;  
}  
```  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="7309a-125">Выполнение образца</span><span class="sxs-lookup"><span data-stu-id="7309a-125">To run the sample</span></span>  

 <span data-ttu-id="7309a-126">В. \\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span><span class="sxs-lookup"><span data-stu-id="7309a-126">C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span></span>  
  
### <a name="sample-output"></a><span data-ttu-id="7309a-127">Пример выходных данных</span><span class="sxs-lookup"><span data-stu-id="7309a-127">Sample output</span></span>  

 <span data-ttu-id="7309a-128">Culture = Neutral</span><span class="sxs-lookup"><span data-stu-id="7309a-128">Culture = neutral</span></span>  
  
 <span data-ttu-id="7309a-129">имя = система</span><span class="sxs-lookup"><span data-stu-id="7309a-129">name = System</span></span>  
  
 <span data-ttu-id="7309a-130">processorArchitecture = MSIL</span><span class="sxs-lookup"><span data-stu-id="7309a-130">processorArchitecture = MSIL</span></span>  
  
 <span data-ttu-id="7309a-131">PublicKeyToken = b77a5c561934e089»</span><span class="sxs-lookup"><span data-stu-id="7309a-131">PublicKeyToken = b77a5c561934e089</span></span>  
  
 <span data-ttu-id="7309a-132">Версия = 2.0.0.0</span><span class="sxs-lookup"><span data-stu-id="7309a-132">Version = 2.0.0.0</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7309a-133">Требования</span><span class="sxs-lookup"><span data-stu-id="7309a-133">Requirements</span></span>  

 <span data-ttu-id="7309a-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7309a-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7309a-135">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="7309a-135">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="7309a-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7309a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7309a-137">См. также</span><span class="sxs-lookup"><span data-stu-id="7309a-137">See also</span></span>

- [<span data-ttu-id="7309a-138">Интерфейс IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="7309a-138">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
- [<span data-ttu-id="7309a-139">Интерфейс IEnumIDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="7309a-139">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
- [<span data-ttu-id="7309a-140">Структура IDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="7309a-140">IDENTITY_ATTRIBUTE Structure</span></span>](identity-attribute-structure.md)
- [<span data-ttu-id="7309a-141">Структуры Fusion</span><span class="sxs-lookup"><span data-stu-id="7309a-141">Fusion Structures</span></span>](fusion-structures.md)
