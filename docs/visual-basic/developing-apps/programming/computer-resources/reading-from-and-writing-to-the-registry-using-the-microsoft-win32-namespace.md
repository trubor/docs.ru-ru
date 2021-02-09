---
description: 'Узнайте подробнее о: Чтение реестра и запись в него с использованием пространства имен Microsoft.Win32 (Visual Basic)'
title: Чтение реестра и запись в него с использованием пространства имен Microsoft.Win32
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: beb81a6385043011a37eee82f2036aca91382240
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701590"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="f1f67-103">Чтение реестра и запись в него с использованием пространства имен Microsoft.Win32 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1f67-103">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>

<span data-ttu-id="f1f67-104">Хотя `My.Computer.Registry` должно хватать для удовлетворения основных потребностей при программировании в реестре, можно также использовать классы <xref:Microsoft.Win32.Registry> и <xref:Microsoft.Win32.RegistryKey> в пространстве имен <xref:Microsoft.Win32> .NET.</span><span class="sxs-lookup"><span data-stu-id="f1f67-104">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of .NET.</span></span>
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="f1f67-105">Разделы в классе Registry</span><span class="sxs-lookup"><span data-stu-id="f1f67-105">Keys in the Registry Class</span></span>  

 <span data-ttu-id="f1f67-106">Класс <xref:Microsoft.Win32.Registry> предоставляет основные разделы реестра, которые можно использовать для доступа к подразделам и их значениям.</span><span class="sxs-lookup"><span data-stu-id="f1f67-106">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="f1f67-107">Сами основные разделы доступны только для чтения.</span><span class="sxs-lookup"><span data-stu-id="f1f67-107">The base keys themselves are read-only.</span></span> <span data-ttu-id="f1f67-108">В следующей таблице перечислены и описаны семь разделов, предоставляемых классом <xref:Microsoft.Win32.Registry>.</span><span class="sxs-lookup"><span data-stu-id="f1f67-108">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="f1f67-109">**Key**</span><span class="sxs-lookup"><span data-stu-id="f1f67-109">**Key**</span></span>|<span data-ttu-id="f1f67-110">**Описание**</span><span class="sxs-lookup"><span data-stu-id="f1f67-110">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="f1f67-111">Определяет типы документов и свойства, связанные с этими типами.</span><span class="sxs-lookup"><span data-stu-id="f1f67-111">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="f1f67-112">Содержит сведения о конфигурации оборудования, не относящиеся к пользователю.</span><span class="sxs-lookup"><span data-stu-id="f1f67-112">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="f1f67-113">Содержит сведения о текущих настройках пользователя, таких как переменные среды.</span><span class="sxs-lookup"><span data-stu-id="f1f67-113">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="f1f67-114">Содержит динамические данные реестра, например, используемые драйверами виртуальных устройств.</span><span class="sxs-lookup"><span data-stu-id="f1f67-114">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="f1f67-115">Включает в себя пять подразделов (оборудование, SAM, безопасность, программное обеспечение и система), содержащих данные о конфигурации для локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="f1f67-115">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="f1f67-116">Содержит сведения о производительности для компонентов программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="f1f67-116">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="f1f67-117">Содержит сведения о настройках пользователя по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f1f67-117">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="f1f67-118">Безопаснее записывать данные для текущего пользователя (<xref:Microsoft.Win32.Registry.CurrentUser>), чем для локального компьютера (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="f1f67-118">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="f1f67-119">Условие, которое обычно называют "захватом", возникает, если создаваемый вами раздел уже был создан другим, возможно вредоносным, процессом.</span><span class="sxs-lookup"><span data-stu-id="f1f67-119">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="f1f67-120">Чтобы предотвратить это, используйте такой метод, как <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, который возвращает `Nothing`, если ключ еще не существует.</span><span class="sxs-lookup"><span data-stu-id="f1f67-120">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="f1f67-121">Чтение значения из реестра</span><span class="sxs-lookup"><span data-stu-id="f1f67-121">Reading a Value from the Registry</span></span>  

 <span data-ttu-id="f1f67-122">В следующем коде показано, как считать строку из раздела HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="f1f67-122">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="f1f67-123">Следующий код считывает, увеличивает, а затем записывает строку в раздел HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="f1f67-123">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="f1f67-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f1f67-124">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="f1f67-125">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="f1f67-125">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="f1f67-126">Чтение данных из реестра и запись в реестр</span><span class="sxs-lookup"><span data-stu-id="f1f67-126">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="f1f67-127">Безопасность и реестр</span><span class="sxs-lookup"><span data-stu-id="f1f67-127">Security and the Registry</span></span>](security-and-the-registry.md)
