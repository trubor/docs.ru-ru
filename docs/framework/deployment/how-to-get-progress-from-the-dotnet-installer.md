---
title: Практическое руководство. Получение хода выполнения установщика .NET Framework 4.5
description: Узнайте о том, как получить ход выполнения установщика .NET Framework 4.5. В ходе разработки приложений для этой версии .NET можно включить (добавить в цепочку) настройку .NET Framework 4.5 в процесс настройки приложения.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
ms.openlocfilehash: 7e21a376c5a7551ecadeaa70c0a70968dc5752fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729126"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="1bbe7-104">Практическое руководство. Получение хода выполнения установщика .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="1bbe7-104">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>

<span data-ttu-id="1bbe7-105">.NET Framework 4.5 — это распространяемый пакет среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-105">The .NET Framework 4.5 is a redistributable runtime.</span></span> <span data-ttu-id="1bbe7-106">Если вы разрабатываете приложения для данной версии платформы .NET Framework, можно включить (присоединить к цепочке) установку .NET Framework 4.5 в качестве необходимого компонента при установке приложения.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-106">If you develop apps for this version of the .NET Framework, you can include (chain) .NET Framework 4.5 setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="1bbe7-107">Для создания специальной или универсальной процедуры установки может потребоваться автоматический запуск и отслеживание процесса установки .NET Framework 4.5 с одновременным отображением собственного представления хода выполнения установки.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-107">To present a customized or unified setup experience, you may want to silently launch .NET Framework 4.5 setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="1bbe7-108">Для включения отслеживания в автоматическом режиме установка .NET Framework 4.5, которая может находиться под наблюдением, определяет протокол с помощью сегмента памяти ввода-вывода (MMIO) для связи с вашей установкой (наблюдателем или формирователем цепочки).</span><span class="sxs-lookup"><span data-stu-id="1bbe7-108">To enable silent tracking, .NET Framework 4.5 setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="1bbe7-109">Этот протокол определяет способ, которым формирователь цепочки получает информацию о ходе выполнения, получает подробные результаты, отвечает на сообщения и отменяет установку .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-109">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the .NET Framework 4.5 setup.</span></span>

- <span data-ttu-id="1bbe7-110">**Вызов**.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-110">**Invocation**.</span></span> <span data-ttu-id="1bbe7-111">Чтобы вызвать процесс установки .NET Framework 4.5 и получать информацию о ходе выполнения из раздела MMIO, программа установки приложения должна выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="1bbe7-111">To call .NET Framework 4.5 setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>

    1. <span data-ttu-id="1bbe7-112">Вызовите распространяемую программу .NET Framework 4.5:</span><span class="sxs-lookup"><span data-stu-id="1bbe7-112">Call the .NET Framework 4.5 redistributable program:</span></span>

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        <span data-ttu-id="1bbe7-113">Где *section name* — любое имя, которое вы хотите использовать для идентификации приложения.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-113">Where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="1bbe7-114">Установка .NET Framework выполняет чтение из раздела MMIO и запись в раздел MMIO асинхронно, поэтому в течение этого времени удобно использовать события и сообщения.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-114">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="1bbe7-115">В этом примере процесс установки .NET Framework создан конструктором, который выделяет раздел MMIO (`TheSectionName`) и указывает событие (`TheEventName`):</span><span class="sxs-lookup"><span data-stu-id="1bbe7-115">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        <span data-ttu-id="1bbe7-116">Эти имена следует заменить на имена, уникальные для программы установки приложения.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-116">Please replace those names with names that are unique to your setup program.</span></span>

    2. <span data-ttu-id="1bbe7-117">Чтение из раздела MMIO.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-117">Read from the MMIO section.</span></span> <span data-ttu-id="1bbe7-118">На платформе .NET Framework 4.5 операции скачивания и установки выполняются одновременно: один компонент .NET Framework может устанавливаться, в то время как другой еще скачивается.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-118">In the .NET Framework 4.5, the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="1bbe7-119">В результате данные о ходе выполнения отправляются назад (записываются) в раздел MMIO в виде двух чисел (`m_downloadSoFar` и `m_installSoFar`), значение которых увеличивается от 0 до 255.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-119">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="1bbe7-120">Когда записано число 255 и .NET Framework завершает работу, установка завершается.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-120">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>

