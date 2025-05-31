### ✅ **انواع وظایف (Tasks) که مدل‌های زبانی بزرگ (LLMs) می‌توانند انجام دهند**

مدل‌های زبانی پیشرفته مانند **BERT، T5، GPT، BART** و غیره قادر به انجام انواع مختلفی از وظایف در حوزه **پردازش زبان طبیعی (NLP)** هستند. این وظایف را می‌توان بر اساس نوع خروجی، ساختار ورودی یا نوع داده به دسته‌های مختلف تقسیم کرد.

---

## 📌 **۱. دسته‌بندی وظایف NLP**

### الف) **بر اساس نوع وظیفه**
| نوع | توضیح |
|------|--------|
| **Token-level tasks** | پیش‌بینی روی هر توکن (کلمه/زیرکلمه) مانند NER، POS Tagging |
| **Sentence-level tasks** | پیش‌بینی کل جمله یا یک بخش از آن مانند طبقه‌بندی جمله |
| **Sentence-pair tasks** | رابطه بین دو جمله مانند Natural Language Inference، Paraphrase Detection |
| **Sequence-to-sequence tasks** | تبدیل یک متن به متن دیگر مانند ترجمه، خلاصه‌سازی |

---

### ب) **بر اساس نوع خروجی**
| نوع | توضیح | مثال |
|------|--------|-------|
| **Classification** | طبقه‌بندی جمله یا توکن | Sentiment Analysis، NER |
| **Regression** | پیش‌بینی عددی | شباهت دو جمله (STS-B) |
| **Text Generation** | تولید متن | ترجمه، خلاصه‌سازی، پاسخ‌دهی به سؤال |
| **Span Prediction** | پیش‌بینی قسمتی از متن | Question Answering (SQuAD) |
| **Multiple Choice** | انتخاب گزینه مناسب از چند گزینه | SWAG، HellaSwag |

---

### ج) **بر اساس نوع مدل**
| مدل | وظایف مناسب |
|------|------------------|
| **Encoder-only (BERT)** | Classification، NER، QA |
| **Decoder-only (GPT)** | Text Generation، Completion |
| **Encoder-Decoder (T5, BART)** | Translation، Summarization، QA، Rewriting |

---

## 🧠 **۲. وظایف شناخته شده و معروف در حوزه NLP**

### 🔹 **الف) Sentence-level Tasks**
#### 1. **Sentiment Analysis (SA)**
- **توضیح:** تشخیص نظر مثبت/منفی/خنثی
- **مثال:**
  ```
  Input: This movie was terrible.
  Output: negative
  ```

#### 2. **Natural Language Inference (NLI)**
- **توضیح:** تعیین رابطه دو جمله (entailment، contradiction، neutral)
- **مثال:**
  ```
  Premise: A man is walking his dog.
  Hypothesis: The man owns a pet.
  Output: entailment
  ```

#### 3. **Paraphrase Detection**
- **توضیح:** آیا دو جمله معنای یکسانی دارند؟
- **مثال:**
  ```
  Sentence1: The cat is on the mat.
  Sentence2: There's a cat sitting on the rug.
  Output: yes
  ```

#### 4. **Acceptability Judgment**
- **توضیح:** آیا جمله از لحاظ نحوی درست است؟
- **مثال:**
  ```
  Input: He go to school yesterday.
  Output: unacceptable
  ```

#### 5. **Question Answering (QA)**
- **توضیح:** یافتن پاسخ به سؤال از یک متن
- **مثال:**
  ```
  Context: Paris is the capital of France.
  Question: What is the capital of France?
  Output: Paris
  ```

#### 6. **Coreference Resolution**
- **توضیح:** تشخیص اینکه دو اسم یا ضمیر به چه چیزی اشاره می‌کنند
- **مثال:**
  ```
  John told Mary he would come. → "he" refers to John
  ```

#### 7. **Textual Entailment**
- **توضیح:** آیا جمله اول شامل جمله دوم است؟
- **مثال:**
  ```
  Sentence1: The car is red.
  Sentence2: The car has color.
  Output: yes
  ```

---

