# Комплексное исследование промптинга для LLM: Исследования 2025 + Официальная документация

**Структура документа:**
- **ЧАСТЬ 1**: 8 авторитетных исследований 2025 года с количественными экспериментами и ПРЯМЫМИ ССЫЛКАМИ
- **ЧАСТЬ 2**: Официальная документация LLM платформ (text-based промптинг)
- **ЧАСТЬ 3**: ПРИМЕРЫ ПРОМПТОВ И АНТИПАТТЕРНОВ (явно выделены для LLM обработки)

---

# ЧАСТЬ 1: ИССЛЕДОВАНИЯ ПРОМПТИНГА 2025 ГОДА

## Введение

Список содержит 8 исследований 2025 года, отобранных по критериям:
- ✅ Количественные экспериментальные данные (метрики в %, точность, BLEU, ROUGE)
- ✅ Множественные LLM модели (>3 моделей)
- ✅ Актуальные модели (GPT-4, Claude, Gemini, DeepSeek, LLaMA, Mistral, Qwen)
- ✅ Надёжная методология (human evaluation или валидированные метрики)
- ✅ Год публикации 2025
- ✅ ПРЯМЫЕ ССЫЛКИ на оригинальные работы

---

## 1. EIFBENCH: Extremely Complex Instruction Following Benchmark

**Конференция**: EMNLP 2025 (November 4-9, 2025)  
**Прямая ссылка**: https://aclanthology.org/2025.emnlp-main.1059.pdf  
**Альтернативная ссылка (PDF)**: https://aclanthology.org/2025.emnlp-main.1059.pdf  
**Авторы**: Tao Zou, Xinghua Zhang, Haiyang Yu et al. (Tongyi Lab, Alibaba Group)

### Релевантность
Первый multi-instruction, multi-constraint benchmark (EIFBENCH), отражающий реальную сложность с 74 constraints и 8.24 instructions в среднем. Масштабные количественные результаты для 20+ моделей.

### Ключевые численные результаты

| Модель | Plain Text ILA% / CLA% | Dyadic ILA% / CLA% | Multi-party ILA% / CLA% |
|--------|------------------------|--------------------|-------------------------|
| GPT-4o | 24.80 / 65.18 | 21.66 / 56.31 | 22.26 / 57.86 |
| DeepSeek-R1 | 22.19 / 68.60 | **34.86** / 79.06 | 22.51 / 74.65 |
| Qwen2.5-72B | 19.83 / 75.65 | 27.87 / 76.57 | 26.36 / 83.08 |
| Claude-3.5-Sonnet | 8.96 / 39.51 | 9.19 / 41.42 | 6.63 / 38.65 |

**SegPO алгоритм улучшения (на Qwen2.5-7B):**
- Base → SegPO: **+14.85%** average
- GRPO → SegPO: **+3.40%** average

**Валидация качества:**
- PCC=0.92 (vs. human experts)
- Fleiss' Kappa=0.74 (vs. GPT-4o judge)

---

## 2. In-context Learning vs. Instruction Tuning: The Case of Small and Multilingual Language Models

**Прямая ссылка (arXiv)**: https://arxiv.org/abs/2503.01611  
**PDF на arXiv**: https://arxiv.org/pdf/2503.01611.pdf  
**arXiv ID**: 2503.01611  
**Дата**: 3 марта 2025 (обновлено 17 марта 2025)  
**Авторы**: David Ponce, Thierry Etchegoyhen

### Релевантность
Прямое сравнение ICL vs. instruction fine-tuning с экспериментальными результатами. Многоязычность (English, French, Spanish) важна для валидации универсальности принципов.

### Ключевые численные результаты
- **ICL performance** сильно зависит от размера модели (small models страдают больше)
- **DPO (Direct Preference Optimization)** частично нивелирует эту проблему
- Сравнение accuracy % между языками показывает различия в эффективности

### Новое знание
Для малых моделей instruction tuning часто превосходит ICL, что контрастирует с large models.

---

## 3. Revisiting Prompt Engineering: A Comprehensive Evaluation for LLM-based Personalized Recommendation

**Прямая ссылка (arXiv)**: https://arxiv.org/abs/2507.13525  
**PDF на arXiv**: https://arxiv.org/pdf/2507.13525.pdf  
**arXiv ID**: 2507.13525  
**Дата**: 17 июля 2025  
**Конференция**: ACM RecSys 2025 (reproducibility track)  
**Авторы**: Genki Kusano, Kosuke Akimoto, Kunihiro Takeoka

### Релевантность
Масштабное сравнение 23 prompt types на 8 datasets × 12 LLMs. Статистический rigor с linear mixed-effects models.

### Ключевые численные результаты

**Три наиболее эффективных промпта для budget-conscious моделей:**
1. **Rephrasing** — переформулировка задачи
2. **Background knowledge** — добавление контекста
3. **Reasoning ease** — облегчение процесса рассуждения

**Контринтуитивное открытие:**
- **High-performance LLMs**: простые промпты > сложные
- **Step-by-step reasoning**: часто ведет к ПОНИЖЕНИЮ accuracy (против ожиданий)

