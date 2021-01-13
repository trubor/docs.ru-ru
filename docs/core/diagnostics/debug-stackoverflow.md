---
title: Отладка ошибок StackOverflow
description: Сведения о диагностике исключений StackOverflow
ms.topic: tutorial
ms.date: 12/22/2020
ms.openlocfilehash: 92edf854ddcc2e778949d74eff1370cf27db25b4
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/24/2020
ms.locfileid: "97764933"
---
# <a name="debugging-stackoverflow-errors"></a><span data-ttu-id="32335-103">Отладка ошибок StackOverflow</span><span class="sxs-lookup"><span data-stu-id="32335-103">Debugging StackOverflow errors</span></span>

<span data-ttu-id="32335-104">Исключение <xref:System.StackOverflowException>, которое возникает при переполнении стека выполнения из-за чрезмерного количества вложенных вызовов метода.</span><span class="sxs-lookup"><span data-stu-id="32335-104">A <xref:System.StackOverflowException> is thrown when when the execution stack overflows because it contains too many nested method calls.</span></span>  

<span data-ttu-id="32335-105">Например, рассмотрим представленное ниже приложение:</span><span class="sxs-lookup"><span data-stu-id="32335-105">For example, suppose you have an app as follows:</span></span>

````
using System;

namespace temp
{
    class Program
    {
        static void Main(string[] args)
        {
            Main(args); // oops this recursion won't stop
        }
    }
}
````

<span data-ttu-id="32335-106">Метод Main будет постоянно вызывать сам себя до тех пор, пока в стеке не закончится место.</span><span class="sxs-lookup"><span data-stu-id="32335-106">The Main method will continuously call itself until there is no more stack space.</span></span>  <span data-ttu-id="32335-107">После этого продолжение будет невозможно и возникнет исключение <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="32335-107">Once there is no more stack space, execution cannot continue and so it will throw a <xref:System.StackOverflowException>.</span></span>  

````
> dotnet run
Stack overflow.
````

> [!NOTE]
> <span data-ttu-id="32335-108">В .NET 5 и более поздних версий стек вызовов выводится на консоль.</span><span class="sxs-lookup"><span data-stu-id="32335-108">On .NET 5 and later, the callstack is output to the console.</span></span>

> [!NOTE]
> <span data-ttu-id="32335-109">В этой статье описывается отладка ситуаций переполнения стека с использованием lldb.</span><span class="sxs-lookup"><span data-stu-id="32335-109">This article describes how to debug a stack overflow with lldb.</span></span> <span data-ttu-id="32335-110">Если вы работаете в Windows, для отладки приложения рекомендуется использовать [Visual Studio](/visualstudio/debugger/what-is-debugging) или [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging).</span><span class="sxs-lookup"><span data-stu-id="32335-110">If you are running on Windows, we suggest debugging the app with [Visual Studio](/visualstudio/debugger/what-is-debugging) or [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging).</span></span>  

## <a name="example"></a><span data-ttu-id="32335-111">Пример</span><span class="sxs-lookup"><span data-stu-id="32335-111">Example</span></span>

1. <span data-ttu-id="32335-112">Запуск приложения, для которого настроено получение дампа при аварийном завершении.</span><span class="sxs-lookup"><span data-stu-id="32335-112">Run the app with it configured to collect a dump on crash</span></span>

    ````
    > export COMPlus_DbgEnableMiniDump=1
    > dotnet run
    Stack overflow.
    Writing minidump with heap to file /tmp/coredump.6412
    Written 58191872 bytes (14207 pages) to core file
    ````

2. <span data-ttu-id="32335-113">Установка расширения SOS с помощью [dotnet-sos](dotnet-sos.md).</span><span class="sxs-lookup"><span data-stu-id="32335-113">Install the SOS extension using [dotnet-sos](dotnet-sos.md)</span></span>

    ````
    dotnet-sos install
    ````