### 🔹 **ب) Token-level Tasks**
#### 1. **Part-of-Speech (POS) Tagging**
- **توضیح:** برچسب‌گذاری کلمات با نقش دستوری (اسم، فعل، ...)
- **مثال:**
  ```
  Input: The quick brown fox jumps over the lazy dog.
  Output: DET ADJ ADJ NOUN VERB ADP DET ADJ NOUN
  ```

#### 2. **Named Entity Recognition (NER)**
- **توضیح:** تشخیص موجودیت‌های خاص (شخص، مکان، سازمان و ...)
- **مثال:**
  ```
  Input: Google was founded by Larry Page and Sergey Brin.
  Output: [ORG Google] was founded by [PER Larry Page] and [PER Sergey Brin].
  ```

#### 3. **Chunking**
- **توضیح:** تقسیم جمله به بخش‌های معنایی
- **مثال:**
  ```
  Input: The quick brown fox jumps over the lazy dog.
  Output: [NP The quick brown fox] [VP jumps over] [NP the lazy dog]
  ```

---

### 🔹 **ج) Sequence-to-Sequence Tasks**
#### 1. **Machine Translation (MT)**
- **توضیح:** ترجمه یک متن به زبان دیگر
- **مثال:**
  ```
  Input (English): The cat is on the mat.
  Output (French): Le chat est sur le tapis.
  ```

#### 2. **Abstractive Summarization**
- **توضیح:** خلاصه‌سازی متن با تولید جملات جدید
- **مثال:**
  ```
  Input: State authorities dispatched emergency crews after a storm hospitalized six people in rural county.
  Output: Six people hospitalized after storm.
  ```

#### 3. **Dialogue Systems**
- **توضیح:** مدیریت گفت‌وگو با کاربر
- **مثال:**
  ```
  User: What's the weather like today?
  Model: It's sunny with a high of 25°C.
  ```

#### 4. **Text Simplification**
- **توضیح:** ساده‌سازی متن برای درک بهتر
- **مثال:**
  ```
  Input: The phenomenon of climate change is causing global warming.
  Output: Climate change makes Earth warmer.
  ```

#### 5. **Text Generation**
- **توضیق:** تولید متن جدید از روی prompt
- **مثال:**
  ```
  Prompt: Write a story about space exploration.
  Output: Once upon a time, astronauts discovered a new galaxy...
  ```

---

### 🔹 **د) Multi-modal Tasks**
#### 1. **Image Captioning**
- **توضیح:** توصیف تصویر با جمله
- **مثال:**
  ```
  Image: A woman riding a bike.
  Output: A woman is riding a bicycle outside.
  ```

#### 2. **Visual Question Answering (VQA)**
- **توضیح:** پاسخ به سؤال مرتبط با تصویر
- **مثال:**
  ```
  Image: A dog playing with a ball.
  Question: What is the animal doing?
  Output: Playing
  ```

#### 3. **Speech-to-Text / Text-to-Speech**
- **توضیح:** تبدیل صوت به متن و بالعکس

---

## 📊 **۳. مجموعه داده‌های معروف برای ارزیابی وظایف NLP**

| مجموعه داده | نوع وظیفه | توضیح |
|-------------|------------|---------|
| **GLUE Benchmark** | Classification، NLI، Similarity | شامل 9 وظیفه استاندارد مثل SST-2، MNLI، MRPC |
| **SuperGLUE** | Classification، QA، Reasoning | وظایف سخت‌تر از GLUE |
| **SQuAD** | Question Answering | پاسخ‌دهی به سؤال از متن |
| **CoNLL-2003** | Named Entity Recognition | تشخیص موجودیت‌های نام‌گذاری شده |
| **CNN/DM** | Summarization | خلاصه‌سازی اخبار |
| **WMT** | Machine Translation | ترجمه ماشینی |
| **BoolQ** | Question Answering | سؤالات بله/خیر |
| **WiC** | Word-in-Context | آیا یک کلمه در دو جمله یکسان استفاده شده؟ |

---

## 🎯 **۴. مقایسه قابلیت‌های مدل‌ها در انجام وظایف**

