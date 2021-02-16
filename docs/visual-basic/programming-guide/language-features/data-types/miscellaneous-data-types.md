---
description: Дополнительные сведения о различных типах данных (Visual Basic)
title: Прочие типы данных
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 3875a3fc3027d573013470cb96c9482a0be6cbbf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462000"
---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="b8097-103">Прочие типы данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8097-103">Miscellaneous Data Types (Visual Basic)</span></span>

<span data-ttu-id="b8097-104">Visual Basic предоставляет несколько типов данных, не ориентированных на числа или символы.</span><span class="sxs-lookup"><span data-stu-id="b8097-104">Visual Basic supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="b8097-105">Вместо этого они работают со специализированными данными, такими как значения Да/нет, значения даты и времени и адреса объектов.</span><span class="sxs-lookup"><span data-stu-id="b8097-105">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="b8097-106">Для таблицы, показывающей параллельное сравнение типов данных Visual Basic, см. в разделе [типы данных](../../../language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="b8097-106">For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="b8097-107">Логический тип</span><span class="sxs-lookup"><span data-stu-id="b8097-107">Boolean Type</span></span>  

 <span data-ttu-id="b8097-108">[Логический тип данных](../../../language-reference/data-types/boolean-data-type.md) — это значение без знака, интерпретируемое как `True` или `False` .</span><span class="sxs-lookup"><span data-stu-id="b8097-108">The [Boolean Data Type](../../../language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="b8097-109">Ширина данных зависит от платформы, реализующей реализацию.</span><span class="sxs-lookup"><span data-stu-id="b8097-109">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="b8097-110">Если переменная может содержать только два значения, например true/false, да/нет или ON/OFF, объявите ее как `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b8097-110">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="b8097-111">Тип данных</span><span class="sxs-lookup"><span data-stu-id="b8097-111">Date Type</span></span>  

 <span data-ttu-id="b8097-112">[Тип данных Date](../../../language-reference/data-types/date-data-type.md) — это 64-разрядное значение, содержащее сведения о дате и времени.</span><span class="sxs-lookup"><span data-stu-id="b8097-112">The [Date Data Type](../../../language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="b8097-113">Каждое приращение представляет 100 наносекунд времени, прошедшее с начала (12:00 AM) 1 января 1 года по григорианскому календарю.</span><span class="sxs-lookup"><span data-stu-id="b8097-113">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="b8097-114">Если переменная может содержать значение даты, значение времени или и то, и другое, объявите ее как `Date` .</span><span class="sxs-lookup"><span data-stu-id="b8097-114">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="b8097-115">Тип объекта</span><span class="sxs-lookup"><span data-stu-id="b8097-115">Object Type</span></span>  

 <span data-ttu-id="b8097-116">[Тип данных Object](../../../language-reference/data-types/object-data-type.md) — это 32-разрядный адрес, указывающий на экземпляр объекта в приложении или в другом приложении.</span><span class="sxs-lookup"><span data-stu-id="b8097-116">The [Object Data Type](../../../language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="b8097-117">`Object`Переменная может ссылаться на любой объект, распознаваемый приложением, или на данные любого типа данных.</span><span class="sxs-lookup"><span data-stu-id="b8097-117">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="b8097-118">К ним относятся оба *типа значений*, такие как `Integer` , `Boolean` и экземпляры структуры, а также *Ссылочные типы*, которые являются экземплярами объектов, созданных из таких классов, как `String` и <xref:System.Windows.Forms.Form> , и экземпляров массивов.</span><span class="sxs-lookup"><span data-stu-id="b8097-118">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="b8097-119">Если переменная хранит указатель на экземпляр класса, который не знает во время компиляции, или если он может указывать на данные различных типов данных, объявите его как `Object` .</span><span class="sxs-lookup"><span data-stu-id="b8097-119">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="b8097-120">Преимущество `Object` типа данных заключается в том, что его можно использовать для хранения данных любого типа данных.</span><span class="sxs-lookup"><span data-stu-id="b8097-120">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="b8097-121">Недостаток заключается в том, что вы получаете дополнительные операции, которые требуют больше времени на выполнение и делают приложение более медленным.</span><span class="sxs-lookup"><span data-stu-id="b8097-121">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="b8097-122">При использовании `Object` переменной для типов значений требуется *Упаковка* и *распаковка*.</span><span class="sxs-lookup"><span data-stu-id="b8097-122">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="b8097-123">При использовании его для ссылочных типов требуется *позднее связывание*.</span><span class="sxs-lookup"><span data-stu-id="b8097-123">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8097-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b8097-124">See also</span></span>

- [<span data-ttu-id="b8097-125">Символы типов</span><span class="sxs-lookup"><span data-stu-id="b8097-125">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="b8097-126">Простые типы данных</span><span class="sxs-lookup"><span data-stu-id="b8097-126">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="b8097-127">Числовые типы данных</span><span class="sxs-lookup"><span data-stu-id="b8097-127">Numeric Data Types</span></span>](numeric-data-types.md)
- [<span data-ttu-id="b8097-128">Символьные типы данных</span><span class="sxs-lookup"><span data-stu-id="b8097-128">Character Data Types</span></span>](character-data-types.md)
- [<span data-ttu-id="b8097-129">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="b8097-129">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="b8097-130">Раннее и позднее связывание</span><span class="sxs-lookup"><span data-stu-id="b8097-130">Early and Late Binding</span></span>](../early-late-binding/index.md)
