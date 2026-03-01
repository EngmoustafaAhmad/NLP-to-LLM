Lemmatization في معالجة اللغة الطبيعية
🔹 يعني إيه Lemmatization؟

Lemmatization هي عملية تحويل الكلمة إلى صورتها الأصلية الصحيحة لغويًا (Lemma).

يعني مش بس نحذف لواحق زي Stemming،
لكن نرجع الكلمة لشكلها القاموسي الصحيح.

🔎 الفرق بين Stemming و Lemmatization
Stemming	Lemmatization
يعتمد على حذف ميكانيكي	يعتمد على تحليل لغوي
قد ينتج كلمة غير صحيحة	ينتج كلمة صحيحة لغويًا
أسرع	أبطأ لكن أدق
مثال بالإنجليزية
الكلمة	Stemming	Lemmatization
playing	play	play
better	better	good
running	run	run

لاحظ:

Stemming مش دايمًا يفهم المعنى

Lemmatization يفهم السياق

🧠 لماذا نستخدم Lemmatization؟

تحسين دقة النماذج

مهم في Chatbots

مهم في Question Answering

مهم في Search Engines

🥇 تطبيق عملي باستخدام NLTK
Step 1: تحميل WordNet (مرة واحدة)
import nltk
nltk.download('wordnet')
nltk.download('omw-1.4')
Step 2: التطبيق
from nltk.stem import WordNetLemmatizer
from nltk.tokenize import word_tokenize

lemmatizer = WordNetLemmatizer()

text = "running better cats"
tokens = word_tokenize(text)

lemmas = [lemmatizer.lemmatize(word) for word in tokens]

print(lemmas)
الناتج:
['running', 'better', 'cat']

لاحظ إن:

cats → cat ✔

running لم تتحول لـ run ❌

لأن لازم نحدد نوع الكلمة (POS).

🥈 Lemmatization مع تحديد نوع الكلمة (أدق)
from nltk.corpus import wordnet

lemmatizer.lemmatize("running", pos=wordnet.VERB)

الناتج:

run
🔥 Full Example احترافي
from nltk.stem import WordNetLemmatizer
from nltk.tokenize import word_tokenize
from nltk.corpus import wordnet

lemmatizer = WordNetLemmatizer()

text = "The cats are running better than dogs"
tokens = word_tokenize(text)

lemmas = [lemmatizer.lemmatize(word, pos=wordnet.VERB) for word in tokens]

print(lemmas)
📌 ماذا عن العربية؟

NLTK لا يدعم Lemmatization عربي جيد.

للعربية نستخدم:

CAMeL Tools

Farasa

Stanza

لكن دول أكبر شوية في الحجم.

🎯 في LLM الحديثة

عادة لا نستخدم:

Stemming

Lemmatization

لأننا نستخدم:

Subword Tokenization (BPE)

WordPiece

SentencePiece

لكن في NLP التقليدي، Lemmatization مهم جدًا.