### Статистическая валидация
Использованы linear mixed-effects models + p-values для надёжности выводов.

---

## 4. Waking Up an AI: A Quantitative Framework for Prompt-Induced Phase Transition in Large Language Models

**Прямая ссылка (arXiv)**: https://arxiv.org/abs/2504.21012  
**PDF на arXiv**: https://arxiv.org/pdf/2504.21012.pdf  
**arXiv ID**: 2504.21012  
**Дата**: 16 апреля 2025 (обновлено 1 мая 2025)  
**Автор**: Makoto Sato

### Релевантность
Novel методология для измерения когнитивных сдвигов: TIP (Transition-Inducing Prompt) + TQP (Transition Quantifying Prompt). Контролируемые эксперименты с численными результатами.

### Ключевые численные результаты
- Различия в LLM responsiveness между semantically fused vs. non-fused промптами
- **LLM NOT демонстрируют концептуальную интеграцию** как люди (量化эффект)
- Количественный framework для измерения когнитивных фаз

---

## 5. Impact of Prompt Engineering on the Performance of ChatGPT: Comparative Study (GPT-3.5 → GPT-4o)

**Прямая ссылка (NIH PMC)**: https://pmc.ncbi.nlm.nih.gov/articles/PMC12488032/  
**DOI**: 10.7759/cureus.XXXXX (медицинское исследование)  
**Источник**: NIH National Center for Biotechnology Information  
**Дата публикации**: 30 сентября 2025  
**Автор**: Peer-reviewed study в Open Access

### Релевантность
Сравнение 5 версий ChatGPT (GPT-3.5, GPT-4.0, GPT-4o, GPT-4o mini, GPT-4o1) на контролируемом тесте (USMLE медицинские экзамены). Показывает эволюцию эффективности промптинга.

### Ключевые численные результаты

| Модель | Улучшение с промптингом | P-value | Интерпретация |
|--------|--------------------------|---------|--------------|
| GPT-3.5 | **+10.6%** | P<.001 | Высокий эффект |
| GPT-4.0 | **+3.2%** | P=.002 | Умеренный эффект |
| GPT-4o | negligible | P≥.07 | Ceiling effect |
| GPT-4o mini | negligible | P≥.07 | Ceiling effect |
| GPT-4o1 | negligible | P≥.07 | Ceiling effect |

### Практический вывод
**Advanced models обладают "ceiling effect"**: промптинг становится менее критичным по мере роста модели.

---

## 6. AgentIF: Benchmarking Instruction Following in Agentic Scenarios

**Прямая ссылка (arXiv)**: https://arxiv.org/abs/2505.16944  
**PDF на arXiv**: https://arxiv.org/pdf/2505.16944.pdf  
**arXiv ID**: 2505.16944  
**Дата**: май 2025 (submitted 22 May 2025)  
**Авторы**: Yunjia Qi, Hao Peng, Xiaozhi Wang, Amy Xin, Youfeng Liu, Bin Xu, Lei Hou, Juanzi Li (Tsinghua NLP Lab)

### Релевантность
Первый benchmark для evaluation LLM instruction following в реальных agentic scenarios. Реалистичные инструкции от 50 real-world applications, средняя длина 1,723 слов.

### Ключевые численные результаты

| Характеристика | Значение |
|----------------|----------|
| Real-world applications | 50 |
| Mean instruction length | 1,723 words |
| Max instruction length | 15,630 words |
| Constraints per instruction | 11.9 (average) |
| Constraint types | Tool specs, conditions, format, etc. |
| Human annotations | 707 instructions |

**Evaluation методы:**
- Code-based evaluation (автоматическое)
- LLM-based evaluation (GPT-4o judge)
- Hybrid code-LLM evaluation (комбинированное)

**Главный вывод:** Current models generally perform poorly, especially на complex constraint structures и tool specifications.

---

## 7. How Many Instructions Can LLMs Follow at Once? (IFScale)

**Прямая ссылка (arXiv)**: https://arxiv.org/abs/2507.11538  
**PDF на arXiv**: https://arxiv.org/pdf/2507.11538.pdf  
**arXiv ID**: 2507.11538  
**Дата**: 15 июля 2025  
**Авторы**: Daniel Jaroslawicz, Brendan Whiting, Parth Shah, Karime Maamari

### Релевантность
Benchmark для измерения degradation performance при высокой instruction density. 500 keyword-inclusion instructions для business report writing. Практически важно для production systems.

### Ключевые численные результаты

| Параметр | Значение |
|----------|----------|
| Models evaluated | 20 (7 major providers) |
| Instruction range | 10 → 500 instructions |
| Best frontier models @ 500 instr | **68% accuracy** |
| Performance degradation patterns | 3 distinct curves |
| Primacy bias | Strong (earlier instructions prioritized) |

**Модели и providers:**
- OpenAI (GPT-4, GPT-4o)
- Google (Gemini)
- Anthropic (Claude)
- Meta (LLaMA)
- Mistral
- DeepSeek
- Дополнительные провайдеры

**Ошибки по типам:**
1. **Omission** (пропуск инструкции)
2. **Modification** (изменение инструкции)
3. **Misalignment** (неправильное применение)