3. <span data-ttu-id="32335-114">Отладка дампа в lldb для просмотра стека сбоев.</span><span class="sxs-lookup"><span data-stu-id="32335-114">Debug the dump in lldb to see the failing stack</span></span>

    ````
    lldb --core /temp/coredump.6412
    (lldb) bt
    ...
        frame #261930: 0x00007f59b40900cc
        frame #261931: 0x00007f59b40900cc
        frame #261932: 0x00007f59b40900cc
        frame #261933: 0x00007f59b40900cc
        frame #261934: 0x00007f59b40900cc
        frame #261935: 0x00007f5a2d4a080f libcoreclr.so`CallDescrWorkerInternal at unixasmmacrosamd64.inc:867
        frame #261936: 0x00007f5a2d3cc4c3 libcoreclr.so`MethodDescCallSite::CallTargetWorker(unsigned long const*, unsigned long*, int) at callhelpers.cpp:70
        frame #261937: 0x00007f5a2d3cc468 libcoreclr.so`MethodDescCallSite::CallTargetWorker(this=<unavailable>, pArguments=0x00007ffe8222e7b0, pReturnValue=0x0000000000000000, cbReturnValue=0) at callhelpers.cpp:604
        frame #261938: 0x00007f5a2d4b6182 libcoreclr.so`RunMain(MethodDesc*, short, int*, PtrArray**) [inlined] MethodDescCallSite::Call(this=<unavailable>, pArguments=<unavailable>) at callhelpers.h:468
    ...
    ````

4. <span data-ttu-id="32335-115">Верхний кадр `0x00007f59b40900cc` повторяется несколько раз.</span><span class="sxs-lookup"><span data-stu-id="32335-115">The top frame `0x00007f59b40900cc` is repeated several times.</span></span> <span data-ttu-id="32335-116">Используйте команду [SOS](sos-debugging-extension.md) `ip2md`, чтобы определить, какой метод находится по адресу `0x00007f59b40900cc`.</span><span class="sxs-lookup"><span data-stu-id="32335-116">Use the [SOS](sos-debugging-extension.md) `ip2md` command to figure out what method is located at the `0x00007f59b40900cc` address</span></span>

    ````
    (lldb) ip2md 0x00007f59b40900cc
    MethodDesc:   00007f59b413ffa8
    Method Name:          temp.Program.Main(System.String[])
    Class:                00007f59b4181d40
    MethodTable:          00007f59b4190020
    mdToken:              0000000006000001
    Module:               00007f59b413dbf8
    IsJitted:             yes
    Current CodeAddr:     00007f59b40900a0
    Version History:
      ILCodeVersion:      0000000000000000
      ReJIT ID:           0
      IL Addr:            0000000000000000
         CodeAddr:           00007f59b40900a0  (MinOptJitted)
         NativeCodeVersion:  0000000000000000
    Source file:  /temp/Program.cs @ 9
    ````

5. <span data-ttu-id="32335-117">Просмотрите указанный метод temp.Program.Main(System.String[]) и источник "/temp/Program.cs @ 9", чтобы определить возможные ошибки.</span><span class="sxs-lookup"><span data-stu-id="32335-117">Go look at the indicated method temp.Program.Main(System.String[]) and source "/temp/Program.cs @ 9" to see if you can figure out what you did wrong.</span></span> <span data-ttu-id="32335-118">Если это не удается сделать, вы можете включить ведение журнала для этой области кода.</span><span class="sxs-lookup"><span data-stu-id="32335-118">If it still wasn't clear you could add logging in that area of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="32335-119">См. также:</span><span class="sxs-lookup"><span data-stu-id="32335-119">See Also</span></span>

* [<span data-ttu-id="32335-120">Общие сведения о дампах в .NET</span><span class="sxs-lookup"><span data-stu-id="32335-120">An introduction to dumps in .NET</span></span>](dumps.md)
* [<span data-ttu-id="32335-121">Отладка дампов Linux</span><span class="sxs-lookup"><span data-stu-id="32335-121">Debug Linux dumps</span></span>](debug-linux-dumps.md)
* [<span data-ttu-id="32335-122">Расширение отладки SOS для .NET</span><span class="sxs-lookup"><span data-stu-id="32335-122">SOS Debugging Extension for .NET</span></span>](sos-debugging-extension.md)
