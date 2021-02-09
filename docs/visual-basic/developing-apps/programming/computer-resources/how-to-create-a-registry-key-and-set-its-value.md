---
description: 'Подробнее о следующем: Практическое руководство. Создание раздела реестра и задание его значения в Visual Basic'
title: Практическое руководство. Создание раздела реестра и задание его значения
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: 73a6f5b2a092bb05df704fe6b9954ccbe13b5d90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797735"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="fbddb-103">Практическое руководство. Создание раздела реестра и задание его значения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fbddb-103">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="fbddb-104">Метод `CreateSubKey` объекта `My.Computer.Registry` можно использовать для создания раздела реестра.</span><span class="sxs-lookup"><span data-stu-id="fbddb-104">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="fbddb-105">Процедура</span><span class="sxs-lookup"><span data-stu-id="fbddb-105">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="fbddb-106">Создание раздела реестра</span><span class="sxs-lookup"><span data-stu-id="fbddb-106">To create a registry key</span></span>

- <span data-ttu-id="fbddb-107">Используйте метод `CreateSubKey`, задав куст, в который нужно поместить раздел, а также имя раздела.</span><span class="sxs-lookup"><span data-stu-id="fbddb-107">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="fbddb-108">Параметр `Subkey` нечувствителен к регистру.</span><span class="sxs-lookup"><span data-stu-id="fbddb-108">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="fbddb-109">В этом примере создается раздел реестра `MyTestKey` в HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="fbddb-109">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="fbddb-110">Создание раздела реестра и задание его значения</span><span class="sxs-lookup"><span data-stu-id="fbddb-110">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="fbddb-111">Используйте метод `CreateSubkey`, задав куст, в который нужно поместить раздел, а также имя раздела.</span><span class="sxs-lookup"><span data-stu-id="fbddb-111">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="fbddb-112">В этом примере создается раздел реестра `MyTestKey` в HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="fbddb-112">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="fbddb-113">Задайте значение с помощью метода `SetValue`.</span><span class="sxs-lookup"><span data-stu-id="fbddb-113">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="fbddb-114">В этом примере строке</span><span class="sxs-lookup"><span data-stu-id="fbddb-114">This example sets the string value.</span></span> <span data-ttu-id="fbddb-115">" MyTestKeyValue" присваивается значение "Это тестовое значение".</span><span class="sxs-lookup"><span data-stu-id="fbddb-115">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="fbddb-116">Пример</span><span class="sxs-lookup"><span data-stu-id="fbddb-116">Example</span></span>

<span data-ttu-id="fbddb-117">В этом примере создается раздел реестра `MyTestKey` в HKEY_CURRENT_USER, а затем строке `This is a test value` задается значение `MyTestKeyValue`.</span><span class="sxs-lookup"><span data-stu-id="fbddb-117">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="fbddb-118">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="fbddb-118">Robust Programming</span></span>

<span data-ttu-id="fbddb-119">Проверьте структуру реестра и найдите подходящее место для ключа.</span><span class="sxs-lookup"><span data-stu-id="fbddb-119">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="fbddb-120">Для этого можно, например, открыть раздел HKEY_CURRENT_USER\Software текущего пользователя и создать раздел с названием вашей компании.</span><span class="sxs-lookup"><span data-stu-id="fbddb-120">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="fbddb-121">Затем добавьте в ключ компании значения реестра.</span><span class="sxs-lookup"><span data-stu-id="fbddb-121">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="fbddb-122">При чтении реестра из веб-приложения текущий пользователь зависит от проверки подлинности и олицетворения, реализованных в веб-приложении.</span><span class="sxs-lookup"><span data-stu-id="fbddb-122">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="fbddb-123">Безопаснее записывать данные в папку пользователя (<xref:Microsoft.Win32.Registry.CurrentUser>), чем на локальный компьютер (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="fbddb-123">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="fbddb-124">Создавая значение реестра, необходимо решить, что делать, если это значение уже существует.</span><span class="sxs-lookup"><span data-stu-id="fbddb-124">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="fbddb-125">Другой процесс (возможно, вредоносный) мог уже создать это значение и получить к нему доступ.</span><span class="sxs-lookup"><span data-stu-id="fbddb-125">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="fbddb-126">Данные, добавленные в значение реестра, становятся доступными для другого процесса.</span><span class="sxs-lookup"><span data-stu-id="fbddb-126">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="fbddb-127">Чтобы этого избежать, используйте метод <xref:Microsoft.Win32.RegistryKey.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbddb-127">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="fbddb-128">Он возвращает `Nothing`, если данный раздел еще не существует.</span><span class="sxs-lookup"><span data-stu-id="fbddb-128">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="fbddb-129">Хранить секретные данные, например пароли, в реестре обычным текстом небезопасно, даже если раздел реестра защищен ACL (списком управления доступом).</span><span class="sxs-lookup"><span data-stu-id="fbddb-129">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="fbddb-130">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="fbddb-130">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="fbddb-131">Имя раздела — `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="fbddb-131">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="fbddb-132">У пользователя нет разрешения на создание разделов реестра (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="fbddb-132">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="fbddb-133">Имя раздела превышает ограничение в 255 символов (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="fbddb-133">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="fbddb-134">Раздел является закрытым (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="fbddb-134">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="fbddb-135">Раздел реестра доступен только для чтения (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="fbddb-135">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="fbddb-136">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fbddb-136">.NET Framework Security</span></span>

<span data-ttu-id="fbddb-137">Для запуска этого процесса сборке нужен уровень привилегий, предоставляемый классом <xref:System.Security.Permissions.RegistryPermission>.</span><span class="sxs-lookup"><span data-stu-id="fbddb-137">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="fbddb-138">Если процесс выполняется в контексте с частичным доверием, он может сгенерировать исключение из-за недостатка привилегий.</span><span class="sxs-lookup"><span data-stu-id="fbddb-138">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="fbddb-139">Аналогичным образом пользователь должен иметь правильные ACL для создания и записи параметров.</span><span class="sxs-lookup"><span data-stu-id="fbddb-139">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="fbddb-140">Например, локальное приложение, имеющее разрешение на доступ к коду, может не иметь разрешения операционной системы.</span><span class="sxs-lookup"><span data-stu-id="fbddb-140">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="fbddb-141">Дополнительные сведения см. в разделе [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="fbddb-141">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbddb-142">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="fbddb-142">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="fbddb-143">Чтение данных из реестра и запись в реестр</span><span class="sxs-lookup"><span data-stu-id="fbddb-143">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="fbddb-144">Основы управления доступом для кода</span><span class="sxs-lookup"><span data-stu-id="fbddb-144">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