---

## 8. Scaling Laws for Many-Shot In-Context Learning with Self-Generated Annotations

**Прямая ссылка (arXiv)**: https://arxiv.org/abs/2503.03062  
**PDF на arXiv**: https://arxiv.org/pdf/2503.03062.pdf  
**arXiv ID**: 2503.03062  
**Дата**: 4 марта 2025 (обновлено 20 мая 2025)  
**Авторы**: Zhengyao Gu, Henry Peng Zou, Yankai Chen, Aiwei Liu, Weizhi Zhang, Philip S. Yu

### Релевантность
Исследование scaling laws для ICL с self-generated labels. Показывает, что больше примеров (1000+) может улучшить performance без human annotation.

### Ключевые численные результаты

**Scaling законы для Naive-SemiICL:**
- Zero-shot baseline
- Few-shot (up to 16 examples)
- Many-shot: **optimal performance with 1000+ demonstrations**

**IterPSD (Iterative Pseudo-label Refinement):**
- +6.8% additional gains on classification tasks
- Combines iterative refinement + curriculum pseudo-labeling

**GPT-4o/mini scaling peaks:**
| Task Type | Peak Performance | Example Count |
|-----------|------------------|---------------|
| Classification | ~500-1000 | GPT-4o peak |
| Classification | ~100-200 | GPT-4o-mini peak |
| Translation | ~100-200 | Most models |

**Важное наблюдение:** Naive-SemiICL (простой baseline) outperforms ground-truth ICL даже в many-shot settings, показывая, что self-generation может быть более эффективна чем human labels.

---

## СВОДНАЯ ТАБЛИЦА: 8 ИССЛЕДОВАНИЙ 2025 С ССЫЛКАМИ

| № | Название | Ссылка | Модели | Главный результат | Дата |
|----|----------|--------|--------|------------------|------|
| 1 | EIFBENCH | https://aclanthology.org/2025.emnlp-main.1059.pdf | 20+ | SegPO +14.85% | Nov 2025 |
| 2 | ICL vs. IT | https://arxiv.org/abs/2503.01611 | 10+ | Small: IT > ICL | Mar 2025 |
| 3 | RecSys | https://arxiv.org/abs/2507.13525 | 12 | Complex ↓ quality | Jul 2025 |
| 4 | TIP/TQP | https://arxiv.org/abs/2504.21012 | Mult. | Phase transition | Apr 2025 |
| 5 | ChatGPT | https://pmc.ncbi.nlm.nih.gov/articles/PMC12488032/ | 5 | GPT-3.5: +10.6% | Sep 2025 |
| 6 | AgentIF | https://arxiv.org/abs/2505.16944 | 20+ | 11.9 constraints | May 2025 |
| 7 | IFScale | https://arxiv.org/abs/2507.11538 | 20 | 500 instr: 68% | Jul 2025 |
| 8 | Scaling-ICL | https://arxiv.org/abs/2503.03062 | Mult. | 1000+ demos opt. | Mar 2025 |

---

# ЧАСТЬ 2: ОФИЦИАЛЬНАЯ ДОКУМЕНТАЦИЯ LLM ПЛАТФОРМ (text-based промптинг)

## 1. OpenAI: ChatGPT и GPT-4 официальные рекомендации

### Источники
- https://help.openai.com/en/articles/10032626-prompt-engineering-best-practices-for-chatgpt
- https://platform.openai.com/docs/guides/prompt-engineering
- https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-the-openai-api

### Ключевые рекомендации

#### 1.1 Основные принципы
1. **Ясность и специфичность** — обеспечить достаточный контекст, избежать неоднозначности
2. **Итеративное улучшение** — начать, пересмотреть, уточнить
3. **Контроль тона** — использовать дескриптивные прилагательные (formal, informal, friendly, professional)

#### 1.2 Структура промпта (Best Practice)
Использовать разделители (`###` или `"""`) для организации:

```
### Instruction ###
[ваша детальная инструкция]

### Context ###
[релевантная информация]

### Input ###
[вопрос пользователя]
```

#### 1.3 Разделение входных данных
- **system** параграф: высокоуровневые инструкции, behavior, tone
- **user** параграф: специфичные инструкции для текущего запроса

**Приоритет**: `instructions` parameter > `input` parameter

#### 1.4 API параметры для контроля
- **Model**: использовать latest (они проще в промптинге)
- **Temperature**: 0 (детерминировано) → 1 (творчески)
- **Max_tokens**: контролировать длину ответа
- **Stop sequences**: указать, где остановиться

---

## 2. Google: Gemini API Official Prompting Strategies

### Источники
- https://ai.google.dev/gemini-api/docs/prompting-strategies
- https://workspace.google.com/learning/content/gemini-prompt-guide
- https://cloud.google.com/gemini-enterprise/resources/prompt-guide

### Ключевые рекомендации