- <span data-ttu-id="1bbe7-121">**Коды выхода**.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-121">**Exit codes**.</span></span> <span data-ttu-id="1bbe7-122">Следующие коды выхода от команды вызова распространяемой программы .NET Framework 4.5 указывают, успешно ли выполнена установка:</span><span class="sxs-lookup"><span data-stu-id="1bbe7-122">The following exit codes from the command to call the .NET Framework 4.5 redistributable program indicate whether setup has succeeded or failed:</span></span>

  - <span data-ttu-id="1bbe7-123">0 — установка выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-123">0 - Setup completed successfully.</span></span>

  - <span data-ttu-id="1bbe7-124">3010 — установка выполнена успешно; необходима перезагрузка системы.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-124">3010 – Setup completed successfully; a system restart is required.</span></span>

  - <span data-ttu-id="1bbe7-125">1602 — установка отменена.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-125">1602 – Setup has been canceled.</span></span>

  - <span data-ttu-id="1bbe7-126">Все другие коды — в процессе установки произошли ошибки; для получения подробных сведений просмотрите файлы журналов, созданные в папке %temp%.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-126">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>

- <span data-ttu-id="1bbe7-127">**Отмена установки**.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-127">**Canceling setup**.</span></span> <span data-ttu-id="1bbe7-128">Установку можно в любое время отменить, используя метод `Abort` для установки флагов `m_downloadAbort` и`m_ installAbort` в разделе MMIO.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-128">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>

## <a name="chainer-sample"></a><span data-ttu-id="1bbe7-129">Пример формирователя цепочки</span><span class="sxs-lookup"><span data-stu-id="1bbe7-129">Chainer Sample</span></span>

<span data-ttu-id="1bbe7-130">Пример формирователя цепочки автоматически запускает и отслеживает установку .NET Framework 4.5, при этом отображая ход выполнения.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-130">The Chainer sample silently launches and tracks .NET Framework 4.5 setup while showing progress.</span></span> <span data-ttu-id="1bbe7-131">Этот пример похож на пример формирователя цепочки, предоставленный для платформы .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-131">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="1bbe7-132">Кроме того, он может избежать перезапуска системы путем обработки диалогового окна закрытия приложения платформы .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-132">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="1bbe7-133">Дополнительные сведения об этом окне сообщения см. в разделе [Уменьшение числа перезагрузок при установке платформы .NET Framework 4.5](reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="1bbe7-133">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](reducing-system-restarts.md).</span></span> <span data-ttu-id="1bbe7-134">Этот пример можно использовать и с установщиком платформы .NET Framework 4; в этом случае сообщение просто не будет отправлено.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-134">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>

> [!WARNING]
> <span data-ttu-id="1bbe7-135">Этот пример следует запускать от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-135">You must run the example as an administrator.</span></span>

<span data-ttu-id="1bbe7-136">Можно загрузить полное решение для Visual Studio, [Пример формирователя цепочки .NET Framework 4.5](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba), из галереи примеров MSDN.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-136">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) from the MSDN Samples Gallery.</span></span>

<span data-ttu-id="1bbe7-137">В следующих разделах описываются важные файлы в данном примере: MMIOChainer.h, ChainingdotNet4.cpp и IProgressObserver.h.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-137">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>

#### <a name="mmiochainerh"></a><span data-ttu-id="1bbe7-138">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="1bbe7-138">MMIOChainer.h</span></span>

