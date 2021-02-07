---
description: Дополнительные сведения о перечислении CorDebugRegister
title: Перечисление CorDebugRegister
ms.date: 03/30/2017
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
ms.openlocfilehash: 7a5dc771a239a82448f898e2f518e920993ec35a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661887"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="3a4ba-103">Перечисление CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="3a4ba-103">CorDebugRegister Enumeration</span></span>

<span data-ttu-id="3a4ba-104">Указывает регистры, связанные с данной архитектурой процессора.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-104">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a4ba-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3a4ba-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a><span data-ttu-id="3a4ba-106">Члены</span><span class="sxs-lookup"><span data-stu-id="3a4ba-106">Members</span></span>  
  
|<span data-ttu-id="3a4ba-107">Член</span><span class="sxs-lookup"><span data-stu-id="3a4ba-107">Member</span></span>|<span data-ttu-id="3a4ba-108">Описание</span><span class="sxs-lookup"><span data-stu-id="3a4ba-108">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="3a4ba-109">Регистр указателя инструкции на любом процессоре.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-109">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="3a4ba-110">Регистр указателя стека на любом процессоре.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-110">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="3a4ba-111">Регистр указателя кадра на любом процессоре.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-111">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="3a4ba-112">Регистр указателя инструкции на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-112">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="3a4ba-113">Регистр указателя стека на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-113">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="3a4ba-114">Регистр базового указателя на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-114">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="3a4ba-115">Регистр данных A на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-115">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="3a4ba-116">Регистр данных C на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-116">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="3a4ba-117">Регистр данных D на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-117">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="3a4ba-118">Регистр данных B на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-118">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="3a4ba-119">Регистр индекса источника на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-119">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="3a4ba-120">Регистр индекса назначения на процессоре x86.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-120">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="3a4ba-121">Нулевой регистр стека на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-121">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="3a4ba-122">Регистр стека #1 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-122">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="3a4ba-123">Регистр стека #2 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-123">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="3a4ba-124">Регистр стека #3 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-124">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="3a4ba-125">Регистр стека #4 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-125">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="3a4ba-126">Регистр стека #5 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-126">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="3a4ba-127">Регистр стека #6 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-127">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="3a4ba-128">Регистр стека #7 на процессоре x86 с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-128">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="3a4ba-129">Регистр указателя инструкции на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-129">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="3a4ba-130">Регистр указателя стека на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-130">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="3a4ba-131">Регистр базового указателя на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-131">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="3a4ba-132">Регистр данных A на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-132">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="3a4ba-133">Регистр данных C на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-133">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="3a4ba-134">Регистр данных D на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-134">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="3a4ba-135">Регистр данных B на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-135">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="3a4ba-136">Регистр индекса источника на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-136">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="3a4ba-137">Регистр индекса назначения на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-137">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="3a4ba-138">Регистр данных #8 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-138">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="3a4ba-139">Регистр данных #9 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-139">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="3a4ba-140">Регистр данных #10 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-140">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="3a4ba-141">Регистр данных #11 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-141">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="3a4ba-142">Регистр данных #12 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-142">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="3a4ba-143">Регистр данных #13 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-143">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="3a4ba-144">Регистр данных #14 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-144">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="3a4ba-145">Регистр данных #15 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-145">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="3a4ba-146">Регистр мультимедиа #0 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-146">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="3a4ba-147">Регистр мультимедиа #1 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-147">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="3a4ba-148">Регистр мультимедиа #2 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-148">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="3a4ba-149">Регистр мультимедиа #3 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-149">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="3a4ba-150">Регистр мультимедиа #4 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-150">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="3a4ba-151">Регистр мультимедиа #5 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-151">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="3a4ba-152">Регистр мультимедиа #6 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-152">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="3a4ba-153">Регистр мультимедиа #7 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-153">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="3a4ba-154">Регистр мультимедиа #8 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-154">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="3a4ba-155">Регистр мультимедиа #9 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-155">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="3a4ba-156">Регистр мультимедиа #10 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-156">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="3a4ba-157">Регистр мультимедиа #11 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-157">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="3a4ba-158">Регистр мультимедиа #12 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-158">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="3a4ba-159">Регистр мультимедиа #13 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-159">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="3a4ba-160">Регистр мультимедиа #14 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-160">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="3a4ba-161">Регистр мультимедиа #15 на процессоре AMD64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-161">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="3a4ba-162">Регистр указателя стека на процессоре IA-64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-162">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="3a4ba-163">Регистр данных #0 на процессоре IA-64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-163">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="3a4ba-164">Регистр данных с плавающей запятой #0 на процессоре IA-64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-164">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="3a4ba-165">Регистр счетчика команд (R15) на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-165">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="3a4ba-166">Регистр указателя стека (R13) на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-166">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="3a4ba-167">Регистр данных R0 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-167">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="3a4ba-168">Регистр данных R1 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-168">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="3a4ba-169">Регистр данных R2 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-169">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="3a4ba-170">Регистр данных R3 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-170">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="3a4ba-171">Регистр R4 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-171">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="3a4ba-172">Регистр R5 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-172">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="3a4ba-173">Регистр R6 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-173">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="3a4ba-174">Регистр R7 (указатель кадра THUMB) на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-174">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="3a4ba-175">Регистр R8 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-175">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="3a4ba-176">Регистр R9 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-176">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="3a4ba-177">Регистр R10 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-177">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="3a4ba-178">Указатель кадра на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-178">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="3a4ba-179">Регистр R12 на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-179">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="3a4ba-180">Регистр связи (R14) на процессоре ARM.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-180">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a4ba-181">Remarks</span><span class="sxs-lookup"><span data-stu-id="3a4ba-181">Remarks</span></span>  

 <span data-ttu-id="3a4ba-182">На процессоре IA-64 имеются 128 регистров данных общего назначения и 128 регистров данных с плавающей запятой, но используются только значения `REGISTER_IA64_R0` и `REGISTER_IA64_F0`.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-182">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="3a4ba-183">Другие значения можно определить следующим образом.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-183">The other values can be determined as follows:</span></span>  
  
- <span data-ttu-id="3a4ba-184">Добавьте номер регистра к `REGISTER_IA64_R0` для значений от `REGISTER_IA64_R1` до `REGISTER_IA64_R127`, которые соответствуют регистрам данных от #1 до #127 на процессоре IA-64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-184">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
- <span data-ttu-id="3a4ba-185">Добавьте номер регистра к `REGISTER_IA64_F0` для значений от `REGISTER_IA64_F1` до `REGISTER_IA64_F127`, которые соответствуют регистрам данных с плавающей запятой от #1 до #127 на процессоре IA-64.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-185">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="3a4ba-186">Например, если необходимо указать регистр данных #83 на процессоре IA-64, добавьте к `REGISTER_IA64_R0` число 83.</span><span class="sxs-lookup"><span data-stu-id="3a4ba-186">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a4ba-187">Требования</span><span class="sxs-lookup"><span data-stu-id="3a4ba-187">Requirements</span></span>  

 <span data-ttu-id="3a4ba-188">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a4ba-188">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a4ba-189">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a4ba-189">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a4ba-190">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a4ba-190">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a4ba-191">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a4ba-191">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a4ba-192">См. также</span><span class="sxs-lookup"><span data-stu-id="3a4ba-192">See also</span></span>

- [<span data-ttu-id="3a4ba-193">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="3a4ba-193">Debugging Enumerations</span></span>](debugging-enumerations.md)