#### 2.1 Core Prompting Principles (Gemini 3)
1. **Точность и прямота** — явно указать цель, избежать лишних убеждающих слов
2. **Konsistent structure** — использовать XML теги (`<context>`, `<task>`, `<role>`, `<constraints>`, `<output_format>`)
3. **Определение параметров** — явно объяснить амбигу термины и ограничения
4. **Контроль многословности** — Gemini 3 обеспечивает прямые ответы по default
5. **Приоритизация критичных инструкций** — поместить в system prompt или начало user prompt

#### 2.2 Структурированный template (Gemini 3)

**System Instruction:**
```xml
<role>
You are Gemini 3, specialized assistant for [Domain].
You are precise, analytical, and persistent.
</role>

<instructions>
1. **Plan**: Analyze and create step-by-step plan.
2. **Execute**: Carry out the plan.
3. **Validate**: Review against user requirements.
4. **Format**: Present in requested structure.
</instructions>

<constraints>
- Verbosity: [Low/Medium/High]
- Tone: [Formal/Casual/Technical]
</constraints>
```

**User Prompt:**
```xml
<context>
[Documents, code, background info]
</context>

<task>
[Specific user request]
</task>

<final_instruction>
Think step-by-step before answering.
</final_instruction>
```

#### 2.3 Zero-shot vs. Few-shot
**Рекомендация Google**: всегда включать few-shot примеры (более эффективно).
- **Optimal number**: начать с 2-3 примеров
- Few-shot регулирует форматирование, формулировку, scope, паттерны

#### 2.4 Дополнительные стратегии
- **Break down instructions** — по одному промпту на инструкцию
- **Chain prompts** — вывод одного = вход другого (для multi-step)
- **Aggregation** — параллельная обработка, затем объединение
- **Fallback responses** — если ошибка, увеличить temperature

---

## 3. Anthropic: Claude 4.x Prompting Best Practices

### Источники
- https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/prompt-improver
- https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-4-best-practices

### Ключевые рекомендации

#### 3.1 Claude 4.x особенности
1. **Точное следование инструкциям** — чувствителен к деталям и примерам
2. **Примеры должны совпадать** с желаемым поведением
3. **Минимизировать антипаттерны** — показать ДО-ПОСЛЕ, где ДО = плохо
4. **Мотивация в инструкциях** — объяснить ЧТО и ПОЧЕМУ (Claude обобщает логику)

#### 3.2 Направление вместо запрета
```
❌ НЕПРАВИЛЬНО: "Don't be verbose"
✅ ПРАВИЛЬНО: "Be concise and direct"

❌ НЕПРАВИЛЬНО: "Avoid markdown"
✅ ПРАВИЛЬНО: "Write in clear, flowing prose without excessive markdown"
```

#### 3.3 System Prompt Responsiveness (Claude 4.5)
- Claude 4.5 чувствителен к system prompt
- Если использовались aggressive instructions ("You MUST..."), смягчить до обычных ("Use this when...")

#### 3.4 Output formatting
- Используемые XML tags для структуры
- Preferredный flowing prose вместо bullet points
- Reserve markdown для inline code и code blocks

---

## 4. Meta: LLaMA 3.1 Prompting Best Practices

### Источники
- https://www.llama.com/docs/how-to-guides/prompting/
- https://www.llama.com/docs/model-cards-and-prompt-formats/llama3_1/
- https://aws.amazon.com/blogs/machine-learning/best-prompting-practices-for-using-meta-llama-3-with-amazon-sagemaker-jumpstart/

### Ключевые рекомендации

#### 4.1 Prompt Format для LLaMA-3 Instruct

**Специальные токены:**
```
<|begin_of_text|><|start_header_id|>system<|end_header_id|>
[system message]<|eot_id|><|start_header_id|>user<|end_header_id|>
[user message]<|eot_id|><|start_header_id|>assistant<|end_header_id|>
[assistant message]<|eot_id|>
```

#### 4.2 Лучшие практики
1. **Ясность и специфичность** — явные инструкции
2. **Понимание различий моделей** — каждая обучена по-разному
3. **Использование примеров** — few-shot особенно полезно для сложных задач
4. **Явные требования** — LLaMA-3 может быть более чувствителен к формулировке

#### 4.3 Inference параметры
- **Temperature**: 0-1
- **Top-k**: number of top candidates
- **Top-p**: cumulative probability
- **Stop sequences**: `<|start_header_id|>`, `<|end_header_id|>`, `<|eot_id|>`

---

## 5. Mistral AI: Official Prompting Capabilities

### Источники
- https://docs.mistral.ai/capabilities/completion/prompting_capabilities
- https://docs.mistral.ai/cookbooks/mistral-prompting-prompting_capabilities

### Ключевые рекомендации

#### 5.1 Chat Template для Mistral-7B-Instruct
```
<s>[INST] Instruction [/INST] Model answer</s>[INST] Follow-up [/INST]
```

#### 5.2 System и User Messages
1. **System prompt** — начало conversation, общий контекст
2. **User prompt** — специфичный контекст для текущего interaction

#### 5.3 Roleplay / Purpose assignment
**Простая техника:**
```
You are a [role], your task is to [task].

Пример:
You are a Python developer. Your task is to write clean, efficient code.
```

