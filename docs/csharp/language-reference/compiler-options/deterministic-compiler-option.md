---
description: -deterministic (параметры компилятора C#)
title: -deterministic (параметры компилятора C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: d64f4d4b0d4e9b5ed2cc1ee40662dc669fc6660d
ms.sourcegitcommit: 4f5f1855849cb02c3b610c7006ac21d7429f3348
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/15/2021
ms.locfileid: "98235330"
---
# <a name="-deterministic"></a><span data-ttu-id="687eb-103">-deterministic</span><span class="sxs-lookup"><span data-stu-id="687eb-103">-deterministic</span></span>

<span data-ttu-id="687eb-104">Указывает компилятору на необходимость создания сборки, чьи побайтовые выходные данные идентичны в разных компиляциях, если входные данные идентичны.</span><span class="sxs-lookup"><span data-stu-id="687eb-104">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="687eb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="687eb-105">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="687eb-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="687eb-106">Remarks</span></span>

<span data-ttu-id="687eb-107">По умолчанию выходные данные компилятора из заданного набора входных данных являются уникальными, поскольку компилятор добавляет метку времени и идентификатор MVID, который создается из случайных чисел.</span><span class="sxs-lookup"><span data-stu-id="687eb-107">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a MVID that is generated from random numbers.</span></span> <span data-ttu-id="687eb-108">Вы можете использовать параметр `-deterministic` для создания *детерминированной сборки*, двоичное содержимое которой идентично в разных компиляциях при условии, что входные данные не изменяются.</span><span class="sxs-lookup"><span data-stu-id="687eb-108">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span> <span data-ttu-id="687eb-109">В такой сборке поля timestamp и MVID будут заменены значениями, полученными из хэша всех входных данных компиляции.</span><span class="sxs-lookup"><span data-stu-id="687eb-109">In such a build, the timestamp and MVID fields will be replaced with values derived from a hash of all the compilation inputs.</span></span>

<span data-ttu-id="687eb-110">Компилятор учитывает идентичность следующих входных данных:</span><span class="sxs-lookup"><span data-stu-id="687eb-110">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="687eb-111">Последовательность параметров командной строки.</span><span class="sxs-lookup"><span data-stu-id="687eb-111">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="687eb-112">Содержимое RSP-файла ответов в компиляторе.</span><span class="sxs-lookup"><span data-stu-id="687eb-112">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="687eb-113">Точная версия компилятора и его связанные сборки.</span><span class="sxs-lookup"><span data-stu-id="687eb-113">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="687eb-114">Текущий путь к каталогу.</span><span class="sxs-lookup"><span data-stu-id="687eb-114">The current directory path.</span></span>
- <span data-ttu-id="687eb-115">Двоичное содержимое всех файлов, явным образом переданных компилятору прямо или косвенно, в том числе:</span><span class="sxs-lookup"><span data-stu-id="687eb-115">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="687eb-116">Исходные файлы</span><span class="sxs-lookup"><span data-stu-id="687eb-116">Source files</span></span>
  - <span data-ttu-id="687eb-117">Связанные сборки</span><span class="sxs-lookup"><span data-stu-id="687eb-117">Referenced assemblies</span></span>
  - <span data-ttu-id="687eb-118">Связанные модули</span><span class="sxs-lookup"><span data-stu-id="687eb-118">Referenced modules</span></span>
  - <span data-ttu-id="687eb-119">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="687eb-119">Resources</span></span>
  - <span data-ttu-id="687eb-120">Файл ключа строгого имени</span><span class="sxs-lookup"><span data-stu-id="687eb-120">The strong name key file</span></span>
  - <span data-ttu-id="687eb-121">Файлы ответов @</span><span class="sxs-lookup"><span data-stu-id="687eb-121">@ response files</span></span>
  - <span data-ttu-id="687eb-122">Анализаторы</span><span class="sxs-lookup"><span data-stu-id="687eb-122">Analyzers</span></span>
  - <span data-ttu-id="687eb-123">Наборы правил</span><span class="sxs-lookup"><span data-stu-id="687eb-123">Rulesets</span></span>
  - <span data-ttu-id="687eb-124">Дополнительные файлы, которые могут использоваться анализаторами</span><span class="sxs-lookup"><span data-stu-id="687eb-124">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="687eb-125">Текущий язык и региональные параметры (для языка сообщений о диагностике и исключениях).</span><span class="sxs-lookup"><span data-stu-id="687eb-125">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="687eb-126">Кодировка по умолчанию (или текущая кодовая страница), если кодировка не указана.</span><span class="sxs-lookup"><span data-stu-id="687eb-126">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="687eb-127">Наличие, отсутствие и содержимое файлов на пути поиска компилятора (задается, например, с помощью `-lib` или `-recurse`).</span><span class="sxs-lookup"><span data-stu-id="687eb-127">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="687eb-128">Платформа среды CLR, в которой выполняется компилятор.</span><span class="sxs-lookup"><span data-stu-id="687eb-128">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="687eb-129">Значение `%LIBPATH%`, которое может повлиять на загрузку зависимостей анализатора.</span><span class="sxs-lookup"><span data-stu-id="687eb-129">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="687eb-130">Если источники общедоступны, детерминированную компиляцию можно использовать, чтобы установить, компилируются ли двоичные данные из надежного источника.</span><span class="sxs-lookup"><span data-stu-id="687eb-130">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="687eb-131">Ее также можно использовать в системе непрерывной сборки, чтобы определить необходимость выполнения шагов сборки, зависящих от изменений в двоичном файле.</span><span class="sxs-lookup"><span data-stu-id="687eb-131">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="687eb-132">См. также</span><span class="sxs-lookup"><span data-stu-id="687eb-132">See also</span></span>

- [<span data-ttu-id="687eb-133">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="687eb-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="687eb-134">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="687eb-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
