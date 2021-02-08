---
description: Дополнительные сведения о средстве "поиск закрытого ключа" (FindPrivateKey.exe)
title: Средство поиска закрытых ключей (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 1d87d19e17c1de89c13db6d7ca092eedf630e6ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793289"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="7aa4a-103">Средство поиска закрытых ключей (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="7aa4a-103">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="7aa4a-104">Эта программа командной строки предназначена для извлечения закрытого ключа из хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7aa4a-104">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="7aa4a-105">Например, *FindPrivateKey.exe* можно использовать для поиска расположения и имени файла закрытого ключа, связанного с конкретным сертификатом X. 509 в хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7aa4a-105">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7aa4a-106">Средство FindPrivateKey поставляется в качестве образца WCF.</span><span class="sxs-lookup"><span data-stu-id="7aa4a-106">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="7aa4a-107">Дополнительные сведения о том, где найти пример и как его создать, см. в разделе [FindPrivateKey](./samples/findprivatekey.md).</span><span class="sxs-lookup"><span data-stu-id="7aa4a-107">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="7aa4a-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7aa4a-108">Syntax</span></span>

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="7aa4a-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="7aa4a-109">Remarks</span></span>

<span data-ttu-id="7aa4a-110">В следующих таблицах описаны аргументы и параметры, которые можно использовать со средством Find Private Key (FindPrivateKey.exe).</span><span class="sxs-lookup"><span data-stu-id="7aa4a-110">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="7aa4a-111">Аргумент</span><span class="sxs-lookup"><span data-stu-id="7aa4a-111">Argument</span></span>|<span data-ttu-id="7aa4a-112">Описание</span><span class="sxs-lookup"><span data-stu-id="7aa4a-112">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="7aa4a-113">Имя хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7aa4a-113">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="7aa4a-114">Расположение хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7aa4a-114">The location of the certificate store.</span></span>|

|<span data-ttu-id="7aa4a-115">Параметр</span><span class="sxs-lookup"><span data-stu-id="7aa4a-115">Option</span></span>|<span data-ttu-id="7aa4a-116">Описание</span><span class="sxs-lookup"><span data-stu-id="7aa4a-116">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="7aa4a-117">`/n <`*SubjectName*`>`</span><span class="sxs-lookup"><span data-stu-id="7aa4a-117">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="7aa4a-118">Задает имя субъекта сертификата.</span><span class="sxs-lookup"><span data-stu-id="7aa4a-118">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="7aa4a-119">`/t <`*отпечаток*`>`</span><span class="sxs-lookup"><span data-stu-id="7aa4a-119">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="7aa4a-120">Задает отпечаток сертификата.</span><span class="sxs-lookup"><span data-stu-id="7aa4a-120">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="7aa4a-121">Используйте Certmgr.exe для извлечения отпечатка сертификата.</span><span class="sxs-lookup"><span data-stu-id="7aa4a-121">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="7aa4a-122">Выводит только имя файла.</span><span class="sxs-lookup"><span data-stu-id="7aa4a-122">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="7aa4a-123">Выводит только каталог.</span><span class="sxs-lookup"><span data-stu-id="7aa4a-123">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="7aa4a-124">Выводит абсолютное имя файла.</span><span class="sxs-lookup"><span data-stu-id="7aa4a-124">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="7aa4a-125">Примеры</span><span class="sxs-lookup"><span data-stu-id="7aa4a-125">Examples</span></span>

<span data-ttu-id="7aa4a-126">Следующая команда извлекает закрытый ключ для Джон Петров:</span><span class="sxs-lookup"><span data-stu-id="7aa4a-126">The following command retrieves the private key for John Doe:</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="7aa4a-127">Следующая команда извлекает закрытый ключ для локального компьютера:</span><span class="sxs-lookup"><span data-stu-id="7aa4a-127">The following command retrieves the private key for the local machine:</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
