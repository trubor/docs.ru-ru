---
description: 'Дополнительные сведения: -deterministic'
title: -deterministic
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
ms.openlocfilehash: b339b76d4f95ba80f8e92c4961586fa390b0839a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461519"
---
# <a name="-deterministic"></a><span data-ttu-id="5ba31-103">-deterministic</span><span class="sxs-lookup"><span data-stu-id="5ba31-103">-deterministic</span></span>

<span data-ttu-id="5ba31-104">Указывает компилятору на необходимость создания сборки, чьи побайтовые выходные данные идентичны в разных компиляциях, если входные данные идентичны.</span><span class="sxs-lookup"><span data-stu-id="5ba31-104">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ba31-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5ba31-105">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="5ba31-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="5ba31-106">Remarks</span></span>

<span data-ttu-id="5ba31-107">По умолчанию выходные данные компилятора из заданного набора входных данных являются уникальными, поскольку компилятор добавляет метку времени и идентификатор GUID, который создается из случайных чисел.</span><span class="sxs-lookup"><span data-stu-id="5ba31-107">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="5ba31-108">Вы можете использовать параметр `-deterministic` для создания *детерминированной сборки*, двоичное содержимое которой идентично в разных компиляциях при условии, что входные данные не изменяются.</span><span class="sxs-lookup"><span data-stu-id="5ba31-108">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="5ba31-109">Компилятор учитывает идентичность следующих входных данных:</span><span class="sxs-lookup"><span data-stu-id="5ba31-109">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="5ba31-110">Последовательность параметров командной строки.</span><span class="sxs-lookup"><span data-stu-id="5ba31-110">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="5ba31-111">Содержимое RSP-файла ответов в компиляторе.</span><span class="sxs-lookup"><span data-stu-id="5ba31-111">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="5ba31-112">Точная версия компилятора и его связанные сборки.</span><span class="sxs-lookup"><span data-stu-id="5ba31-112">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="5ba31-113">Текущий путь к каталогу.</span><span class="sxs-lookup"><span data-stu-id="5ba31-113">The current directory path.</span></span>
- <span data-ttu-id="5ba31-114">Двоичное содержимое всех файлов, явным образом переданных компилятору прямо или косвенно, в том числе:</span><span class="sxs-lookup"><span data-stu-id="5ba31-114">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="5ba31-115">Исходные файлы</span><span class="sxs-lookup"><span data-stu-id="5ba31-115">Source files</span></span>
  - <span data-ttu-id="5ba31-116">Связанные сборки</span><span class="sxs-lookup"><span data-stu-id="5ba31-116">Referenced assemblies</span></span>
  - <span data-ttu-id="5ba31-117">Связанные модули</span><span class="sxs-lookup"><span data-stu-id="5ba31-117">Referenced modules</span></span>
  - <span data-ttu-id="5ba31-118">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="5ba31-118">Resources</span></span>
  - <span data-ttu-id="5ba31-119">Файл ключа строгого имени</span><span class="sxs-lookup"><span data-stu-id="5ba31-119">The strong name key file</span></span>
  - <span data-ttu-id="5ba31-120">Файлы ответов @</span><span class="sxs-lookup"><span data-stu-id="5ba31-120">@ response files</span></span>
  - <span data-ttu-id="5ba31-121">Анализаторы</span><span class="sxs-lookup"><span data-stu-id="5ba31-121">Analyzers</span></span>
  - <span data-ttu-id="5ba31-122">Наборы правил</span><span class="sxs-lookup"><span data-stu-id="5ba31-122">Rulesets</span></span>
  - <span data-ttu-id="5ba31-123">Дополнительные файлы, которые могут использоваться анализаторами</span><span class="sxs-lookup"><span data-stu-id="5ba31-123">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="5ba31-124">Текущий язык и региональные параметры (для языка сообщений о диагностике и исключениях).</span><span class="sxs-lookup"><span data-stu-id="5ba31-124">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="5ba31-125">Кодировка по умолчанию (или текущая кодовая страница), если кодировка не указана.</span><span class="sxs-lookup"><span data-stu-id="5ba31-125">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="5ba31-126">Наличие, отсутствие и содержимое файлов на пути поиска компилятора (задается, например, с помощью `-lib` или `-recurse`).</span><span class="sxs-lookup"><span data-stu-id="5ba31-126">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="5ba31-127">Платформа среды CLR, в которой выполняется компилятор.</span><span class="sxs-lookup"><span data-stu-id="5ba31-127">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="5ba31-128">Значение `%LIBPATH%`, которое может повлиять на загрузку зависимостей анализатора.</span><span class="sxs-lookup"><span data-stu-id="5ba31-128">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="5ba31-129">Если источники общедоступны, детерминированную компиляцию можно использовать, чтобы установить, компилируются ли двоичные данные из надежного источника.</span><span class="sxs-lookup"><span data-stu-id="5ba31-129">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="5ba31-130">Ее также можно использовать в системе непрерывной сборки, чтобы определить необходимость выполнения шагов сборки, зависящих от изменений в двоичном файле.</span><span class="sxs-lookup"><span data-stu-id="5ba31-130">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ba31-131">См. также</span><span class="sxs-lookup"><span data-stu-id="5ba31-131">See also</span></span>

- [<span data-ttu-id="5ba31-132">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="5ba31-132">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="5ba31-133">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="5ba31-133">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