| مدل | Classification | NLI | QA | Translation | Summarization | Few-shot | Zero-shot |
|-----|----------------|-----|----|-------------|---------------|----------|-----------|
| **BERT** | ✅ عالی | ✅ عالی | ✅ عالی | ❌ | ❌ | ❌ | ❌ |
| **RoBERTa** | ✅ عالی | ✅ عالی | ✅ عالی | ❌ | ❌ | ❌ | ❌ |
| **GPT-3** | ✅ خوب | ✅ خوب | ✅ خوب | ✅ خوب | ✅ خوب | ✅ بسیار خوب | ✅ بسیار خوب |
| **T5** | ✅ خوب | ✅ خوب | ✅ خوب | ✅ خوب | ✅ خوب | ✅ خوب | ✅ خوب |
| **BART** | ✅ خوب | ✅ خوب | ✅ خوب | ✅ خوب | ✅ عالی | ✅ خوب | ✅ خوب |
| **Prompt-based models** | ✅ خوب | ✅ خوب | ✅ خوب | ✅ خوب | ✅ خوب | ✅ خوب | ✅ خوب |

---

## 🧪 **۵. وظایف بر اساس روش حل (Prompt-based vs Full FT)**

### الف) **Prompt-based Learning**
- بدون fine-tuning کامل
- تنها با طراحی دقیق prompt و label words
- مناسب برای:
  - وظایف classification (SST-2، CoLA)
  - NLI (MNLI، RTE)
  - Question Answering (SQuAD)
  - Paraphrase Detection (MRPC)

### ب) **Full Fine-tuning**
- تمام پارامترهای مدل به‌روزرسانی می‌شوند
- مناسب برای:
  - وظایف پیچیده با داده فراوان
  - وظایف generation (ترجمه، خلاصه‌سازی)
  - وظایف token-level (NER، POS)

---

## 🧩 **۶. چطور یک وظیفه را به صورت Prompt-based فرمول‌بندی کنیم؟**

### مرحله ۱: **فرمول‌بندی وظیفه با Template**
```
[Sentence] It was [MASK].
```

### مرحله ۲: **انتخاب Label Words**
```
[MASK] = great → positive  
[MASK] = terrible → negative
```

### مرحله ۳: **استفاده از مدل برای پیش‌بینی**
- مدل احتمال هر کلمه را محاسبه می‌کند.
- کلمه با بیشترین احتمال در label words انتخاب می‌شود.

---

## 📈 **۷. عملکرد مدل‌ها در وظایف مختلف (با داده کم و زیاد)**

### با داده کم (Few-shot)
| روش | SST-2 | CoLA | RTE | MRPC |
|------|-------|------|-----|------|
| **Prompt-based Zero-shot** | 83.6% | 32.0% | 51.3% | 61.9% |
| **Prompt-based Few-shot** | 92.7% | 91.2% | 69.1% | 74.5% |
| **Full Fine-tuning** | 95.0% | 97.0% | 80.9% | 91.4% |

### با داده زیاد (Full Data)
| روش | SST-2 | CoLA | RTE | MRPC |
|------|-------|------|-----|------|
| **Prompt-based** | ~85% | ~80% | ~65% | ~70% |
| **Full Fine-tuning** | 95% | 97% | 81% | 91% |

> ⚠️ مشاهده می‌کنیم که در شرایط **few-shot**، Prompt-based learning عملکرد خوبی دارد ولی در شرایط **داده فراوان**، full fine-tuning بهتر است.

---

## 🧬 **۸. وظایف مخصوص برای زبان فارسی و زبان‌های کم‌منبع**

در زبان‌هایی مانند **فارسی** که داده برچسب‌گذاری‌شده کم است، مدل‌های زیر بهترین گزینه‌ها هستند:

| مدل | مناسب برای فارسی؟ | دقت (در داده کم) |
|-----|--------------------|-------------------|
| **mBERT** | ✅ بله | 80–85% |
| **XLM-R** | ✅ بله | 85–90% |
| **Prompt-based + XLM-R** | ✅✅ بسیار مناسب | 88–92% |
| **T5** | ✅ با fine-tuning | 85–90% |
| **BART** | ✅ خلاصه‌سازی و بازنویسی | 87–91% |
| **GPT (smaller versions)** | ✅ تولید متن | 80–85% |

---

## 🧰 **۹. مثال‌هایی از فرمول‌بندی وظایف با Prompt-based Learning**

### ۱. **Sentiment Analysis**
```
Input: I really liked this movie.
Template: It was [MASK].
Label Words: great / terrible
Output: great
```

