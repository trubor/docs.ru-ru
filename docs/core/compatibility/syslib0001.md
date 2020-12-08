---
title: Предупреждение SYSLIB0001
description: Сведения об устаревших элементах, которые приводят к появлению предупреждения во время компиляции SYSLIB0001.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: d275717e22b260d9ceff4fe94993e9a0e6996cf0
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437846"
---
# <a name="syslib0001-the-utf-7-encoding-is-insecure"></a><span data-ttu-id="1fda1-103">SYSLIB0001. Кодировка UTF-7 небезопасна</span><span class="sxs-lookup"><span data-stu-id="1fda1-103">SYSLIB0001: The UTF-7 encoding is insecure</span></span>

<span data-ttu-id="1fda1-104">Кодировка UTF-7 больше не используется широко в приложениях, и многие спецификации теперь [запрещают использовать ее](https://security.stackexchange.com/a/68609/3573) при обмене.</span><span class="sxs-lookup"><span data-stu-id="1fda1-104">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="1fda1-105">Кроме того, иногда она [служит вектором атаки](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) в приложениях, которые не предусматривают получение данных в этой кодировке.</span><span class="sxs-lookup"><span data-stu-id="1fda1-105">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="1fda1-106">Корпорация Майкрософт предостерегает от использования класса <xref:System.Text.UTF7Encoding?displayProperty=nameWithType>, так как он не выполняет обнаружение ошибок.</span><span class="sxs-lookup"><span data-stu-id="1fda1-106">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="1fda1-107">В связи с этим следующие API помечены как устаревшие, начиная с версии .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="1fda1-107">Consequently, the following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="1fda1-108">При использовании этих API во время компиляции создается предупреждение `SYSLIB0001`.</span><span class="sxs-lookup"><span data-stu-id="1fda1-108">Use of these APIs generates warning `SYSLIB0001` at compile time.</span></span>

- <span data-ttu-id="1fda1-109">Свойство<xref:System.Text.Encoding.UTF7?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1fda1-109"><xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property</span></span>
- <span data-ttu-id="1fda1-110">Конструкторы <xref:System.Text.UTF7Encoding.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="1fda1-110"><xref:System.Text.UTF7Encoding.%23ctor%2A> constructors</span></span>

## <a name="workarounds"></a><span data-ttu-id="1fda1-111">Обходные пути</span><span class="sxs-lookup"><span data-stu-id="1fda1-111">Workarounds</span></span>

- <span data-ttu-id="1fda1-112">Если вы используете <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> или <xref:System.Text.UTF7Encoding> в своем формате протокола или файла:</span><span class="sxs-lookup"><span data-stu-id="1fda1-112">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="1fda1-113">Перейдите на использование <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> или <xref:System.Text.UTF8Encoding>.</span><span class="sxs-lookup"><span data-stu-id="1fda1-113">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="1fda1-114">Кодировка UTF-8 является отраслевым стандартом, поддерживающим различные языки, операционные системы и среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="1fda1-114">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="1fda1-115">Использование UTF-8 упрощает дальнейшее обслуживание кода и улучшает его совместимость с остальной экосистемой.</span><span class="sxs-lookup"><span data-stu-id="1fda1-115">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="1fda1-116">Если вы сравниваете экземпляр <xref:System.Text.Encoding> со свойством <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="1fda1-116">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="1fda1-117">Вместо этого рекомендуется выполнять проверку по кодовой странице UTF-7 — `65000`.</span><span class="sxs-lookup"><span data-stu-id="1fda1-117">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="1fda1-118">Сравнение с кодовой страницей позволяет избежать предупреждения, а также обрабатывать некоторые пограничные случаи, например, когда вызывается `new UTF7Encoding()` или создается подкласс типа.</span><span class="sxs-lookup"><span data-stu-id="1fda1-118">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="1fda1-119">См. также</span><span class="sxs-lookup"><span data-stu-id="1fda1-119">See also</span></span>

- [<span data-ttu-id="1fda1-120">Пути к коду в кодировке UTF-7 устарели</span><span class="sxs-lookup"><span data-stu-id="1fda1-120">UTF-7 code paths are obsolete</span></span>](core-libraries/5.0/utf-7-code-paths-obsolete.md)
