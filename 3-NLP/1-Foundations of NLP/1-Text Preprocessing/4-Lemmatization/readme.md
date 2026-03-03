**Lemmatization في معالجة اللغة الطبيعية (NLP)**

---

**ما هي Lemmatization؟**

Lemmatization هي عملية تحويل الكلمة إلى صورتها الأصلية الصحيحة لغويًا (Lemma).

على عكس Stemming الذي يعتمد على حذف ميكانيكي للواحق، فإن Lemmatization تعتمد على تحليل لغوي وقاموس لإرجاع الكلمة إلى الشكل القاموسي الصحيح.

أمثلة:

* running → run
* better → good
* cats → cat

---

**الفرق بين Stemming و Lemmatization**

| Stemming               | Lemmatization               |
| ---------------------- | --------------------------- |
| يعتمد على حذف ميكانيكي | يعتمد على تحليل لغوي وقاموس |
| قد ينتج كلمة غير صحيحة | ينتج كلمة صحيحة لغويًا      |
| أسرع                   | أبطأ لكن أدق                |

---

**مقارنة عملية**

| الكلمة   | Stemming | Lemmatization | الملاحظة                |
| -------- | -------- | ------------- | ----------------------- |
| studies  | studi    | study         | Stemming يشوه الكلمة    |
| studying | studi    | study         | Lemmatizer يرجعها للأصل |
| children | children | child         | يفهم الجمع غير المنتظم  |
| better   | better   | good (مع POS) | يحتاج تحديد نوع الكلمة  |
| running  | run      | run           | كلاهما صحيح             |
| leaves   | leav     | leaf          | Stemming يقطع فقط       |
| fishes   | fish     | fish          | Lemmatizer يفهم القاعدة |

---

**تطبيق عملي باستخدام NLTK**

1. تحميل الموارد (مرة واحدة فقط)

```python
import nltk
nltk.download('wordnet')
nltk.download('omw-1.4')
```

2. Lemmatization بدون تحديد نوع الكلمة

```python
from nltk.stem import WordNetLemmatizer
from nltk.tokenize import word_tokenize

lemmatizer = WordNetLemmatizer()

text = "running better cats"
tokens = word_tokenize(text)

lemmas = [lemmatizer.lemmatize(word) for word in tokens]

print(lemmas)
```

الناتج:

```
['running', 'better', 'cat']
```

ملاحظة:

* cats → cat ✔
* running لم تتحول إلى run ❌
* better لم تتحول إلى good ❌

السبب: لم يتم تحديد نوع الكلمة (POS).

---

**Lemmatization مع تحديد نوع الكلمة (أكثر دقة)**

```python
from nltk.corpus import wordnet

lemmatizer.lemmatize("running", pos=wordnet.VERB)
```

الناتج:

```
run
```

مثال آخر:

```python
lemmatizer.lemmatize("better", pos=wordnet.ADJ)
```

الناتج:

```
good
```

---

**مثال تطبيقي كامل**

```python
from nltk.stem import WordNetLemmatizer
from nltk.tokenize import word_tokenize
from nltk.corpus import wordnet

lemmatizer = WordNetLemmatizer()

text = "The cats are running better than dogs"
tokens = word_tokenize(text)

lemmas = []

for word in tokens:
    lemmas.append(lemmatizer.lemmatize(word, pos=wordnet.VERB))

print(lemmas)
```

في التطبيقات الاحترافية يجب تنفيذ POS Tagging أولًا ثم تمرير النوع المناسب لكل كلمة.

---

**نص لاختبار الفرق بوضوح**

```python
text = """
Relational relationships are relatively related.
The organization was organizing organized events.
He was caring and carefully cared for the cared cats.
"""
```

نتائج Stemming قد تكون:

* relational → relat
* organization → organ
* carefully → care

بينما Lemmatization تعطي كلمات منطقية أكثر.

---

**ماذا عن اللغة العربية؟**

مكتبة NLTK لا توفر دعمًا قويًا لـ Lemmatization باللغة العربية.
يُفضل استخدام أدوات متخصصة مثل:

* CAMeL Tools
* Farasa
* Stanza

---

**ماذا عن نماذج اللغة الحديثة (LLMs)؟**

في النماذج الحديثة غالبًا لا يتم استخدام:

* Stemming
* Lemmatization

بسبب الاعتماد على تقنيات Subword Tokenization مثل:

* BPE
* WordPiece
* SentencePiece

لكن في أنظمة NLP التقليدية، تظل Lemmatization خطوة مهمة لتحسين جودة البيانات ودقة النماذج.

---

**الخلاصة**

* Lemmatization أدق لغويًا من Stemming
* تحتاج تحديد نوع الكلمة (POS) للحصول على أفضل نتيجة
* مهمة جدًا في NLP التقليدي
* أقل استخدامًا في نماذج اللغة الكبيرة الحديثة
