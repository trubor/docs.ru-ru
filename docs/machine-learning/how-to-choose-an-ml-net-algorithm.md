---
title: Выбор алгоритма ML.NET
description: Сведения о выборе алгоритма ML.NET для модели машинного обучения
ms.topic: overview
ms.date: 03/31/2021
ms.openlocfilehash: c1a35f2b5b2ece2a846469f855e91b49887f0c90
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122629"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a><span data-ttu-id="243d5-103">Выбор алгоритма ML.NET</span><span class="sxs-lookup"><span data-stu-id="243d5-103">How to choose an ML.NET algorithm</span></span>

<span data-ttu-id="243d5-104">Для каждой [задачи ML.NET](resources/tasks.md) существует несколько возможных алгоритмов обучения.</span><span class="sxs-lookup"><span data-stu-id="243d5-104">For each [ML.NET task](resources/tasks.md), there are multiple training algorithms to choose from.</span></span> <span data-ttu-id="243d5-105">Выбор конкретного алгоритма определяется проблемой, которую вы пытаетесь решить, характеристиками данных, а также доступными вам вычислительными ресурсами и ресурсами хранения.</span><span class="sxs-lookup"><span data-stu-id="243d5-105">Which one to choose depends on the problem you are trying to solve, the characteristics of your data, and the compute and storage resources you have available.</span></span> <span data-ttu-id="243d5-106">Важно отметить, что обучение модели машинного обучения — это итеративный процесс.</span><span class="sxs-lookup"><span data-stu-id="243d5-106">It is important to note that training a machine learning model is an iterative process.</span></span> <span data-ttu-id="243d5-107">Может потребоваться попробовать несколько алгоритмов, чтобы определить лучший из них.</span><span class="sxs-lookup"><span data-stu-id="243d5-107">You might need to try multiple algorithms to find the one that works best.</span></span>

<span data-ttu-id="243d5-108">Алгоритмы работают на базе **признаков**.</span><span class="sxs-lookup"><span data-stu-id="243d5-108">Algorithms operate on **features**.</span></span> <span data-ttu-id="243d5-109">Признаки — это числовые значения, вычисляемые на основе входных данных.</span><span class="sxs-lookup"><span data-stu-id="243d5-109">Features are numerical values computed from your input data.</span></span> <span data-ttu-id="243d5-110">Они являются оптимальным входными данными для алгоритмов машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="243d5-110">They are optimal inputs for machine learning algorithms.</span></span> <span data-ttu-id="243d5-111">Вы преобразовываете необработанные входные данные в признаки, используя одно или несколько [преобразований данных](resources/transforms.md).</span><span class="sxs-lookup"><span data-stu-id="243d5-111">You transform your raw input data into features using one or more [data transforms](resources/transforms.md).</span></span> <span data-ttu-id="243d5-112">Например, текстовые данные преобразуются в набор из числа слов и числа сочетаний слов.</span><span class="sxs-lookup"><span data-stu-id="243d5-112">For example, text data is transformed into a set of word counts and word combination counts.</span></span> <span data-ttu-id="243d5-113">После извлечения признаков из необработанных данных с помощью преобразований данных они считаются **определенными признаками**.</span><span class="sxs-lookup"><span data-stu-id="243d5-113">Once the features have been extracted from a raw data type using data transforms, they are referred to as **featurized**.</span></span> <span data-ttu-id="243d5-114">Например, определенные признаки текста или определенные признаки данных изображения.</span><span class="sxs-lookup"><span data-stu-id="243d5-114">For example, featurized text, or featurized image data.</span></span>

## <a name="trainer--algorithm--task"></a><span data-ttu-id="243d5-115">Обучающий алгоритм = алгоритм + задача</span><span class="sxs-lookup"><span data-stu-id="243d5-115">Trainer = Algorithm + Task</span></span>

<span data-ttu-id="243d5-116">Алгоритм — это математическое описание, используемое для создания **модели**.</span><span class="sxs-lookup"><span data-stu-id="243d5-116">An algorithm is the math that executes to produce a **model**.</span></span> <span data-ttu-id="243d5-117">Различные алгоритмы дают модели с разными характеристиками.</span><span class="sxs-lookup"><span data-stu-id="243d5-117">Different algorithms produce models with different characteristics.</span></span>

<span data-ttu-id="243d5-118">В ML.NET один алгоритм можно применить к различным задачам.</span><span class="sxs-lookup"><span data-stu-id="243d5-118">With ML.NET, the same algorithm can be applied to different tasks.</span></span> <span data-ttu-id="243d5-119">Например, стохастический двойной покоординатный подъем можно использовать для двоичной классификации, многоклассовой классификации и регрессии.</span><span class="sxs-lookup"><span data-stu-id="243d5-119">For example, Stochastic Dual Coordinate Ascent can be used for Binary Classification, Multiclass Classification, and Regression.</span></span> <span data-ttu-id="243d5-120">Различие заключается в интерпретации выходных данных алгоритма для сопоставления с задачей.</span><span class="sxs-lookup"><span data-stu-id="243d5-120">The difference is in how the output of the algorithm is interpreted to match the task.</span></span>