#### 5.4 Few-shot Learning / In-context Learning
- **Facts provision** для customer support bots
- **JSON output**: `response_format = {"type": "json_object"}`
- **Higher temperature** (0.7-0.9) для творческих outputs

---

## 6. DeepSeek: Prompt Engineering Guidance

### Источники
- https://api-docs.deepseek.com
- https://docs.together.ai/docs/prompting-deepseek-r1
- https://mydeepseekapi.com/blog/deepseek-r1-system-prompt-guide

### Ключевые рекомендации

#### 6.1 Базовые принципы
1. **Четкие и специфичные промпты** — plain language, избегать длинных complex промптов
2. **Sampling parameters**:
   - Temperature: 0.5-0.7 (рекомендуется 0.6)
   - Top-p: 0.95 (prevent repetitions)
3. **NO system prompt** — все инструкции в user prompt (DeepSeek R1 особенность!)
4. **NO few-shot для R1** — примеры деградируют performance!

#### 6.2 Структурирование промпта
1. **Четкие маркеры** для разных частей:
   - XML tags: `<problem>`, `<task>`, `<output_format>`
   - Markdown formatting
   - Labeled sections

2. **Set clear requirements** — явные limitations и criteria

#### 6.3 System Prompt Structure (если нужен)
```json
{
  "role": "system",
  "content": "You are a backend developer expert in Python, Docker, AWS..."
}
```

**Best practices:**
1. Explicit about expertise, не просто "Be helpful"
2. Limit ambiguity
3. Chain-of-Thought для complex tasks

---

## 7. ИНТЕГРАТИВНЫЙ ОБЗОР: Лучшие практики по платформам

### Сравнительная таблица

| Аспект | OpenAI | Gemini | Claude | LLaMA | Mistral | DeepSeek |
|--------|--------|--------|---------|-------|---------|----------|
| **System prompt** | ✅ Да | ✅ Да | ✅ Да | ✅ Да | ✅ Да | ❌ Нет (R1) |
| **Few-shot примеры** | ✅ Рек. | ✅ Рек. | ✅ Рек. | ✅ Исп. | ✅ Да | ❌ Деградирует |
| **XML структуры** | Опционально | ✅ Рек. | ✅ Рек. | ❌ Нет | Опционально | Опционально |
| **Специальные токены** | Нет | Нет | Нет | ✅ Обязательно | ✅ [INST] | Нет |
| **Chain-of-Thought** | ✅ "think step by step" | ✅ "Plan-Execute" | ✅ Примеры | ✅ Явно | ✅ Да | ✅ Встроенный |
| **Temperature рек.** | 0-1 (зав.) | 1.0 (Gemini 3) | 0-1 (зав.) | 0-1 | 0.7 | 0.6 |

### Универсальные лучшие практики (ВСЕ платформы)

1. ✅ **Ясность и специфичность**
2. ✅ **Структурированный формат** (XML, markdown, labeled sections)
3. ✅ **Явные требования и constraints**
4. ✅ **Примеры** (кроме DeepSeek R1)
5. ✅ **Итеративное улучшение**
6. ✅ **Контроль параметров** (temperature, max_tokens, stop_sequences)

---

# ЧАСТЬ 3: ПРИМЕРЫ ПРОМПТОВ И АНТИПАТТЕРНОВ

## ⚠️ НАЧАЛО БЛОКА ПРИМЕРОВ И АНТИПАТТЕРНОВ

### Этот раздел содержит конкретные примеры промптов, отделённые маркерами:
- ✅ `[GOOD EXAMPLE]` — правильный пример промпта
- ❌ `[BAD EXAMPLE / ANTIPATTERN]` — неправильный пример, что избегать

---

## Категория 1: Простые информационные запросы (QA)

### ✅ GOOD EXAMPLE 1.1: Информационный вопрос с контекстом

```
[GOOD EXAMPLE START]

### Instruction ###
Answer the question based only on the provided context. Be concise and factual.

### Context ###
The Python programming language was created by Guido van Rossum and first released in 1991. 
It emphasizes code readability and simplicity, making it popular for beginners and professionals alike.

### Question ###
When was Python created and who created it?

### Expected Output ###
Python was created by Guido van Rossum and first released in 1991.

[GOOD EXAMPLE END]
```

**Почему это хорошо:**
- Явная структура (Instruction/Context/Question)
- Ограничение scope ("based only on provided context")
- Требование к стилю ("Be concise and factual")
- Ожидаемый вывод показывает формат

---

### ❌ BAD EXAMPLE 1.1: Неструктурированный запрос

```
[BAD EXAMPLE / ANTIPATTERN START]

When was Python created?

[BAD EXAMPLE / ANTIPATTERN END]
```

**Почему это плохо:**
- Отсутствует контекст
- Нет явных требований
- Неопределённый формат ответа (может быть слишком длинный)
- Model может галлюцинировать факты

---

## Категория 2: Классификация и категоризация

### ✅ GOOD EXAMPLE 2.1: Классификация с четкими категориями

