---
description: 'Дополнительные сведения: действие завершения экземпляра'
title: Действие завершения экземпляра
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 84405ca9869369e4fe00b0049d628671a79a9f68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792691"
---
# <a name="instance-completion-action"></a><span data-ttu-id="fd9b8-103">Действие завершения экземпляра</span><span class="sxs-lookup"><span data-stu-id="fd9b8-103">Instance Completion Action</span></span>

<span data-ttu-id="fd9b8-104">Свойство **действие завершения экземпляра** хранилища экземпляров рабочих процессов SQL позволяет указать, будут ли данные и метаданные экземпляров рабочего процесса удалены из базы данных сохраняемости после завершения экземпляров.</span><span class="sxs-lookup"><span data-stu-id="fd9b8-104">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="fd9b8-105">Допустимые значения для этого свойства: **DeleteAll** и **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="fd9b8-105">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="fd9b8-106">Эти варианты описаны в следующем списке.</span><span class="sxs-lookup"><span data-stu-id="fd9b8-106">The following list describes these options:</span></span>

- <span data-ttu-id="fd9b8-107">**DeleteAll (по умолчанию).**</span><span class="sxs-lookup"><span data-stu-id="fd9b8-107">**DeleteAll (default).**</span></span> <span data-ttu-id="fd9b8-108">Если свойство имеет значение DeleteAll, данные и метаданные экземпляров рабочих процессов удаляются из базы данных сохраняемости после завершения работы экземпляров.</span><span class="sxs-lookup"><span data-stu-id="fd9b8-108">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>

- <span data-ttu-id="fd9b8-109">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="fd9b8-109">**DeleteNothing.**</span></span> <span data-ttu-id="fd9b8-110">Если свойство имеет значение DeleteNothing, данные и метаданные экземпляров рабочих процессов не удаляются из базы данных постоянного сохранения даже после завершения работы экземпляров.</span><span class="sxs-lookup"><span data-stu-id="fd9b8-110">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="fd9b8-111">Если данные о состоянии экземпляров сохраняются после завершения работы, размер базы данных сохраняемости начинает увеличиваться.</span><span class="sxs-lookup"><span data-stu-id="fd9b8-111">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="fd9b8-112">По мере роста базы данных операции, выполняемые подсистемой сохраняемости, занимают все больше времени, поэтому рекомендуется периодически удалять сведения о состоянии экземпляров из базы данных сохраняемости, чтобы службы работали с удовлетворительной производительностью.</span><span class="sxs-lookup"><span data-stu-id="fd9b8-112">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
