### مدل **Prompt-based Learning** (بر اساس جزوات)

مدل‌های **Prompt-based** یک روش نوین در زمینه یادگیری ماشین و به خصوص در مدل‌های زبانی بزرگ (LLMs) هستند که بدون تغییر پارامترهای مدل، با استفاده از **فرمول‌بندی وظایف به صورت طبیعی قابل خواندن برای مدل** (prompt)، مدل را قادر می‌سازند تا بدون fine-tuning مستقیم، وظایف مختلفی را حل کنند.

---

## 📌 ۱. **مفاهیم کلیدی Prompt-based Learning**

### الف) **Prompt**
- یک **قالب متنی** است که ورودی وظیفه را به شکلی قابل فهم برای مدل در می‌آورد.
- مثال:  
  ```
  The movie was [MASK]. 
  Options: great / terrible
  ```

### ب) **Verbalizer**
- نگاشتی بین **خروجی مدل** (مثل کلمه پیش‌بینی‌شده در [MASK]) و **برچسب‌های معنایی** (مانند positive/negative).
- مثال:
  - `great` → `positive`
  - `terrible` → `negative`

### ج) **Zero-shot / Few-shot Prompting**
- **Zero-shot**: بدون هیچ داده آموزشی، فقط با prompt و verbalizer.
- **Few-shot**: با تعداد کمی نمونه (مثلاً 10 نمونه) به عنوان "demonstrations" در کنار prompt.

---

## 🧠 ۲. **چرا Prompt-based Learning؟**

| مزیت | توضیح |
|------|--------|
| **بدون Fine-tuning** | نیازی به به‌روزرسانی پارامترهای مدل نیست. |
| **ذخیره‌سازی کمتر** | تنها قالب ورودی (prompt) ذخیره می‌شود. |
| **قابلیت عمومیت** | می‌تواند روی وظایف جدید بدون re-training کار کند. |
| **کارایی بالا در شرایط کم‌داده** | برای زبان‌های کم‌منبع و داده‌های محدود مناسب است. |

---

## 🎯 ۳. **روش کار Prompt-based Learning**

### مرحله ۱: **فرمول‌بندی وظیفه با Prompt Template**
مثال:
```
[Sentence] It was [MASK].
```

### مرحله ۲: **انتخاب Verbalizer**
```
[MASK] = great → Positive
[MASK] = terrible → Negative
```

### مرحله ۳: **استفاده از مدل زبانی**
- مدل احتمالات را برای تمام کلمات موجود در واژه‌نامه محاسبه می‌کند.
- سپس احتمال کلمات در verbalizer مقایسه می‌شود.

### مرحله ۴: **پیش‌بینی**
- کلمه با بیشترین احتمال در verbalizer انتخاب می‌شود.

---

## 🧩 ۴. **انواع Prompt-based Learning**

| نوع | توضیح |
|-----|--------|
| **Zero-shot Prompting** | بدون هیچ نمونه آموزشی، فقط با prompt template. |
| **Few-shot Prompting** | با تعداد کمی نمونه (مثل 5-20 نمونه) در کنار prompt. |
| **Manual Prompting** | طراحی دستی prompt و verbalizer. |
| **Automatic Prompting** | استفاده از الگوریتم‌ها برای یافتن بهترین template و label words. |

---

## 📊 ۵. **مقایسه عملکرد Prompt-based با روش‌های دیگر**

| روش | SST-2 (acc) | CoLA (acc) | MRPC (F1) | QNLI (acc) | RTE (acc) | منبع |
|-----|-------------|------------|------------|------------|-----------|--------|
| **Prompt-based Zero-shot** | 83.6% | 32.0% | 61.9% | 50.8% | 51.3% | Zero-Shot File |
| **Prompt-based Few-shot** | 92.7% | 91.2% | 74.5% | 68.3% | 69.1% | Zero-Shot File |
| **Full Fine-tuning** | 95.0% | 97.0% | 91.4% | 93.3% | 80.9% | Zero-Shot File |

> ⚠️ مشاهده می‌کنیم که **Prompt-based learning** بدون fine-tuning کامل، می‌تواند به نتایج قابل قبولی دست یابد، به خصوص در شرایط **few-shot**.

---

## 🔍 ۶. **مزایای Prompt-based Learning**