```
[GOOD EXAMPLE START]

### Instruction ###
Classify the following customer feedback into one of these categories:
- Positive (satisfied with product/service)
- Negative (unsatisfied, complaints)
- Neutral (factual feedback, no strong emotion)

Return ONLY the category name, nothing else.

### Input ###
"The delivery was fast, but the product quality could be better."

### Expected Output ###
Neutral

[GOOD EXAMPLE END]
```

**Почему это хорошо:**
- Четко определены категории
- Output primer ("Return ONLY the category name")
- Явное требование к формату
- Пример ожидаемого результата

---

### ❌ BAD EXAMPLE 2.1: Неясные категории, многословный ответ

```
[BAD EXAMPLE / ANTIPATTERN START]

### Instruction ###
How would you rate this feedback?

### Input ###
"The delivery was fast, but the product quality could be better."

### Expected Output ###
Mixed sentiments detected: positive aspect (fast delivery) combined with 
negative aspect (quality concerns). The overall sentiment leans slightly 
toward neutral...

[BAD EXAMPLE / ANTIPATTERN END]
```

**Почему это плохо:**
- "How would you rate" — неопределённая инструкция (rate как? по какой шкале?)
- Нет явных требований к формату
- Model генерирует длинный многословный ответ вместо simple classification
- Нет контроля над выводом

---

## Категория 3: Сложное рассуждение (Complex Reasoning)

### ✅ GOOD EXAMPLE 3.1: Chain-of-Thought для математики

```
[GOOD EXAMPLE START]

### Instruction ###
Solve this math problem step-by-step. Show your work clearly at each step.

### Problem ###
A store sells apples at $2 per pound. Sarah buys 3 pounds and pays with a $20 bill. 
How much change does she receive?

### Solution Format ###
Step 1: [Identify what we know]
Step 2: [Calculate total cost]
Step 3: [Calculate change]
Final Answer: [Answer in dollars]

### Expected Output ###
Step 1: Identify: apples = $2/lb, Sarah buys 3 lbs, pays with $20
Step 2: Total cost = $2 × 3 = $6
Step 3: Change = $20 - $6 = $14
Final Answer: $14

[GOOD EXAMPLE END]
```

**Почему это хорошо:**
- Chain-of-Thought структура (step-by-step)
- Explicit format specification
- Пример показывает желаемый процесс
- Clear expected output

---

### ❌ BAD EXAMPLE 3.1: Просто вопрос без структуры

```
[BAD EXAMPLE / ANTIPATTERN START]

### Instruction ###
A store sells apples at $2 per pound. Sarah buys 3 pounds and pays with a $20 bill. 
How much change does she receive?

[BAD EXAMPLE / ANTIPATTERN END]
```

**Почему это плохо:**
- Нет явного требования step-by-step рассуждения
- Model может просто дать ответ без работы
- Невозможно проверить процесс логики
- Риск ошибок выше без явного структурирования

---

## Категория 4: Генерирование контента (Creativity + Structure)

### ✅ GOOD EXAMPLE 4.1: Генерирование с роль и constraints

```
[GOOD EXAMPLE START]

### Role ###
You are a professional copywriter specializing in tech product marketing.

### Task ###
Write a product description for a new productivity app.

### Constraints ###
- Length: 150-200 words
- Tone: Engaging but professional
- Include: 2-3 key benefits
- Avoid: Clichés like "game-changer" or "revolutionary"
- Format: Paragraph format, not bullet points

### Key Features ###
- AI-powered task prioritization
- Real-time team collaboration
- Integration with 50+ tools

### Example Style (what we want) ###
"Designed for teams that move fast, this app intelligently prioritizes your 
work and keeps everyone aligned. With real-time collaboration features and 
seamless integrations, you spend less time organizing and more time building."

[GOOD EXAMPLE END]
```

**Почему это хорошо:**
- Явная роль (role assignment)
- Clear constraints (length, tone, avoid)
- Specific features provided
- Example style shows desired tone
- Detailed output format

---

### ❌ BAD EXAMPLE 4.1: Vague instruction, no constraints

```
[BAD EXAMPLE / ANTIPATTERN START]

### Instruction ###
Write a description for our new app. Make it good.

[BAD EXAMPLE / ANTIPATTERN END]
```

**Почему это плохо:**
- "Make it good" — субъективное, неясное требование
- Нет constraints (длина, тон, стиль)
- Нет примеров
- Model может генерировать anything (может быть слишком длинный, неправильный тон и т.д.)

---

## Категория 5: Code Generation

### ✅ GOOD EXAMPLE 5.1: Код с контекстом и требованиями

```
[GOOD EXAMPLE START]

### Instruction ###
Write a Python function to validate email addresses.

### Requirements ###
1. Function name: validate_email
2. Input: email_string (str)
3. Output: True if valid, False otherwise
4. Validation rules:
   - Must contain exactly one '@'
   - Must have domain name after '@'
   - Domain must contain at least one '.'
5. No external libraries (use regex only)

### Example Usage ###
validate_email("user@example.com")  # → True
validate_email("invalid@.com")      # → False
validate_email("invalid.com")       # → False

### Code Template ###
import re

def validate_email(email_string):
    """
    Validate email address format.
    """
    # Your implementation here
    pass

[GOOD EXAMPLE END]
```

