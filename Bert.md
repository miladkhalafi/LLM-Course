### معماری مدل **BERT** بر اساس جزوه

#### ۱. **مقدمه**
**BERT (Bidirectional Encoder Representations from Transformers)** یک مدل زبانی مبتنی بر **Transformer Encoder** است که به‌طور دوطرفه (bidirectional) اطلاعات را پردازش می‌کند و نمایش‌های عمیقی از کلمات با توجه به **کل متن** فراهم می‌کند.

---

### ۲. **ویژگی‌های کلیدی BERT**

| خصوصیت | توضیح |
|--------|--------|
| **نوع مدل** | فقط **Encoder** از Transformer |
| **آموزش** | بدون نظارت (pre-training)، سپس fine-tuning |
| **روش آموزش** | Masked Language Modeling + Next Sentence Prediction |
| **نوع زبان** | دوطرفه (با در نظر گرفتن تمام متن، چپ و راست) |
| **کاربرد** | طبقه‌بندی جمله، تشخیص موجودیت، پاسخ‌دهی به سوال، ویرایش متن و غیره |

---

### ۳. **معماری کلی BERT**

#### الف) **ورودی (Input Representation)**

هر ورودی شامل سه نوع embedding است:

1. **Token Embeddings**: نمایش برداری کلمات
2. **Segment Embeddings**: برای تشخیص بین دو جمله (A و B)
3. **Positional Embeddings**: موقعیت کلمه در جمله را مشخص می‌کند

مثال:
```
[CLS] The man went to the [MASK] store [SEP]
My dog is a cute animal [SEP]
```

- `[CLS]`: توکن خاص برای نمایش شروع جمله و استفاده در classification
- `[SEP]`: جداکننده بین دو جمله

#### ب) **Transformer Encoder Stack**

- **تعداد لایه‌ها (N)**: 12 یا 24 لایه (در نسخه‌های مختلف)
- **تعداد Head‌های Attention**: 12 یا 16
- **ابعاد هر بردار (d_model)**: 768 یا 1024
- **Feed Forward Network**: دو لایه با ReLU

#### ج) **خروجی**

- **CLS Token**: برای وظایفی مثل طبقه‌بندی جمله
- **Hidden States**: برای وظایف token-level مثل NER یا POS Tagging

---

### ۴. **هدف‌های آموزشی BERT**

#### الف) **Masked Language Model (MLM)**

- 15% از کلمات در جمله **mask** می‌شوند.
- از این کلمات mask شده برای پیش‌بینی کلمه اصلی استفاده می‌شود.
- این کار به مدل کمک می‌کند تا با توجه به **کل جمله** معنای کلمه را متوجه شود.

##### نحوه انتخاب کلمه‌های mask:
- 80%: با `[MASK]` جایگزین می‌شوند
- 10%: با کلمه تصادفی جایگزین می‌شوند
- 10%: بدون تغییر باقی می‌مانند

> ⚠️ توجه: مقدار 15% انتخاب شده بهینه است. خیلی کم = آموزش کند، خیلی زیاد = از دست دادن ساختار جمله

#### ب) **Next Sentence Prediction (NSP)**

- **هدف:** تشخیص اینکه آیا دو جمله پشت سر هم هستند یا نه.
- برای وظایفی مثل Natural Language Inference (NLI) و Question Answering مناسب است.

##### نحوه آموزش:
- 50% جفت جمله متوالی (next sentence)
- 50% جفت جمله تصادفی (not next)

---

### ۵. **فرآیند آموزش BERT**

#### الف) **واژه‌نامه (Vocabulary)**

- از **WordPiece** استفاده می‌شود (نسخه‌ای از BPE).
- حجم واژه‌نامه: 30,000 subword unit
- شامل کلمات متداول، خطاهای املایی، واحدهای جدید و ...

#### ب) **Embedding‌ها**

