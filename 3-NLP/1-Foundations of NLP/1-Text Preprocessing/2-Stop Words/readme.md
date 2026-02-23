# 🛑 إزالة الكلمات الشائعة (Stop Words) باستخدام NLTK

في معالجة النصوص (NLP)، **Stop Words** هي الكلمات الشائعة التي عادة لا تحمل معنى كبير في التحليل، مثل: "و"، "في"، "على"، "من"، إلخ.  
إزالة هذه الكلمات تساعد النماذج على التركيز على الكلمات المهمة فقط.

---

## 🔹 تثبيت مكتبة NLTK وتحميل Stop Words

```python
import nltk
nltk.download('stopwords')  # تحميل قائمة الكلمات الشائعة
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

🔹 استخدام Stop Words بالعربية
arabic_stopwords = stopwords.words('arabic')
print(arabic_stopwords[:10])  # عرض أول 10 كلمات كمثال

نتيجة محتملة:

['كلاهما', 'كلنا', 'كلما', 'كليكما', 'كليهما', 'كم', 'كما', 'كي', ...]

إزالة Stop Words من نص
text = "كلنا نحب تعلم الذكاء الاصطناعي في الجامعة."
tokens = word_tokenize(text)

# إزالة الكلمات الشائعة
filtered_tokens = [w for w in tokens if w not in arabic_stopwords]

print(filtered_tokens)

الناتج:

['نحب', 'تعلم', 'الذكاء', 'الاصطناعي', 'الجامعة', '.']
🔹 ملاحظات مهمة

إزالة Stop Words تساعد على تقليل الضوضاء في البيانات النصية.

لا تحذف دائمًا كل الكلمات الشائعة، لأن بعضها قد يكون مهم في بعض التحليلات (مثل تحليل المشاعر).

يمكن دمج هذه الخطوة مع Tokenization، Stemming، Lemmatization للحصول على نتائج أفضل.

🔹 خطوات مستقبلية

تطبيق TF-IDF على النص بعد إزالة Stop Words

استخدام Word Embeddings مثل Word2Vec أو GloVe

بناء Classification أو NLP Model مع بيانات نظيفة