**Почему это хорошо:**
- Четкие требования
- Specification constraints
- Примеры usage (expected behavior)
- Template для следования
- Clear input/output contract

---

### ❌ BAD EXAMPLE 5.1: Расплывчатая просьба о коде

```
[BAD EXAMPLE / ANTIPATTERN START]

### Instruction ###
Write code to check if an email is valid.

[BAD EXAMPLE / ANTIPATTERN END]
```

**Почему это плохо:**
- "Valid" — неопределённо (какие правила валидации?)
- Нет языка указано (может быть Python, Java, JavaScript и т.д.)
- Нет примеров
- Model может использовать external libraries или регулярные выражения неправильно
- Uncertainty in requirements

---

## Категория 6: Форматирование и структурирование

### ✅ GOOD EXAMPLE 6.1: JSON Output с явным format specification

```
[GOOD EXAMPLE START]

### Instruction ###
Extract information about books from the provided text and return as JSON.

### Format ###
Return a JSON array with this exact structure:
{
  "books": [
    {
      "title": "string",
      "author": "string",
      "year": "number",
      "genre": "string"
    }
  ]
}

### Input Text ###
"The Great Gatsby by F. Scott Fitzgerald was published in 1925 and is considered 
a masterpiece of American fiction. Another classic, 1984 by George Orwell, was 
published in 1949 and is a dystopian novel."

### Expected Output ###
{
  "books": [
    {
      "title": "The Great Gatsby",
      "author": "F. Scott Fitzgerald",
      "year": 1925,
      "genre": "Fiction"
    },
    {
      "title": "1984",
      "author": "George Orwell",
      "year": 1949,
      "genre": "Dystopian"
    }
  ]
}

[GOOD EXAMPLE END]
```

**Почему это хорошо:**
- Explicit format specification (JSON schema)
- Fields defined precisely
- Expected output shown
- Data types specified (string, number)
- Parser-friendly format

---

### ❌ BAD EXAMPLE 6.1: Нечеткое требование к формату

```
[BAD EXAMPLE / ANTIPATTERN START]

### Instruction ###
Tell me about the books in this text.

### Input Text ###
"The Great Gatsby by F. Scott Fitzgerald was published in 1925. 
1984 by George Orwell was published in 1949."

### Expected Output ###
The Great Gatsby - by Fitzgerald - 1925
1984 - Orwell - 1949

[BAD EXAMPLE / ANTIPATTERN END]
```

**Почему это плохо:**
- "Tell me about" — неопределённое требование
- Формат не специфицирован (почему dashes? почему этот порядок?)
- Может быть нераспарсиваемым для автоматической обработки
- Неясно, должна ли быть пополняющая информация

---

## Категория 7: Что избегать (ANTIPATTERNS)

### ❌ ANTIPATTERN 7.1: "Don't" вместо "Do"

```
[BAD EXAMPLE / ANTIPATTERN START]

### Instruction ###
Write a product review. Don't be verbose. Don't use complicated words. 
Don't mention price. Don't be too positive.

[BAD EXAMPLE / ANTIPATTERN END]
```

**Почему это плохо:**
- Множество "don't" confuses models
- Лучше указать что ДЕЛАТЬ

**Как исправить:**
```
[GOOD EXAMPLE START]

### Instruction ###
Write a concise product review (max 150 words).
Use simple, clear language that anyone can understand.
Focus on product quality and functionality, not price.
Include both strengths and areas for improvement.

[GOOD EXAMPLE END]
```

---

### ❌ ANTIPATTERN 7.2: Слишком вежливые инструкции (для professional tasks)

```
[BAD EXAMPLE / ANTIPATTERN START]

### Instruction ###
Would you please mind terribly if you could perhaps consider categorizing 
these emails, if that's not too much trouble? It would be lovely if you could 
sort them by priority when you have a moment.

[BAD EXAMPLE / ANTIPATTERN END]
```

**Почему это плохо:**
- Чрезмерная вежливость confuses intent
- Model может не понять что действительно требуется
- Для technical tasks: be direct

**Как исправить:**
```
[GOOD EXAMPLE START]

### Instruction ###
Categorize the following emails by priority: High, Medium, Low.
Base priority on urgency indicators and business impact.
Return categories only.

[GOOD EXAMPLE END]
```

---

### ❌ ANTIPATTERN 7.3: Смешивание нескольких задач в один промпт

```
[BAD EXAMPLE / ANTIPATTERN START]

### Instruction ###
Read this customer email, translate it to Spanish, summarize it in bullet points, 
classify sentiment, extract entities, and then generate a response.

[Input: long customer email]

[BAD EXAMPLE / ANTIPATTERN END]
```

**Почему это плохо:**
- Слишком много tasks одновременно
- Quality degrades при multi-tasking
- Difficult to evaluate individual components

**Как исправить:**
```
[GOOD EXAMPLE START]

# Task 1: Sentiment Classification
### Instruction ###
Classify the sentiment of this email: Positive, Negative, or Neutral.
Return only the classification.

[Input]

---

# Task 2: Entity Extraction
### Instruction ###
Extract names, dates, and product mentions from this email.
Format as JSON: {"names": [], "dates": [], "products": []}

[Input]

---

# Task 3: Generate Response
### Instruction ###
Write a professional response to this customer email.
Keep it under 200 words.
Address their main concerns.

[Input]

[GOOD EXAMPLE END]
```