- **عدم نیاز به fine-tuning**: صرفه‌جویی در زمان و منابع محاسباتی.
- **استفاده از دانش قبلی مدل**: مدل از دانش pre-trained خود استفاده می‌کند.
- **انعطاف‌پذیری بالا**: با تغییر prompt و label mapping می‌توان وظایف جدید را حل کرد.
- **مناسب برای کاربردهای کم‌داده**: مثل زبان‌های کم‌منبع یا دامنه‌های جدید.

---

## 🧩 ۷. **معایب Prompt-based Learning**

- **وابستگی به طراحی دقیق prompt و verbalizer**: یک template ضعیف می‌تواند عملکرد را بشدت کاهش دهد.
- **حساسیت به انتخاب label words**: بعضی از کلمات بهتر از دیگران برای verbalizer هستند.
- **عدم وجود روش‌های استاندارد**: طراحی بهینه prompt هنوز یک چالش است.
- **عملکرد پایین‌تر نسبت به full fine-tuning** در شرایط داده فراوان.

---

## 🛠️ ۸. **روش‌های انتخاب خودکار Prompt و Label Words**

### الف) **انتخاب خودکار Label Words**
1. **Top-k Selection**:
   - برای هر کلاس، k کلمه با بیشترین احتمال در حضور prompt انتخاب می‌شوند.
2. **Enumerate Combinations**:
   - تمام ترکیبات ممکن label words برای کلاس‌ها ارزیابی می‌شوند.
3. **Prune by Zero-shot Accuracy**:
   - ترکیباتی که عملکرد بدی دارند حذف می‌شوند.
4. **Fine-tuning on Top Candidates**:
   - بهترین ترکیب‌ها با fine-tuning کوتاه انتخاب می‌شوند.

### ب) **ایجاد خودکار Template**
- با استفاده از مدل‌های زبانی مثل T5 یا GPT، templates بهینه‌ای تولید می‌شوند.
- این templates با beam search یا reinforcement learning بهینه می‌شوند.

---

## 🧪 ۹. **کاربردهای Prompt-based Learning**

| دامنه | مثال |
|-------|------|
| **Sentiment Analysis** | تشخیص نظر مثبت/منفی در متن |
| **Natural Language Inference (NLI)** | تشخیص عبارات پوشیده (entailment, contradiction) |
| **Question Answering** | پاسخ‌دهی به سؤالات با استفاده از متن |
| **Subjectivity Detection** | تشخیص آیا متن شخصی است یا شیوه‌ای |
| **Paraphrase Detection** | تشخیص تکرار معنایی دو جمله |
| **Text Similarity** | محاسبه شباهت دو جمله |

---

## 📈 ۱۰. **عملکرد Prompt-based Learning در مقایسه با سایر روش‌ها**

### بر اساس RoBERTa-large:

| روش | SST-2 | CoLA | MRPC | QNLI | RTE | STS-B |
|------|-------|------|------|------|-----|--------|
| **Zero-shot Prompt-based** | 83.6% | 32.0% | 61.9% | 50.8% | 51.3% | -3.2% |
| **Few-shot Prompt-based (manual)** | 92.7% | 91.2% | 74.5% | 68.3% | 69.1% | 71.0% |
| **Few-shot Prompt-based (auto + manual)** | 93.0% | 92.3% | 78.1% | 69.2% | 71.1% | 76.4% |
| **Full Fine-tuning** | 95.0% | 97.0% | 91.4% | 93.3% | 80.9% | 91.9% |

مشاهده می‌کنیم که حتی با داده کم، **Prompt-based learning** می‌تواند عملکرد خوبی داشته باشد و در برخی موارد بهتر از روش‌های قدیمی‌تر است.

---

## 🧬 ۱۱. **مقایسه انواع Template (Prompt) در Sentiment Analysis**

| Template | Label Words | دقت (SST-2) |
|---------|------------|---------------|
| `<S1>It was [MASK].` | great/terrible | 92.7% |
| `<S1>It was [MASK].` | good/bad | 92.5% |
| `<S1>It was [MASK].` | cat/dog | 91.5% |
| `<S1>It was [MASK].` | dog/cat | 86.2% |
| `<S1>It was [MASK].` | terrible/great | 83.2% |
| **Full Fine-tuning** | — | 81.4% |

این جدول نشان می‌دهد که انتخاب صحیح template و label words چقدر مهم است.

---

## 🧠 ۱۲. **چطور بهترین Prompt و Label Words را انتخاب کنیم؟**

### الف) **روش‌های دستی**
- طراحی template بر اساس تجربه متخصص.
- انتخاب label words با توجه به معنا و فراوانی در داده.

