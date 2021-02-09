---
description: 'Подробнее о следующем: Практическое руководство. Запись сведений о событиях в текстовый файл (Visual Basic)'
title: Практическое руководство. Запись сведений о событиях в текстовый файл
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: eb6fab9976c010080c0cffa37edd4f790dc73956
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775140"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="56a06-103">Практическое руководство. Запись сведений о событиях в текстовый файл (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56a06-103">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="56a06-104">Объекты `My.Application.Log` и `My.Log` можно использовать для записи в журнал информации о событиях, происходящих в приложении.</span><span class="sxs-lookup"><span data-stu-id="56a06-104">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="56a06-105">В этом примере показано использование метода `My.Application.Log.WriteEntry` для записи данных трассировки в файл журнала.</span><span class="sxs-lookup"><span data-stu-id="56a06-105">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="56a06-106">Добавление и настройка прослушивателя файлового журнала</span><span class="sxs-lookup"><span data-stu-id="56a06-106">To add and configure the file log listener</span></span>

1. <span data-ttu-id="56a06-107">Щелкните правой кнопкой мыши файл app.config в **обозревателе решений** и выберите команду **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="56a06-107">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="56a06-108">\- или -</span><span class="sxs-lookup"><span data-stu-id="56a06-108">\- or -</span></span>

     <span data-ttu-id="56a06-109">Если файл app.config отсутствует, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="56a06-109">If there is no app.config file:</span></span>

    1. <span data-ttu-id="56a06-110">В меню **Проект** выберите пункт **Добавить новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="56a06-110">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="56a06-111">В диалоговом окне **Добавление нового элемента** выберите элемент **Файл конфигурации приложения**.</span><span class="sxs-lookup"><span data-stu-id="56a06-111">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="56a06-112">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="56a06-112">Click **Add**.</span></span>

2. <span data-ttu-id="56a06-113">Найдите раздел `<listeners>` в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="56a06-113">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="56a06-114">Вы найдете раздел \<listeners> в разделе \<source> с атрибутом имени DefaultSource, вложенным в раздел \<system.diagnostics> , который, в свою очередь, вложен в раздел \<configuration> верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="56a06-114">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="56a06-115">Добавьте в этот раздел `<listeners>` следующий элемент:</span><span class="sxs-lookup"><span data-stu-id="56a06-115">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="56a06-116">Найдите раздел `<sharedListeners>` в разделе `<system.diagnostics>` в разделе верхнего уровня `<configuration>`.</span><span class="sxs-lookup"><span data-stu-id="56a06-116">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="56a06-117">Добавьте в этот раздел `<sharedListeners>` следующий элемент:</span><span class="sxs-lookup"><span data-stu-id="56a06-117">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="56a06-118">Измените значение атрибута `customlocation` на путь к каталогу журнала.</span><span class="sxs-lookup"><span data-stu-id="56a06-118">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="56a06-119">Чтобы задать значение свойства прослушивателя, используйте атрибут, имеющий то же имя, что и свойство, но со всеми строчными буквами в имени.</span><span class="sxs-lookup"><span data-stu-id="56a06-119">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="56a06-120">Например, атрибуты `location` и `customlocation` задают значения свойств <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> и <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>.</span><span class="sxs-lookup"><span data-stu-id="56a06-120">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="56a06-121">Запись информации о событии в файловый журнал</span><span class="sxs-lookup"><span data-stu-id="56a06-121">To write event information to the file log</span></span>

<span data-ttu-id="56a06-122">Для записи сведений в файловый журнал используйте метод `My.Application.Log.WriteEntry` или `My.Application.Log.WriteException`.</span><span class="sxs-lookup"><span data-stu-id="56a06-122">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="56a06-123">Дополнительные сведения см. в разделах [Практическое руководство. Запись сообщений в журнал](how-to-write-log-messages.md) и [Практическое руководство. Запись в журнал сведений об исключениях](how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="56a06-123">For more information, see [How to: Write Log Messages](how-to-write-log-messages.md) and [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

<span data-ttu-id="56a06-124">После настройки прослушивателя файлового журнала для сборки он получает все сообщения, которые записываются объектом `My.Application.Log` из этой сборки.</span><span class="sxs-lookup"><span data-stu-id="56a06-124">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="56a06-125">См. также</span><span class="sxs-lookup"><span data-stu-id="56a06-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="56a06-126">Работа с журналами приложения</span><span class="sxs-lookup"><span data-stu-id="56a06-126">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="56a06-127">Практическое руководство. Исплючения журналов</span><span class="sxs-lookup"><span data-stu-id="56a06-127">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