- <span data-ttu-id="1bbe7-139">Файл MMIOChainer.h (см. [полный код](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) содержит определение структуры данных и базовый класс, из которого должен быть получен класс формирователя цепочки.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-139">The MMIOChainer.h file (see [complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="1bbe7-140">.NET Framework 4.5 расширяет структуру данных MMIO для обработки данных, необходимых установщику .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-140">The .NET Framework 4.5 extends the MMIO data structure to handle data that the .NET Framework 4.5 installer needs.</span></span> <span data-ttu-id="1bbe7-141">Изменения в структуре MMIO обладают обратной совместимостью, поэтому формирователь цепочки платформы .NET Framework 4 может работать с установкой платформы .NET Framework 4.5 без необходимости повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-141">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="1bbe7-142">Но этот сценарий не поддерживает функцию для уменьшения перезапусков системы.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-142">However, this scenario does not support the feature for reducing system restarts.</span></span>

    <span data-ttu-id="1bbe7-143">Поле версии предоставляет средства для определения изменений структуры и формата сообщения.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-143">A version field provides a means of identifying revisions to the structure and message format.</span></span> <span data-ttu-id="1bbe7-144">Установка платформы .NET Framework определяет версию интерфейса формирователя цепочки путем вызова функции `VirtualQuery` для определения размера сопоставления файлов.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-144">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span> <span data-ttu-id="1bbe7-145">Если размер достаточно большой, чтобы вместить поле версии, то установка платформы .NET Framework использует указанное значение.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-145">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="1bbe7-146">Если сопоставление файлов слишком мало для хранения поля версии, как в варианте с платформой .NET Framework 4, то процесс установки предполагает версию 0 (4).</span><span class="sxs-lookup"><span data-stu-id="1bbe7-146">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="1bbe7-147">Если формирователь цепочки не поддерживает версию сообщения, которое хочет отправить установка платформы .NET Framework, то установка платформы .NET Framework отвечает игнорированием.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-147">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>

    <span data-ttu-id="1bbe7-148">Структура данных MMIO определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1bbe7-148">The MMIO data structure is defined as follows:</span></span>

    ```cpp
    // MMIO data structure for interprocess communication
        struct MmioDataStructure
        {
            bool m_downloadFinished;               // Is download complete?
            bool m_installFinished;                // Is installation complete?
            bool m_downloadAbort;                  // Set to cause downloader to abort.
            bool m_installAbort;                   // Set to cause installer to abort.
            HRESULT m_hrDownloadFinished;          // Resulting HRESULT for download.
            HRESULT m_hrInstallFinished;           // Resulting HRESULT for installation.
            HRESULT m_hrInternalError;
            WCHAR m_szCurrentItemStep[MAX_PATH];
            unsigned char m_downloadSoFar;         // Download progress 0-255 (0-100% done).
            unsigned char m_installSoFar;          // Installation progress 0-255 (0-100% done).
            WCHAR m_szEventName[MAX_PATH];         // Event that chainer creates and chainee opens to sync communications.

            BYTE m_version;                        // Version of the data structure, set by chainer:
                                                   // 0x0: .NET Framework 4
                                                   // 0x1: .NET Framework 4.5

            DWORD m_messageCode;                   // Current message sent by the chainee; 0 if no message is active.
            DWORD m_messageResponse;               // Chainer's response to current message; 0 if not yet handled.
            DWORD m_messageDataLength;             // Length of the m_messageData field, in bytes.
            BYTE m_messageData[1];                 // Variable-length buffer; content depends on m_messageCode.
        };
    ```

- <span data-ttu-id="1bbe7-149">Структура данных `MmioDataStructure` не должна использоваться напрямую; вместо этого для реализации формирователя цепочки следует использовать класс `MmioChainer`.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-149">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="1bbe7-150">Создайте класс, производный от класса `MmioChainer`, для привязки распространяемого пакета .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-150">Derive from the `MmioChainer` class to chain the .NET Framework 4.5 redistributable.</span></span>

#### <a name="iprogressobserverh"></a><span data-ttu-id="1bbe7-151">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="1bbe7-151">IProgressObserver.h</span></span>

- <span data-ttu-id="1bbe7-152">Файл IProgressObserver.h реализует наблюдатель хода выполнения (см. [полный код](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span><span class="sxs-lookup"><span data-stu-id="1bbe7-152">The IProgressObserver.h file implements a progress observer ([see complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span></span> <span data-ttu-id="1bbe7-153">Этот наблюдатель получает уведомления о ходе выполнения загрузки и установки (определяется как `char`, 0–255, указывающее степень завершения 1 %–100 %).</span><span class="sxs-lookup"><span data-stu-id="1bbe7-153">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="1bbe7-154">Наблюдатель также получает уведомления, когда элемент цепочки отправляет сообщение, и наблюдатель должен отправить ответ.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-154">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="1bbe7-155">ChainingdotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="1bbe7-155">ChainingdotNet4.5.cpp</span></span>

- <span data-ttu-id="1bbe7-156">Файл [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) реализует класс `Server`, унаследованный от класса `MmioChainer`, и переопределяет соответствующие методы для отображения информации о ходе выполнения.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-156">The [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="1bbe7-157">MmioChainer создает раздел с указанным именем раздела и инициализирует формирователь цепочки с указанным именем события.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-157">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="1bbe7-158">Имя события сохраняется в сопоставленной структуре данных.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-158">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="1bbe7-159">Имена раздела и событий должны быть уникальными.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-159">You should make the section and event names unique.</span></span> <span data-ttu-id="1bbe7-160">Класс `Server` в следующем коде запускает указанную программу установки, отслеживает ход ее выполнения и возвращает код выхода.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-160">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    <span data-ttu-id="1bbe7-161">Программа установки запускается в методе Main.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-161">The installation is started in the Main method.</span></span>

    ```cpp
    // Main entry point for program
    int __cdecl main(int argc, _In_count_(argc) char **_argv)
    {
        int result = 0;
        CString args;
        if (argc > 1)
        {
            args = CString(_argv[1]);
        }

        if (IsNetFx4Present(NETFX45_RC_REVISION))
        {
            printf(".NET Framework 4.5 is already installed");
        }
        else
        {
            result = Server().Launch(args);
        }

        return result;
    }
    ```

- <span data-ttu-id="1bbe7-162">Перед запуском программы установки формирователь цепочки проверяет, не установлена ли уже .NET Framework 4.5, с помощью вызова `IsNetFx4Present`:</span><span class="sxs-lookup"><span data-stu-id="1bbe7-162">Before launching the installation, the chainer checks to see if the .NET Framework 4.5 is already installed by calling `IsNetFx4Present`:</span></span>

    ```cpp
    ///  Checks for presence of the .NET Framework 4.
    ///    A value of 0 for dwMinimumRelease indicates a check for the .NET Framework 4 full
    ///    Any other value indicates a check for a specific compatible release of the .NET Framework 4.
    #define NETFX40_FULL_REVISION 0
    // TODO: Replace with released revision number
    #define NETFX45_RC_REVISION MAKELONG(50309, 5)   // .NET Framework 4.5
    bool IsNetFx4Present(DWORD dwMinimumRelease)
    {
        DWORD dwError = ERROR_SUCCESS;
        HKEY hKey = NULL;
        DWORD dwData = 0;
        DWORD dwType = 0;
        DWORD dwSize = sizeof(dwData);

        dwError = ::RegOpenKeyExW(HKEY_LOCAL_MACHINE, L"SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full", 0, KEY_READ, &hKey);
        if (ERROR_SUCCESS == dwError)
        {
            dwError = ::RegQueryValueExW(hKey, L"Release", 0, &dwType, (LPBYTE)&dwData, &dwSize);

            if ((ERROR_SUCCESS == dwError) && (REG_DWORD != dwType))
            {
                dwError = ERROR_INVALID_DATA;
            }
            else if (ERROR_FILE_NOT_FOUND == dwError)
            {
                // Release value was not found, let's check for 4.0.
                dwError = ::RegQueryValueExW(hKey, L"Install", 0, &dwType, (LPBYTE)&dwData, &dwSize);

                // Install = (REG_DWORD)1;
                if ((ERROR_SUCCESS == dwError) && (REG_DWORD == dwType) && (dwData == 1))
                {
                    // treat 4.0 as Release = 0
                    dwData = 0;
                }
                else
                {
                    dwError = ERROR_INVALID_DATA;
                }
            }
        }

        if (hKey != NULL)
        {
            ::RegCloseKey(hKey);
        }

        return ((ERROR_SUCCESS == dwError) && (dwData >= dwMinimumRelease));
    }
    ```

- <span data-ttu-id="1bbe7-163">Можно изменить путь к исполняемому файлу (Setup.exe в примере) в методе `Launch`, чтобы он указывал на правильное расположение, или настроить код для определения расположения.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-163">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="1bbe7-164">Базовый класс `MmioChainer` предоставляет блокирующий метод `Run()`, который вызывается производным классом.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-164">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>

    ```cpp
    bool Launch(const CString& args)
    {
    CString cmdline = L"dotNetFx45_Full_x86_x64.exe -pipe TheSectionName " + args; // Customize with name and location of setup .exe that you want to run
    STARTUPINFO si = {0};
    si.cb = sizeof(si);
    PROCESS_INFORMATION pi = {0};

    // Launch the Setup.exe that installs the .NET Framework 4.5
    BOOL bLaunchedSetup = ::CreateProcess(NULL,
     cmdline.GetBuffer(),
     NULL, NULL, FALSE, 0, NULL, NULL,
     &si,
     &pi);

    // If successful
    if (bLaunchedSetup != 0)
    {
    IProgressObserver& observer = dynamic_cast<IProgressObserver&>(*this);
    Run(pi.hProcess, observer);

    ……………………..
    return (bLaunchedSetup != 0);
    }
    ```

- <span data-ttu-id="1bbe7-165">Метод `Send` перехватывает и обрабатывает сообщения.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-165">The `Send` method intercepts and processes the messages.</span></span> <span data-ttu-id="1bbe7-166">В данной версии платформы .NET Framework поддерживается только сообщение о закрытии приложения.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-166">In this version of the .NET Framework, the only supported message is the close application message.</span></span>

    ```cpp
            // SendMessage
            //
            // Send a message and wait for the response.
            // dwMessage: Message to send
            // pData: The buffer to copy the data to
            // dwDataLength: Initially a pointer to the size of pBuffer. Upon successful call, the number of bytes copied to pBuffer.
            //--------------------------------------------------------------
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)
        {
            DWORD dwResult = 0;
            printf("received message: %d\n", dwMessage);
            // Handle message
            switch (dwMessage)
            {
            case MMIO_CLOSE_APPS:
                {
                    printf("    applications are holding files in use:\n");
                    IronMan::MmioCloseApplications* applications = reinterpret_cast<IronMan::MmioCloseApplications*>(pData);
                    for(DWORD i = 0; i < applications->m_dwApplicationsSize; i++)
                    {
                        printf("      %ls (%d)\n", applications->m_applications[i].m_szName, applications->m_applications[i].m_dwPid);
                    }

                    printf("    should appliations be closed? (Y)es, (N)o, (R)efresh : ");
                    while (dwResult == 0)
                    {
                        switch (toupper(getwchar()))
                        {
                        case 'Y':
                            dwResult = IDYES;  // Close apps
                            break;
                        case 'N':
                            dwResult = IDNO;
                            break;
                        case 'R':
                            dwResult = IDRETRY;
                            break;
                        }
                    }
                    printf("\n");
                    break;
                }
            default:
                break;
            }
            printf("  response: %d\n  ", dwResult);
            return dwResult;
        }
    };
    ```

- <span data-ttu-id="1bbe7-167">Данные о ходе выполнения хранятся в переменной типа `char` без знака от 0 (0 %) до 255 (100 %).</span><span class="sxs-lookup"><span data-stu-id="1bbe7-167">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- <span data-ttu-id="1bbe7-168">HRESULT передается методу `Finished`.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-168">The HRESULT is passed to the `Finished` method.</span></span>

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="1bbe7-169">Распространяемый пакет .NET Framework 4.5 обычно записывает много сообщений о ходе выполнения и одно сообщение, указывающее о завершении (на стороне формирователя цепочки).</span><span class="sxs-lookup"><span data-stu-id="1bbe7-169">The .NET Framework 4.5 redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="1bbe7-170">Он также выполняет асинхронное чтение, осуществляя поиск записи `Abort`.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-170">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="1bbe7-171">Если он получает запись `Abort`, то отменяет установку и записывает завершенную запись с E_ABORT как его данные после прерывания установки и отката операции установки.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-171">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>

<span data-ttu-id="1bbe7-172">Типовой сервер создает случайное имя файла MMIO, создает файл (как показано в предыдущем примере кода в `Server::CreateSection`) и запускает распространяемый пакет с помощью метода `CreateProcess`, передавая имя канала с параметром `-pipe someFileSectionName`.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-172">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="1bbe7-173">Сервер должен реализовать методы `OnProgress`, `Send` и `Finished` с кодом, характерным для пользовательского интерфейса приложения.</span><span class="sxs-lookup"><span data-stu-id="1bbe7-173">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>

## <a name="see-also"></a><span data-ttu-id="1bbe7-174">См. также</span><span class="sxs-lookup"><span data-stu-id="1bbe7-174">See also</span></span>

- [<span data-ttu-id="1bbe7-175">Руководство по развертыванию для разработчиков</span><span class="sxs-lookup"><span data-stu-id="1bbe7-175">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="1bbe7-176">Развертывание</span><span class="sxs-lookup"><span data-stu-id="1bbe7-176">Deployment</span></span>](index.md)