### ب) **روش‌های خودکار**
- استفاده از مدل‌های زبانی برای پیشنهاد template.
- انتخاب label words با استفاده از احتمالات شرطی در مدل زبانی.

### ج) **روش‌های جستجوی خودکار**
- جستجوی تمام ترکیبات ممکن label words.
- استفاده از beam search یا reinforcement learning برای پیدا کردن بهترین template.

---

## 📦 ۱۳. **کاربرد در زبان‌های کم‌منبع (Low-resource Languages)**

در زبان‌هایی مانند **فارسی** که داده‌های برچسب‌گذاری‌شده کمی وجود دارد، Prompt-based learning یکی از بهترین روش‌ها است:

### چگونه؟
1. **استفاده از مدل multilingual** (مثل mBERT یا XLM-R)
2. **طراحی template و label words مناسب برای زبان فارسی**
3. **استفاده از few-shot examples در context**
4. **بهینه‌سازی label words با استفاده از احتمالات شرطی**

مثال:
```
فیلم واقعاً خوب بود. [MASK]
گزینه‌ها: عالی / بد
```

---

## 🧪 ۱۴. **مقایسه با روش‌های دیگر**

| روش | مزایا | معایب | بهترین شرایط |
|------|--------|--------|------------------|
| **Prompt-based Zero-shot** | بدون داده، بدون fine-tuning | وابستگی به template | وقتی داده نداریم |
| **Prompt-based Few-shot** | بدون fine-tuning، با دقت بالا | نیاز به انتخاب هوشمندانه نمونه‌ها | داده کم، دقت بالا |
| **Prompt-based + Auto Prompt** | خودکار، بدون دخالت کاربر | نیاز به محاسبات بیشتر | داده کم، منابع زیاد |
| **Full Fine-tuning** | دقت بالا در شرایط داده فراوان | نیاز به fine-tuning | داده فراوان، منابع زیاد |

---

## 🧩 ۱۵. **چالش‌ها و مسائل باقی‌مانده**

| چالش | توضیح |
|-------|--------|
| **طراحی بهینه Prompt** | چطور بهترین template را پیدا کنیم؟ |
| **انتخاب بهترین Label Words** | چه کلماتی بهترین عملکرد را دارند؟ |
| **Overfitting در Few-shot** | ممکن است model به نمونه‌های few-shot overfit کند. |
| **Generalization به وظایف جدید** | مدل چقدر به خوبی روی وظایف جدید عمل می‌کند؟ |

---

## 📈 ۱۶. **روند بهبود عملکرد Prompt-based Models**

| مرحله | نحوه بهبود |
|-------|--------------|
| **Template Design** | استفاده از الگوهای خودکار و بهینه |
| **Label Word Selection** | استفاده از top-k احتمالات شرطی |
| **Demonstration Selection** | انتخاب هوشمندانه از نمونه‌های few-shot |
| **Re-ranking after Finetuning** | ارزیابی نهایی با fine-tuning کوتاه |

---

## 🧭 ۱۷. **نتیجه‌گیری**

### ✅ **مزایای اصلی:**
- بدون fine-tuning کامل
- استفاده از دانش pre-trained
- کارایی بالا در شرایط کم‌داده
- انعطاف‌پذیری بالا در طراحی وظایف

### ❌ **چالش‌ها:**
- طراحی بهینه template و label words
- عدم وجود استاندارد واحد
- حساسیت به انتخاب نمونه‌ها (few-shot)

### 📌 **کاربردهای مناسب:**
- زبان‌های کم‌منبع (مثل فارسی)
- وظایف جدید بدون داده برچسب‌گذاری‌شده
- مدل‌های بزرگ (مثل BERT، RoBERTa، T5، GPT-3)

---

### 💡 **نکته کاربردی:**  
اگر به دنبال **راه‌حلی برای یک پروژه با داده کم** هستید، **Prompt-based Learning** یکی از بهترین گزینه‌هاست. مخصوصاً اگر از **GPT-3** یا **T5** استفاده کنید، می‌توانید بدون fine-tuning، نتایج خوبی بگیرید.

---

### 📚 منابع:
- `section5-zero-shot learning.pdf`
- `section6-parameter efficient fine tuning.pdf`
- `section4-Transformers (part3).pdf`

اگر می‌خواهید **کد عملی** یا **پروژه‌های کاربردی** با Prompt-based Learning ببینید، لطفاً بفرمایید!
