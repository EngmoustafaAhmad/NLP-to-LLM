<div dir="rtl">

# 🛑 إزالة الكلمات الشائعة (Stop Words) للنص العربي باستخدام NLTK

في معالجة اللغة الطبيعية (NLP)، تعتبر **الكلمات الشائعة (Stop Words)** كلمات متكررة لا تضيف معنى كبير للتحليل مثل:  
"في"، "من"، "على"، "حول"، إلخ.

إزالة هذه الكلمات تساعد النموذج على التركيز على الكلمات المهمة فقط.

---

## 🔹 المتطلبات

تأكد من تثبيت مكتبة NLTK:

```bash
pip install nltk

import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

# تحميل الموارد (مرة واحدة فقط)
# nltk.download('punkt')
# nltk.download('stopwords')

# Define a sample Arabic text
arabic_text = "قامت الشركة بإصدار بيانات تفصيلية حول أدائها في الربع الأول من العام الحالي"

# Tokenize the text into words
words = word_tokenize(arabic_text)

# Load the Arabic stop words
stop_words = set(stopwords.words('arabic'))

# Filter out the stop words
filtered_words = [word for word in words if word not in stop_words]

# Join correctly with space
filtered_text = ' '.join(filtered_words)

print(filtered_text)

```
# الناتج المتوقع

بعد إزالة كلمات مثل:

في

من

حول

سيكون الناتج تقريبًا:

قامت الشركة بإصدار بيانات تفصيلية أدائها الربع الأول العام الحالي





# تحسين احترافي أقوى (للـ NLP الحقيقي)

في اللغة العربية الأفضل تعمل:

Normalization (إزالة التشكيل)

إزالة علامات الترقيم

توحيد الألف (أ، إ، آ → ا)

إزالة Stopwords

Stemming أو Lemmatization


</div>
