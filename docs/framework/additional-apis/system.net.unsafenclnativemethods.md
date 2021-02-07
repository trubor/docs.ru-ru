---
description: 'Дополнительные сведения о: Унсафенклнативемесодс Class'
title: Класс Унсафенклнативемесодс (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.UnsafeNclNativeMethods
- System.Net.UnsafeNclNativeMethods.NativePKI
- System.Net.UnsafeNclNativeMethods.NativePKI.FindClientCertificates
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fa1084efddae0ba5cbfc9a949dcd94d2c64f3272
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699497"
---
# <a name="unsafenclnativemethods-class"></a><span data-ttu-id="ead29-103">Класс UnsafeNclNativeMethods</span><span class="sxs-lookup"><span data-stu-id="ead29-103">UnsafeNclNativeMethods class</span></span>

<span data-ttu-id="ead29-104">Содержит классы, импортирующие ненадежные встроенные сетевые методы.</span><span class="sxs-lookup"><span data-stu-id="ead29-104">Contains classes that import unsafe native networking methods.</span></span> <span data-ttu-id="ead29-105">Этот класс не наследуется.</span><span class="sxs-lookup"><span data-stu-id="ead29-105">This class cannot be inherited.</span></span>

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> <span data-ttu-id="ead29-106">Этот класс является внутренним и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="ead29-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ead29-107">Корпорация Майкрософт не поддерживает использование этого класса в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="ead29-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="nativepki-class"></a><span data-ttu-id="ead29-108">Класс Нативепки</span><span class="sxs-lookup"><span data-stu-id="ead29-108">NativePKI class</span></span>

<span data-ttu-id="ead29-109">Содержит методы, импортированные из crypt32.dll.</span><span class="sxs-lookup"><span data-stu-id="ead29-109">Contains methods imported from crypt32.dll.</span></span> <span data-ttu-id="ead29-110">Эти методы обрабатывали сертификаты при использовании безопасного протокола HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="ead29-110">These methods handle certificates when using Hypertext Transfer Protocol Secure (HTTPS).</span></span> <span data-ttu-id="ead29-111">Этот класс не наследуется.</span><span class="sxs-lookup"><span data-stu-id="ead29-111">This class cannot be inherited.</span></span>

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a><span data-ttu-id="ead29-112">Нативепки. Финдклиентцертификатес, метод</span><span class="sxs-lookup"><span data-stu-id="ead29-112">NativePKI.FindClientCertificates method</span></span>

<span data-ttu-id="ead29-113">Обнаружение доступных клиентских сертификатов для отправки на сервер.</span><span class="sxs-lookup"><span data-stu-id="ead29-113">Discovers available client certificates to send to the server.</span></span>

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a><span data-ttu-id="ead29-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ead29-114">Return value</span></span>

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

<span data-ttu-id="ead29-115">Коллекция доступных клиентских сертификатов.</span><span class="sxs-lookup"><span data-stu-id="ead29-115">A collection of available client certificates.</span></span>

## <a name="requirements"></a><span data-ttu-id="ead29-116">Требования</span><span class="sxs-lookup"><span data-stu-id="ead29-116">Requirements</span></span>

<span data-ttu-id="ead29-117">**Пространство имен:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="ead29-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="ead29-118">**Сборка:** Система (в System.dll)</span><span class="sxs-lookup"><span data-stu-id="ead29-118">**Assembly:** System (in System.dll)</span></span>
