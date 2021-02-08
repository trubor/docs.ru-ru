---
description: 'Дополнительные сведения о: BC42015: " <interfacename> . <membername> " уже реализован базовым классом " <baseclassname> ". Предполагается повторная реализация <type>'
title: <interfacename>.<membername> уже реализован базовым классом <baseclassname>. Предполагается повторная реализация <type>
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 7e9cce6250d21dfc4255d9971eea407b3a60e96a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796032"
---
# <a name="bc42015-interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="8c639-105">BC42015: " \<interfacename> . \<membername> " уже реализован базовым классом " \<baseclassname> ".</span><span class="sxs-lookup"><span data-stu-id="8c639-105">BC42015: '\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="8c639-106">Предполагается повторная реализация \<type></span><span class="sxs-lookup"><span data-stu-id="8c639-106">Re-implementation of \<type> assumed</span></span>

<span data-ttu-id="8c639-107">Свойство, процедура или событие в производном классе использует `Implements` предложение, задающее член интерфейса, который уже реализован в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="8c639-107">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>

 <span data-ttu-id="8c639-108">Производный класс может повторно реализовать элемент интерфейса, который реализован его базовым классом.</span><span class="sxs-lookup"><span data-stu-id="8c639-108">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="8c639-109">Это не та же переопределяющая реализация базового класса.</span><span class="sxs-lookup"><span data-stu-id="8c639-109">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="8c639-110">Для получения дополнительной информации см. [Implements](../statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8c639-110">For more information, see [Implements](../statements/implements-clause.md).</span></span>

 <span data-ttu-id="8c639-111">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="8c639-111">By default, this message is a warning.</span></span> <span data-ttu-id="8c639-112">Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8c639-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="8c639-113">**Идентификатор ошибки:** BC42015</span><span class="sxs-lookup"><span data-stu-id="8c639-113">**Error ID:** BC42015</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8c639-114">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="8c639-114">To correct this error</span></span>

- <span data-ttu-id="8c639-115">Если вы собираетесь реализовать элемент интерфейса, вам не нужно предпринимать никаких действий.</span><span class="sxs-lookup"><span data-stu-id="8c639-115">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="8c639-116">Код в производном классе обращается к повторно реализованному элементу, если не используется `MyBase` ключевое слово для доступа к реализации базового класса.</span><span class="sxs-lookup"><span data-stu-id="8c639-116">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>

- <span data-ttu-id="8c639-117">Если вы не собираетесь реализовать элемент интерфейса, удалите предложение `Implements` из свойства, процедуры или объявления события.</span><span class="sxs-lookup"><span data-stu-id="8c639-117">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c639-118">См. также</span><span class="sxs-lookup"><span data-stu-id="8c639-118">See also</span></span>

- [<span data-ttu-id="8c639-119">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="8c639-119">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