<span data-ttu-id="243d5-121">Для каждого сочетания алгоритма и задачи ML.NET предоставляет компонент, который выполняет алгоритм обучения и осуществляет интерпретацию.</span><span class="sxs-lookup"><span data-stu-id="243d5-121">For each algorithm/task combination, ML.NET provides a component that executes the training algorithm and makes the interpretation.</span></span> <span data-ttu-id="243d5-122">Такие компоненты называются обучающими алгоритмами.</span><span class="sxs-lookup"><span data-stu-id="243d5-122">These components are called trainers.</span></span> <span data-ttu-id="243d5-123">Например, <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> использует алгоритм **StochasticDualCoordinatedAscent**, применяемый к задаче **регрессии**.</span><span class="sxs-lookup"><span data-stu-id="243d5-123">For example, the <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> uses the **StochasticDualCoordinatedAscent** algorithm applied to the **Regression** task.</span></span>

## <a name="linear-algorithms"></a><span data-ttu-id="243d5-124">Линейные алгоритмы</span><span class="sxs-lookup"><span data-stu-id="243d5-124">Linear algorithms</span></span>

<span data-ttu-id="243d5-125">Линейные алгоритмы создают модель, которая вычисляет **оценки** на базе линейного сочетания входных данных и набора **весовых коэффициентов**.</span><span class="sxs-lookup"><span data-stu-id="243d5-125">Linear algorithms produce a model that calculates **scores** from a linear combination of the input data and a set of **weights**.</span></span> <span data-ttu-id="243d5-126">Весовые коэффициенты — это параметры модели, оцениваемые во время обучения.</span><span class="sxs-lookup"><span data-stu-id="243d5-126">The weights are parameters of the model estimated during training.</span></span>