- **Token Embedding**: برای هر توکن
- **Segment Embedding**: برای تمایز بین دو جمله (A و B)
- **Positional Embedding**: برای موقعیت توکن در جمله (تا 512 توکن)

---

### ۶. **Fine-tuning BERT**

#### الف) **وظایف سطح جمله (Sentence-level Tasks)**

- مثال: SST-2 (Sentiment Analysis)، CoLA (Linguistic Acceptability)
- تنها یک لایه linear روی `[CLS]` اضافه می‌شود.

#### ب) **وظایف جفت جمله (Sentence Pair Tasks)**

- مثال: MNLI، QQP، QNLI، STS-B، MRPC
- `[SEP]` برای جدا کردن دو جمله استفاده می‌شود.

#### ج) **وظایف Token-level**

- مثال: SQuAD (Question Answering)، CoNLL-2003 (NER)
- از hidden states خروجی هر token استفاده می‌شود.

#### د) **تعداد پارامترهای قابل آموزش**

- BERT-base: ~110 میلیون پارامتر
- BERT-large: ~340 میلیون پارامتر

---

### ۷. **مدل‌های مشابه و اصلاح شده BERT**

- **RoBERTa**: بدون NSP، آموزش بیشتر، عملکرد بهتر
- **ALBERT**: به اشتراک گذاشتن وزن‌ها بین لایه‌ها → ذخیره‌سازی کمتر
- **DistilBERT**: کوچک‌تر و سریع‌تر، ولی با کمی کاهش دقت
- **SciBERT / BioBERT / ClinicalBERT**: برای حوزه‌های علمی، پزشکی و بالینی
- **Multilingual BERT**: آموزش روی 104 زبان با یک واژه‌نامه مشترک

---

### ۸. **مزایای BERT**

- یادگیری دوطرفه (context دو طرفه)
- استفاده از attention mechanism قوی
- انعطاف‌پذیری بالا برای وظایف مختلف
- بهبود چشمگیری در مجموعه‌های GLUE، SuperGLUE و SQuAD

---

### ۹. **معایب BERT**

- نسبتاً سنگین و حافظه‌بر
- فقط Encoder، بنابراین نمی‌تواند مستقیماً تولید متن کند
- محدودیت در طول جمله (حداکثر 512 توکن)

---

### ۱۰. **خلاصه معماری BERT**

| جزء | توضیح |
|-----|-------|
| **Encoder فقط** | 12 یا 24 لایه Transformer Encoder |
| **Attention** | Multi-head Self-Attention |
| **Positional Embedding** | یادگیری‌شده، تا 512 توکن |
| **Segment Embedding** | A یا B |
| **MLM Objective** | 15% توکن‌ها mask شده |
| **NSP Objective** | 50% جفت جمله مرتبط، 50% تصادفی |
| **Fine-tuning** | اضافه کردن لایه‌های task-specific |

---

### تصویر کلی از Fine-tuning BERT برای وظایف مختلف:

#### الف) **Single Sentence Classification**
```
[CLS] This movie is great! [SEP]
          ↘ Linear ↘ Class (Positive/Negative)
```

#### ب) **Sentence Pair Classification (MNLI)**
```
[CLS] Premise [SEP] Hypothesis [SEP]
          ↘ Linear ↘ Entailment/Neutral/Contradiction
```

#### ج) **Named Entity Recognition (NER)**
```
[CLS] My name is George Washington [SEP]
     ↘ ↘ ↘ ↘ ↘ ↘ ↘ ↘ ↘ ↘ ↘
    O   O   O   B-PER   I-PER
```

#### د) **Question Answering (SQuAD)**
```
[CLS] Question [SEP] Passage [SEP]
     ↘ Start Position
     ↘ End Position
```

---

### منبع:
- `section4-Transformers (part3).pdf`
- `section3-Transformers (part2).pdf`

اگر می‌خواهید مقایسه BERT با GPT یا T5 یا نحوه fine-tuning دقیق آن را ببینید، بفرمایید!
