# 📚 تقسيم النصوص (Tokenization) باستخدام NLTK

هذا المستودع يوضح كيفية استخدام مكتبة **NLTK** لتقسيم النصوص إلى **جمل وكلمات**، خطوة بخطوة.

---

## 🔹 تثبيت المكتبة والموارد

```python
import nltk
nltk.download()  # يقوم بتحميل الموارد اللازمة مثل punkt

punkt ضروري لتقسيم الجمل والكلمات.

🔹 تقسيم النص إلى جمل وكلمات
text = "Hello! How are you doing today? I"

# تقسيم النص إلى جمل
sentences = nltk.sent_tokenize(text)

# تقسيم النص إلى كلمات
tokens = nltk.word_tokenize(text)

print(sentences)
print(tokens)
الناتج المتوقع

الجمل:

['Hello!', 'How are you doing today?', 'I']

الكلمات (Tokens):

['Hello', '!', 'How', 'are', 'you', 'doing', 'today', '?', 'I']
🔹 ملاحظات مهمة

word_tokenize يحافظ على علامات الترقيم كتوكنات منفصلة.

هذه الطريقة تسمى Word-level Tokenization، وهي مشابهة للخطوات الأولى قبل استخدام BPE أو Subword Tokenization.

🔹 تحسين عملي: إزالة علامات الترقيم
import string

clean_tokens = [t for t in tokens if t not in string.punctuation]
print(clean_tokens)

الناتج:

['Hello', 'How', 'are', 'you', 'doing', 'today', 'I']
🔹 خطوات مستقبلية

يمكن تطوير Tokenizer خاص بكلمة وكلمة جاهز للبناء على Mini LLM من الصفر.

بعد هذه الخطوة، يمكنك الانتقال إلى:

TF-IDF و Word Embeddings

RNN / LSTM

Transformers و LLM

🔹 المراجع

NLTK Documentation

Tokenization in NLP


---