### ۲. **NLI**
```
Premise: A soccer game with multiple males playing.
Hypothesis: Some men are playing sport.
Template: <S1>?[MASK],<S2>
Label Words: Yes / Maybe / No
Output: Yes
```

### ۳. **Question Answering**
```
Passage: Paris is the capital of France.
Question: What is the capital of France?
Template: Passage: [PASSAGE]. Question: [QUESTION]? Answer: [MASK].
Label Words: Paris
Output: Paris
```

### ۴. **Translation**
```
Input: That is good.
Template: Translate English to German: That is good.
Label Words: Das ist gut
Output: Das ist gut
```

---

## 📦 **۱۰. وظایف خاص با استفاده از مدل‌های Encoder-Decoder (مثل T5 و BART)**

| وظیفه | Template | مثال |
|--------|----------|--------|
| **Summarization** | `summarize:` | خلاصه‌سازی مقاله |
| **Translation** | `translate English to French:` | ترجمه متن |
| **Text Simplification** | `simplify:` | ساده‌سازی جمله |
| **Paraphrasing** | `paraphrase:` | بازنویسی جمله |
| **Dialogue Response Generation** | `dialogue:` | پاسخ به گفت‌وگو |
| **Data-to-Text Generation** | `generate text from table` | تولید متون از جدول |
| **Fill-in-the-blank** | `[CLS]The movie was [MASK].` | پر کردن جای خالی |
| **Text Correction** | `correct:` | اصلاح متن |
| **Text Style Transfer** | `formalize:` / `informalize:` | تغییر سبک متن |

---

## 📋 **۱۱. مثال‌هایی از وظایف در GLUE و SuperGLUE**

| مجموعه داده | نوع وظیفه | توضیح |
|-------------|------------|--------|
| **SST-2** | Sentiment Analysis | طبقه‌بندی جمله به مثبت/منفی |
| **CoLA** | Acceptability | درستی گرامری جمله |
| **MRPC** | Paraphrase Detection | آیا دو جمله معنای یکسانی دارند؟ |
| **STS-B** | Sentence Similarity | شباهت دو جمله (عددی بین 1 تا 5) |
| **QQP** | Duplicate Questions | آیا دو سؤال یکسان هستند؟ |
| **MNLI** | NLI | رابطه منطقی دو جمله |
| **RTE** | NLI | استنتاج منطقی در متن کوتاه |
| **WNLI** | Coreference | آیا یک ضمیر به یک اسم اشاره دارد؟ |

---

## 🧠 **۱۲. نتیجه‌گیری**

### ✅ **مزایای اصلی مدل‌های زبانی بزرگ**
- **دانش عمومی**: مدل‌ها دانش زیادی از زبان دارند.
- **قابلیت generalization**: می‌توانند روی وظایف جدید بدون داده کار کنند (zero-shot).
- **انعطاف‌پذیری**: با تغییر prompt و label words، می‌توانند به وظایف مختلف پاسخ دهند.

### ❌ **چالش‌ها**
- **طراحی بهینه prompt و label words**
- **عدم ثبات در zero-shot (بسته به template و وزن‌دهی)**
- **نیاز به fine-tuning در وظایف پیچیده**

---

## 🧾 **خلاصه نهایی**

| نوع وظیفه | بهترین مدل | بهترین روش |
|----------|--------------|----------------|
| **Sentence Classification** | RoBERTa، BERT | Prompt-based یا Full FT |
| **NER، POS Tagging** | BERT، XLM-R | Token-level FT |
| **Translation** | T5، BART، MarianMT | Seq2Seq Fine-tuning |
| **Summarization** | BART، T5 | Seq2Seq Fine-tuning |
| **Question Answering** | BERT، T5 | Masked LM یا Seq2Seq |
| **Zero-shot/Few-shot** | GPT، T5، BART | Prompt-based Tuning |
| **Low-resource languages** | XLM-R، mBERT، T5 | Prompt-based یا Multilingual FT |

---

اگر می‌خواهید **کد نمونه** برای یک وظیفه خاص (مثل sentiment analysis یا translation) ببینید، یا می‌خواهید یک **prompt template خودکار** بسازید، فقط بگو!