---

### ❌ ANTIPATTERN 7.4: Недостаточный контекст

```
[BAD EXAMPLE / ANTIPATTERN START]

### Instruction ###
Translate this to French.

### Input ###
"It was a pleasure to help."

[BAD EXAMPLE / ANTIPATTERN END]
```

**Почему это плохо:**
- Нет контекста (formal/informal? technical? literary?)
- "Pleasure" может перевестись несколькими способами
- Model может выбрать неправильный стиль

**Как исправить:**
```
[GOOD EXAMPLE START]

### Instruction ###
Translate this to French. Maintain formal, professional business tone.

### Context ###
This is part of a formal business email response.

### Input ###
"It was a pleasure to help."

### Expected Output ###
"Cela a été un plaisir de vous aider." (or similar formal expression)

[GOOD EXAMPLE END]
```

---

### ❌ ANTIPATTERN 7.5: Неполные или противоречивые инструкции

```
[BAD EXAMPLE / ANTIPATTERN START]

### Instruction ###
Write a short, detailed product description that is concise but comprehensive 
and includes everything important but stays brief.

[BAD EXAMPLE / ANTIPATTERN END]
```

**Почему это плохо:**
- "short" vs "detailed" — противоречие
- "concise" vs "comprehensive" — противоречие
- Model confuses about priorities

**Как исправить:**
```
[GOOD EXAMPLE START]

### Instruction ###
Write a product description (200-250 words).
Prioritize: (1) Key benefits, (2) Target audience, (3) Unique features.
Omit: price, company history, detailed specifications.
Tone: Professional but approachable.

[GOOD EXAMPLE END]
```

---

## Категория 8: Примеры для разных LLM платформ

### ✅ GOOD EXAMPLE 8.1: OpenAI GPT-4

```
[GOOD EXAMPLE START]

{
  "model": "gpt-4o",
  "messages": [
    {
      "role": "system",
      "content": "You are a data analyst. Provide insights in clear, actionable language."
    },
    {
      "role": "user",
      "content": "### Data ###\n[Dataset]\n\n### Task ###\nIdentify top 3 trends.\n\n### Format ###\n1. [Trend]: [Insight with numbers]\n2. ..."
    }
  ],
  "temperature": 0.5,
  "max_tokens": 500
}

[GOOD EXAMPLE END]
```

---

### ✅ GOOD EXAMPLE 8.2: Claude (Anthropic)

```
[GOOD EXAMPLE START]

### Instruction ###
You are a senior software architect. Your task is to review this code design.

### Code Design ###
[Design description]

### Evaluation Criteria ###
1. Scalability
2. Maintainability
3. Security

### Format ###
Provide structured feedback for each criterion.
Start with a brief summary (2-3 sentences).
Then detailed recommendations for each criterion.

[GOOD EXAMPLE END]
```

---

### ✅ GOOD EXAMPLE 8.3: Gemini (Google)

```
[GOOD EXAMPLE START]

<role>
You are a Python expert. You write efficient, well-documented code.
</role>

<task>
Write a function to compute Fibonacci numbers efficiently.
</task>

<constraints>
- Use memoization for optimization
- Include docstring
- Handle edge cases (n < 0)
- Time complexity: O(n)
</constraints>

<output_format>
Return Python code with inline comments explaining logic.
</output_format>

[GOOD EXAMPLE END]
```

---

### ✅ GOOD EXAMPLE 8.4: DeepSeek (NO few-shot, NO system prompt)

```
[GOOD EXAMPLE START]

You are a machine learning researcher specializing in NLP.

<task>
Explain how attention mechanisms work in transformer models.
</task>

<output_format>
Clear explanation with:
1. Core concept
2. Mathematical intuition
3. Practical example with numbers
4. Why it's better than alternatives
</output_format>

Keep explanation technical but understandable to graduate students.

[GOOD EXAMPLE END]
```

---

## ⚠️ КОНЕЦ БЛОКА ПРИМЕРОВ И АНТИПАТТЕРНОВ

### Итоговые рекомендации для всех платформ:

1. **Структура**: всегда используйте ### или <> tags
2. **Четкость**: избегайте двусмысленности и противоречий
3. **Do's, not Don'ts**: говорите что ДЕЛАТЬ, не что избегать
4. **Примеры**: покажите ожидаемый вывод
5. **Constraints**: явно ограничивайте scope (длина, формат, тон)
6. **Format specification**: для structured outputs используйте JSON или явный format
7. **Roleplaying**: assign role для consistency
8. **Iterative**: улучшайте промпт на основе результатов

---

**Финальный документ подготовлен**: январь 2026  
**Покрытие**: 8 исследований + 6 LLM платформ + примеры + антипаттерны  
**Статус**: Полная компиляция официальной документации и текущих исследований  
**Прямые ссылки**: Все исследования имеют прямые ссылки на оригинальные работы  