<span data-ttu-id="243d5-127">Линейные алгоритмы хорошо подходят для признаков, являющихся [линейно сепарабельными](https://en.wikipedia.org/wiki/Linear_separability).</span><span class="sxs-lookup"><span data-stu-id="243d5-127">Linear algorithms work well for features that are [linearly separable](https://en.wikipedia.org/wiki/Linear_separability).</span></span>

<span data-ttu-id="243d5-128">Перед обучением с помощью линейного алгоритма нужно нормализовать признаки.</span><span class="sxs-lookup"><span data-stu-id="243d5-128">Before training with a linear algorithm, the features should be normalized.</span></span> <span data-ttu-id="243d5-129">Это не позволяет одному признаку оказывать большее влияние на результат по сравнению с другими признаками.</span><span class="sxs-lookup"><span data-stu-id="243d5-129">This prevents one feature from having more influence over the result than others.</span></span>

<span data-ttu-id="243d5-130">В общем случае линейные алгоритмы являются масштабируемыми и быстрыми, а также не требуют больших затрат на обучение и прогнозирование.</span><span class="sxs-lookup"><span data-stu-id="243d5-130">In general, linear algorithms are scalable, fast, cheap to train, and cheap to predict.</span></span> <span data-ttu-id="243d5-131">Они масштабируются по количеству признаков и приблизительно по размеру набора данных для обучения.</span><span class="sxs-lookup"><span data-stu-id="243d5-131">They scale by the number of features and approximately by the size of the training data set.</span></span>

<span data-ttu-id="243d5-132">Линейные алгоритмы делают несколько проходов по данным для обучения.</span><span class="sxs-lookup"><span data-stu-id="243d5-132">Linear algorithms make multiple passes over the training data.</span></span> <span data-ttu-id="243d5-133">Если набор данных помещается в память, то добавление [контрольной точки кэша](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint%2A) в конвейер ML.NET перед добавлением обучающего алгоритма ускорит обучение.</span><span class="sxs-lookup"><span data-stu-id="243d5-133">If your dataset fits into memory, then adding a [cache checkpoint](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint%2A) to your ML.NET pipeline before appending the trainer will make the training run faster.</span></span>

### <a name="averaged-perceptron"></a><span data-ttu-id="243d5-134">Усредненный персептрон</span><span class="sxs-lookup"><span data-stu-id="243d5-134">Averaged perceptron</span></span>

<span data-ttu-id="243d5-135">Идеально подходит для классификации текста.</span><span class="sxs-lookup"><span data-stu-id="243d5-135">Best for text classification.</span></span>

|<span data-ttu-id="243d5-136">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-136">Trainer</span></span>|<span data-ttu-id="243d5-137">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-137">Task</span></span>|<span data-ttu-id="243d5-138">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-138">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|<span data-ttu-id="243d5-139">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-139">Binary classification</span></span>|<span data-ttu-id="243d5-140">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-140">Yes</span></span>|

### <a name="stochastic-dual-coordinated-ascent"></a><span data-ttu-id="243d5-141">Стохастический двойной покоординатный подъем</span><span class="sxs-lookup"><span data-stu-id="243d5-141">Stochastic dual coordinated ascent</span></span>

<span data-ttu-id="243d5-142">Не требуется настройка для обеспечения хорошей производительности.</span><span class="sxs-lookup"><span data-stu-id="243d5-142">Tuning not needed for good default performance.</span></span>

|<span data-ttu-id="243d5-143">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-143">Trainer</span></span>|<span data-ttu-id="243d5-144">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-144">Task</span></span>|<span data-ttu-id="243d5-145">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-145">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>|<span data-ttu-id="243d5-146">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-146">Binary classification</span></span>|<span data-ttu-id="243d5-147">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-147">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>|<span data-ttu-id="243d5-148">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-148">Binary classification</span></span>|<span data-ttu-id="243d5-149">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-149">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>|<span data-ttu-id="243d5-150">Многоклассовая классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-150">Multiclass classification</span></span>|<span data-ttu-id="243d5-151">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-151">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>|<span data-ttu-id="243d5-152">Многоклассовая классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-152">Multiclass classification</span></span>|<span data-ttu-id="243d5-153">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-153">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>|<span data-ttu-id="243d5-154">Регрессия</span><span class="sxs-lookup"><span data-stu-id="243d5-154">Regression</span></span>|<span data-ttu-id="243d5-155">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-155">Yes</span></span>|

### <a name="l-bfgs"></a><span data-ttu-id="243d5-156">L-BFGS</span><span class="sxs-lookup"><span data-stu-id="243d5-156">L-BFGS</span></span>

<span data-ttu-id="243d5-157">Используется при большом числе признаков.</span><span class="sxs-lookup"><span data-stu-id="243d5-157">Use when number of features is large.</span></span> <span data-ttu-id="243d5-158">Создает статистику обучения логистической регрессии, но масштабируется не так хорошо, как AveragedPerceptronTrainer.</span><span class="sxs-lookup"><span data-stu-id="243d5-158">Produces logistic regression training statistics, but doesn't scale as well as the AveragedPerceptronTrainer.</span></span>

|<span data-ttu-id="243d5-159">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-159">Trainer</span></span>|<span data-ttu-id="243d5-160">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-160">Task</span></span>|<span data-ttu-id="243d5-161">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-161">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>|<span data-ttu-id="243d5-162">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-162">Binary classification</span></span>|<span data-ttu-id="243d5-163">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-163">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>|<span data-ttu-id="243d5-164">Многоклассовая классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-164">Multiclass classification</span></span>|<span data-ttu-id="243d5-165">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-165">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>|<span data-ttu-id="243d5-166">Регрессия</span><span class="sxs-lookup"><span data-stu-id="243d5-166">Regression</span></span>|<span data-ttu-id="243d5-167">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-167">Yes</span></span>|

### <a name="symbolic-stochastic-gradient-descent"></a><span data-ttu-id="243d5-168">Посимвольный стохастический градиентный спуск</span><span class="sxs-lookup"><span data-stu-id="243d5-168">Symbolic stochastic gradient descent</span></span>

<span data-ttu-id="243d5-169">Самый быстрый и точный линейный обучающий алгоритм двоичной классификации.</span><span class="sxs-lookup"><span data-stu-id="243d5-169">Fastest and most accurate linear binary classification trainer.</span></span> <span data-ttu-id="243d5-170">Хорошо масштабируется с учетом числа процессоров.</span><span class="sxs-lookup"><span data-stu-id="243d5-170">Scales well with number of processors.</span></span>

|<span data-ttu-id="243d5-171">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-171">Trainer</span></span>|<span data-ttu-id="243d5-172">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-172">Task</span></span>|<span data-ttu-id="243d5-173">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-173">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|<span data-ttu-id="243d5-174">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-174">Binary classification</span></span>|<span data-ttu-id="243d5-175">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-175">Yes</span></span>|

### <a name="online-gradient-descent"></a><span data-ttu-id="243d5-176">Метод градиентного спуска в подключенном режиме</span><span class="sxs-lookup"><span data-stu-id="243d5-176">Online gradient descent</span></span>

<span data-ttu-id="243d5-177">Реализует стандартный (не пакетный) стохастический градиентный спуск с выбором функций потери и возможностью обновлять весовой вектор по среднему значению наблюдаемых векторов.</span><span class="sxs-lookup"><span data-stu-id="243d5-177">Implements the standard (non-batch) stochastic gradient descent, with a choice of loss functions, and an option to update the weight vector using the average of the vectors seen over time.</span></span>

|<span data-ttu-id="243d5-178">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-178">Trainer</span></span>|<span data-ttu-id="243d5-179">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-179">Task</span></span>|<span data-ttu-id="243d5-180">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-180">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>|<span data-ttu-id="243d5-181">Регрессия</span><span class="sxs-lookup"><span data-stu-id="243d5-181">Regression</span></span>|<span data-ttu-id="243d5-182">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-182">Yes</span></span>|

## <a name="decision-tree-algorithms"></a><span data-ttu-id="243d5-183">Алгоритмы дерева принятия решений</span><span class="sxs-lookup"><span data-stu-id="243d5-183">Decision tree algorithms</span></span>

<span data-ttu-id="243d5-184">Алгоритмы дерева принятия решений создают модель, которая содержит ряд решений: по сути, блок-схему для значений данных.</span><span class="sxs-lookup"><span data-stu-id="243d5-184">Decision tree algorithms create a model that contains a series of decisions: effectively a flow chart through the data values.</span></span>

<span data-ttu-id="243d5-185">Для использования этого типа алгоритма не требуются линейно масштабируемые признаки.</span><span class="sxs-lookup"><span data-stu-id="243d5-185">Features do not need to be linearly separable to use this type of algorithm.</span></span> <span data-ttu-id="243d5-186">Кроме того, признаки не нужно нормализовывать, так как отдельные значения в векторе признаков используются независимо в процессе принятия решений.</span><span class="sxs-lookup"><span data-stu-id="243d5-186">And features do not need to be normalized, because the individual values in the feature vector are used independently in the decision process.</span></span>

<span data-ttu-id="243d5-187">Алгоритмы дерева принятия решений обычно очень точны.</span><span class="sxs-lookup"><span data-stu-id="243d5-187">Decision tree algorithms are generally very accurate.</span></span>

<span data-ttu-id="243d5-188">За исключением обобщенных аддитивных моделей (GAM), модели дерева могут иметь недостаточную объясняемость, когда число признаков велико.</span><span class="sxs-lookup"><span data-stu-id="243d5-188">Except for Generalized Additive Models (GAMs), tree models can lack explainability when the number of features is large.</span></span>

<span data-ttu-id="243d5-189">Алгоритмы дерева принятия решений используют больше ресурсов и хуже масштабируются по сравнению с линейными алгоритмами.</span><span class="sxs-lookup"><span data-stu-id="243d5-189">Decision tree algorithms take more resources and do not scale as well as linear ones do.</span></span> <span data-ttu-id="243d5-190">Они хорошо подходят для наборов данных, помещающихся в память.</span><span class="sxs-lookup"><span data-stu-id="243d5-190">They do perform well on datasets that can fit into memory.</span></span>

<span data-ttu-id="243d5-191">Расширенные деревья принятия решений представляют собой ансамбль небольших деревьев, где каждое дерево оценивает входные данные и передает результат следующему дереву для уточнения оценки и т. д., то есть каждое следующее дерево улучшает результат предыдущего.</span><span class="sxs-lookup"><span data-stu-id="243d5-191">Boosted decision trees are an ensemble of small trees where each tree scores the input data and passes the score onto the next tree to produce a better score, and so on, where each tree in the ensemble improves on the previous.</span></span>

### <a name="light-gradient-boosted-machine"></a><span data-ttu-id="243d5-192">Машина слабого градиентного бустинга</span><span class="sxs-lookup"><span data-stu-id="243d5-192">Light gradient boosted machine</span></span>

<span data-ttu-id="243d5-193">Самый быстрый и точный из обучающих алгоритмов деревьев двоичной классификации.</span><span class="sxs-lookup"><span data-stu-id="243d5-193">Fastest and most accurate of the binary classification tree trainers.</span></span> <span data-ttu-id="243d5-194">Широкие возможности настройки.</span><span class="sxs-lookup"><span data-stu-id="243d5-194">Highly tunable.</span></span>

|<span data-ttu-id="243d5-195">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-195">Trainer</span></span>|<span data-ttu-id="243d5-196">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-196">Task</span></span>|<span data-ttu-id="243d5-197">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-197">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>|<span data-ttu-id="243d5-198">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-198">Binary classification</span></span>|<span data-ttu-id="243d5-199">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-199">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>|<span data-ttu-id="243d5-200">Многоклассовая классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-200">Multiclass classification</span></span>|<span data-ttu-id="243d5-201">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-201">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>|<span data-ttu-id="243d5-202">Регрессия</span><span class="sxs-lookup"><span data-stu-id="243d5-202">Regression</span></span>|<span data-ttu-id="243d5-203">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-203">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>|<span data-ttu-id="243d5-204">Функции ранжирования</span><span class="sxs-lookup"><span data-stu-id="243d5-204">Ranking</span></span>|<span data-ttu-id="243d5-205">Нет</span><span class="sxs-lookup"><span data-stu-id="243d5-205">No</span></span>|

### <a name="fast-tree"></a><span data-ttu-id="243d5-206">Быстрое дерево</span><span class="sxs-lookup"><span data-stu-id="243d5-206">Fast tree</span></span>

<span data-ttu-id="243d5-207">Используется для данных изображения с определенными признаками.</span><span class="sxs-lookup"><span data-stu-id="243d5-207">Use for featurized image data.</span></span> <span data-ttu-id="243d5-208">Устойчив к несбалансированным данным.</span><span class="sxs-lookup"><span data-stu-id="243d5-208">Resilient to unbalanced data.</span></span> <span data-ttu-id="243d5-209">Широкие возможности настройки.</span><span class="sxs-lookup"><span data-stu-id="243d5-209">Highly tunable.</span></span>

|<span data-ttu-id="243d5-210">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-210">Trainer</span></span>|<span data-ttu-id="243d5-211">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-211">Task</span></span>|<span data-ttu-id="243d5-212">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-212">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>|<span data-ttu-id="243d5-213">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-213">Binary classification</span></span>|<span data-ttu-id="243d5-214">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-214">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>|<span data-ttu-id="243d5-215">Регрессия</span><span class="sxs-lookup"><span data-stu-id="243d5-215">Regression</span></span>|<span data-ttu-id="243d5-216">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-216">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>|<span data-ttu-id="243d5-217">Регрессия</span><span class="sxs-lookup"><span data-stu-id="243d5-217">Regression</span></span>|<span data-ttu-id="243d5-218">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-218">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>|<span data-ttu-id="243d5-219">Функции ранжирования</span><span class="sxs-lookup"><span data-stu-id="243d5-219">Ranking</span></span>|<span data-ttu-id="243d5-220">Нет</span><span class="sxs-lookup"><span data-stu-id="243d5-220">No</span></span>|

### <a name="fast-forest"></a><span data-ttu-id="243d5-221">Быстрый лес</span><span class="sxs-lookup"><span data-stu-id="243d5-221">Fast forest</span></span>

<span data-ttu-id="243d5-222">Отлично подходит для данных с высоким уровнем шума.</span><span class="sxs-lookup"><span data-stu-id="243d5-222">Works well with noisy data.</span></span>

|<span data-ttu-id="243d5-223">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-223">Trainer</span></span>|<span data-ttu-id="243d5-224">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-224">Task</span></span>|<span data-ttu-id="243d5-225">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-225">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>|<span data-ttu-id="243d5-226">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-226">Binary classification</span></span>|<span data-ttu-id="243d5-227">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-227">Yes</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>|<span data-ttu-id="243d5-228">Регрессия</span><span class="sxs-lookup"><span data-stu-id="243d5-228">Regression</span></span>|<span data-ttu-id="243d5-229">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-229">Yes</span></span>|

### <a name="generalized-additive-model-gam"></a><span data-ttu-id="243d5-230">Обобщенная аддитивная модель (GAM)</span><span class="sxs-lookup"><span data-stu-id="243d5-230">Generalized additive model (GAM)</span></span>

<span data-ttu-id="243d5-231">Лучше всего подходит для задач, с которыми хорошо справляются алгоритмы дерева, если объясняемость имеет высокий приоритет.</span><span class="sxs-lookup"><span data-stu-id="243d5-231">Best for problems that perform well with tree algorithms but where explainability is a priority.</span></span>

|<span data-ttu-id="243d5-232">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-232">Trainer</span></span>|<span data-ttu-id="243d5-233">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-233">Task</span></span>|<span data-ttu-id="243d5-234">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-234">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>|<span data-ttu-id="243d5-235">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-235">Binary classification</span></span>|<span data-ttu-id="243d5-236">Нет</span><span class="sxs-lookup"><span data-stu-id="243d5-236">No</span></span>|
|<xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>|<span data-ttu-id="243d5-237">Регрессия</span><span class="sxs-lookup"><span data-stu-id="243d5-237">Regression</span></span>|<span data-ttu-id="243d5-238">Нет</span><span class="sxs-lookup"><span data-stu-id="243d5-238">No</span></span>|

## <a name="matrix-factorization"></a><span data-ttu-id="243d5-239">Факторизация матрицы</span><span class="sxs-lookup"><span data-stu-id="243d5-239">Matrix factorization</span></span>

### <a name="matrix-factorization"></a><span data-ttu-id="243d5-240">Факторизация матрицы</span><span class="sxs-lookup"><span data-stu-id="243d5-240">Matrix Factorization</span></span>

<span data-ttu-id="243d5-241">Используется для [совместной фильтрации](https://en.wikipedia.org/wiki/Collaborative_filtering) в рекомендации.</span><span class="sxs-lookup"><span data-stu-id="243d5-241">Used for [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) in recommendation.</span></span>

|<span data-ttu-id="243d5-242">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-242">Trainer</span></span>|<span data-ttu-id="243d5-243">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-243">Task</span></span>|<span data-ttu-id="243d5-244">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-244">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>|<span data-ttu-id="243d5-245">Рекомендация</span><span class="sxs-lookup"><span data-stu-id="243d5-245">Recommendation</span></span>|<span data-ttu-id="243d5-246">Нет</span><span class="sxs-lookup"><span data-stu-id="243d5-246">No</span></span>|

### <a name="field-aware-factorization-machine"></a><span data-ttu-id="243d5-247">Факторизационный метод с полями</span><span class="sxs-lookup"><span data-stu-id="243d5-247">Field Aware Factorization Machine</span></span>

 <span data-ttu-id="243d5-248">Лучше всего подходит для разреженных категориальных данных с большими наборами данных.</span><span class="sxs-lookup"><span data-stu-id="243d5-248">Best for sparse categorical data, with large datasets.</span></span>

|<span data-ttu-id="243d5-249">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-249">Trainer</span></span>|<span data-ttu-id="243d5-250">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-250">Task</span></span>|<span data-ttu-id="243d5-251">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-251">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|<span data-ttu-id="243d5-252">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-252">Binary classification</span></span>|<span data-ttu-id="243d5-253">Нет</span><span class="sxs-lookup"><span data-stu-id="243d5-253">No</span></span>|

## <a name="meta-algorithms"></a><span data-ttu-id="243d5-254">Метаалгоритмы</span><span class="sxs-lookup"><span data-stu-id="243d5-254">Meta algorithms</span></span>

<span data-ttu-id="243d5-255">Эти обучающие алгоритмы создают многоклассовый обучающий алгоритм из двоичного.</span><span class="sxs-lookup"><span data-stu-id="243d5-255">These trainers create a multiclass trainer from a binary trainer.</span></span> <span data-ttu-id="243d5-256">Используется с <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>, <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>.</span><span class="sxs-lookup"><span data-stu-id="243d5-256">Use with <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>, <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>.</span></span>

### <a name="one-versus-all"></a><span data-ttu-id="243d5-257">Один против всех</span><span class="sxs-lookup"><span data-stu-id="243d5-257">One versus all</span></span>

<span data-ttu-id="243d5-258">Этот многоклассовый классификатор обучает один двоичный классификатор для каждого класса, который отличает этот класс от других.</span><span class="sxs-lookup"><span data-stu-id="243d5-258">This multiclass classifier trains one binary classifier for each class, which distinguishes that class from all other classes.</span></span> <span data-ttu-id="243d5-259">Масштабирование ограничено числом классов для классификации.</span><span class="sxs-lookup"><span data-stu-id="243d5-259">Is limited in scale by the number of classes to categorize.</span></span>

|<span data-ttu-id="243d5-260">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-260">Trainer</span></span>|<span data-ttu-id="243d5-261">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-261">Task</span></span>|<span data-ttu-id="243d5-262">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-262">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OneVersusAllTrainer>|<span data-ttu-id="243d5-263">Многоклассовая классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-263">Multiclass classification</span></span>|<span data-ttu-id="243d5-264">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-264">Yes</span></span>|

### <a name="pairwise-coupling"></a><span data-ttu-id="243d5-265">Попарное соединение</span><span class="sxs-lookup"><span data-stu-id="243d5-265">Pairwise coupling</span></span>

<span data-ttu-id="243d5-266">Этот многоклассовый классификатор обучает алгоритм двоичной классификации для каждой пары классов.</span><span class="sxs-lookup"><span data-stu-id="243d5-266">This multiclass classifier trains a binary classification algorithm on each pair of classes.</span></span> <span data-ttu-id="243d5-267">Масштабирование ограничено числом классов, так как требуется обучение для каждого сочетания из двух классов.</span><span class="sxs-lookup"><span data-stu-id="243d5-267">Is limited in scale by the number of classes, as each combination of two classes must be trained.</span></span>

|<span data-ttu-id="243d5-268">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-268">Trainer</span></span>|<span data-ttu-id="243d5-269">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-269">Task</span></span>|<span data-ttu-id="243d5-270">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-270">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>|<span data-ttu-id="243d5-271">Многоклассовая классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-271">Multiclass classification</span></span>|<span data-ttu-id="243d5-272">Нет</span><span class="sxs-lookup"><span data-stu-id="243d5-272">No</span></span>|

## <a name="k-means"></a><span data-ttu-id="243d5-273">Метод k-средних</span><span class="sxs-lookup"><span data-stu-id="243d5-273">K-Means</span></span>

<span data-ttu-id="243d5-274">Используется для кластеризации.</span><span class="sxs-lookup"><span data-stu-id="243d5-274">Used for clustering.</span></span>

|<span data-ttu-id="243d5-275">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-275">Trainer</span></span>|<span data-ttu-id="243d5-276">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-276">Task</span></span>|<span data-ttu-id="243d5-277">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-277">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.KMeansTrainer>|<span data-ttu-id="243d5-278">Кластеризация</span><span class="sxs-lookup"><span data-stu-id="243d5-278">Clustering</span></span>|<span data-ttu-id="243d5-279">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-279">Yes</span></span>|

## <a name="principal-component-analysis"></a><span data-ttu-id="243d5-280">Анализ главных компонентов</span><span class="sxs-lookup"><span data-stu-id="243d5-280">Principal component analysis</span></span>

<span data-ttu-id="243d5-281">Используется для обнаружения аномалий.</span><span class="sxs-lookup"><span data-stu-id="243d5-281">Used for anomaly detection.</span></span>

|<span data-ttu-id="243d5-282">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-282">Trainer</span></span>|<span data-ttu-id="243d5-283">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-283">Task</span></span>|<span data-ttu-id="243d5-284">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-284">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|<span data-ttu-id="243d5-285">Обнаружение аномалий</span><span class="sxs-lookup"><span data-stu-id="243d5-285">Anomaly detection</span></span>|<span data-ttu-id="243d5-286">Нет</span><span class="sxs-lookup"><span data-stu-id="243d5-286">No</span></span>|

## <a name="naive-bayes"></a><span data-ttu-id="243d5-287">упрощенный алгоритм Байеса</span><span class="sxs-lookup"><span data-stu-id="243d5-287">Naive Bayes</span></span>

<span data-ttu-id="243d5-288">Этот алгоритм многоклассовой классификации используется, когда признаки являются независимыми, а набор данных небольшой.</span><span class="sxs-lookup"><span data-stu-id="243d5-288">Use this multi-class classification algorithm when the features are independent, and the training dataset is small.</span></span>

|<span data-ttu-id="243d5-289">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-289">Trainer</span></span>|<span data-ttu-id="243d5-290">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-290">Task</span></span>|<span data-ttu-id="243d5-291">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-291">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|<span data-ttu-id="243d5-292">Многоклассовая классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-292">Multiclass classification</span></span>|<span data-ttu-id="243d5-293">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-293">Yes</span></span>|

## <a name="prior-trainer"></a><span data-ttu-id="243d5-294">Базовый обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-294">Prior Trainer</span></span>

<span data-ttu-id="243d5-295">Этот алгоритм двоичной классификации позволяет задать базовый уровень производительности для других обучающих алгоритмов.</span><span class="sxs-lookup"><span data-stu-id="243d5-295">Use this binary classification algorithm to baseline the performance of other trainers.</span></span> <span data-ttu-id="243d5-296">Для обеспечения эффективности метрики других обучающих алгоритмов должны быть лучше, чем у базового.</span><span class="sxs-lookup"><span data-stu-id="243d5-296">To be effective, the metrics of the other trainers should be better than the prior trainer.</span></span>

|<span data-ttu-id="243d5-297">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-297">Trainer</span></span>|<span data-ttu-id="243d5-298">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-298">Task</span></span>|<span data-ttu-id="243d5-299">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-299">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.PriorTrainer>|<span data-ttu-id="243d5-300">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-300">Binary classification</span></span>|<span data-ttu-id="243d5-301">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-301">Yes</span></span>|

## <a name="support-vector-machines"></a><span data-ttu-id="243d5-302">Метод опорных векторов</span><span class="sxs-lookup"><span data-stu-id="243d5-302">Support vector machines</span></span>

<span data-ttu-id="243d5-303">Метод опорных векторов (SVM) — это невероятно популярный и хорошо изученный класс моделей для контролируемого обучения, который можно использовать в линейных и нелинейных задачах классификации.</span><span class="sxs-lookup"><span data-stu-id="243d5-303">Support vector machines (SVMs) are an extremely popular and well-researched class of supervised learning models, which can be used in linear and non-linear classification tasks.</span></span>

<span data-ttu-id="243d5-304">В последних исследованиях основное внимание уделяется способам оптимизации этих моделей для эффективного масштабирования до более крупных наборов обучающих данных.</span><span class="sxs-lookup"><span data-stu-id="243d5-304">Recent research has focused on ways to optimize these models to efficiently scale to larger training sets.</span></span>

### <a name="linear-svm"></a><span data-ttu-id="243d5-305">Линейный метод опорных векторов</span><span class="sxs-lookup"><span data-stu-id="243d5-305">Linear SVM</span></span>

<span data-ttu-id="243d5-306">Прогнозирует целевое значение с использованием модели линейной двоичной классификации, обученной по двоичным данным с метками.</span><span class="sxs-lookup"><span data-stu-id="243d5-306">Predicts a target using a linear binary classification model trained over boolean labeled data.</span></span> <span data-ttu-id="243d5-307">Поочередно применяет этапы стохастического градиентного спуска и проекции.</span><span class="sxs-lookup"><span data-stu-id="243d5-307">Alternates between stochastic gradient descent steps and projection steps.</span></span>

|<span data-ttu-id="243d5-308">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-308">Trainer</span></span>|<span data-ttu-id="243d5-309">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-309">Task</span></span>|<span data-ttu-id="243d5-310">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-310">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LinearSvmTrainer>|<span data-ttu-id="243d5-311">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-311">Binary classification</span></span>|<span data-ttu-id="243d5-312">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-312">Yes</span></span>|

### <a name="local-deep-svm"></a><span data-ttu-id="243d5-313">Глубокий локальный метод опорных векторов</span><span class="sxs-lookup"><span data-stu-id="243d5-313">Local Deep SVM</span></span>

<span data-ttu-id="243d5-314">Прогнозирует целевое значение с использованием модели нелинейной двоичной классификации.</span><span class="sxs-lookup"><span data-stu-id="243d5-314">Predicts a target using a non-linear binary classification model.</span></span> <span data-ttu-id="243d5-315">Сокращает затраты времени на получение прогноза. Затраты при увеличении обучающего набора растут не линейно, а логарифмически, с допустимой потерей точности классификации.</span><span class="sxs-lookup"><span data-stu-id="243d5-315">Reduces the prediction time cost; the prediction cost grows logarithmically with the size of the training set, rather than linearly, with a tolerable loss in classification accuracy.</span></span>

|<span data-ttu-id="243d5-316">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-316">Trainer</span></span>|<span data-ttu-id="243d5-317">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-317">Task</span></span>|<span data-ttu-id="243d5-318">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-318">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.LdSvmTrainer>|<span data-ttu-id="243d5-319">Двоичная классификация</span><span class="sxs-lookup"><span data-stu-id="243d5-319">Binary classification</span></span>|<span data-ttu-id="243d5-320">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-320">Yes</span></span>|

## <a name="ordinary-least-squares"></a><span data-ttu-id="243d5-321">Обычный метод наименьших квадратов</span><span class="sxs-lookup"><span data-stu-id="243d5-321">Ordinary least squares</span></span>

<span data-ttu-id="243d5-322">Обычный метод наименьших квадратов является одним из самых распространенных методов линейной регрессии.</span><span class="sxs-lookup"><span data-stu-id="243d5-322">Ordinary least squares (OLS) is one of the most commonly used techniques in linear regression.</span></span>

<span data-ttu-id="243d5-323">Обычный метод наименьших квадратов ссылается на функцию потерь, которая вычисляет погрешность как сумму квадрата расхождения фактического значения и спрогнозированной линии и подгоняет модель, минимизируя квадратичную погрешность.</span><span class="sxs-lookup"><span data-stu-id="243d5-323">Ordinary least squares refers to the loss function, which computes error as the sum of the square of distance from the actual value to the predicted line, and fits the model by minimizing the squared error.</span></span> <span data-ttu-id="243d5-324">Этот метод предполагает сильную линейную зависимость между входными данными и зависимой переменной.</span><span class="sxs-lookup"><span data-stu-id="243d5-324">This method assumes a strong linear relationship between the inputs and the dependent variable.</span></span>

|<span data-ttu-id="243d5-325">Обучающий алгоритм</span><span class="sxs-lookup"><span data-stu-id="243d5-325">Trainer</span></span>|<span data-ttu-id="243d5-326">Задача</span><span class="sxs-lookup"><span data-stu-id="243d5-326">Task</span></span>|<span data-ttu-id="243d5-327">Экспортируемый в ONNX</span><span class="sxs-lookup"><span data-stu-id="243d5-327">ONNX Exportable</span></span>|
|---------|----------|----------|
|<xref:Microsoft.ML.Trainers.OlsTrainer>|<span data-ttu-id="243d5-328">Регрессия</span><span class="sxs-lookup"><span data-stu-id="243d5-328">Regression</span></span>|<span data-ttu-id="243d5-329">Да</span><span class="sxs-lookup"><span data-stu-id="243d5-329">Yes</span></span>|
