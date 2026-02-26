<div dir="rtl">

# 🌿 Stemming في معالجة اللغة الطبيعية (NLP)

## 📌 ما هو Stemming؟

**Stemming** هو عملية تقليل الكلمة إلى أصلها أو جذرها الأساسي (Stem)  
عن طريق حذف اللواحق والزوائد.

الهدف هو تقليل عدد الكلمات المختلفة التي تعبر عن نفس المعنى.

---

## 🔎 مثال باللغة الإنجليزية

| الكلمة الأصلية | بعد Stemming |
|---------------|-------------|
| playing      | play        |
| played       | play        |
| plays        | play        |

---

## 🔎 مثال باللغة العربية

| الكلمة | بعد Stemming |
|--------|--------------|
| يكتبون | كتب |
| كتابة  | كتب |
| مكتوب  | كتب |

> ⚠️ ملاحظة: اللغة العربية أكثر تعقيدًا بسبب الاشتقاق الصرفي.

---

## 🎯 لماذا نستخدم Stemming؟

- تقليل حجم الـ Vocabulary
- تحسين نتائج البحث
- تحسين أداء نماذج التصنيف
- تقليل الضوضاء في البيانات

---

## 🔄 الفرق بين Stemming و Lemmatization

| Stemming | Lemmatization |
|-----------|--------------|
| سريع وبسيط | أكثر دقة |
| قد يعطي كلمات غير صحيحة لغويًا | يعطي كلمات صحيحة لغويًا |
| يعتمد على حذف اللواحق | يعتمد على تحليل لغوي وقاموس |

---

## 🧪 تطبيق عملي (English)

```python
from nltk.stem import PorterStemmer
from nltk.tokenize import word_tokenize

ps = PorterStemmer()

text = "playing played plays"
words = word_tokenize(text)

for word in words:
    print(ps.stem(word))
