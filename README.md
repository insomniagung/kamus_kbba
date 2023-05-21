# kamus_kbba
kamus bahasa indonesia khusus bahasa alay (slang) untuk melakukan analisis sentimen pada tahap slang word standardization.

example of how to use:
---

kbba_dictionary = pd.read_csv('https://raw.githubusercontent.com/insomniagung/kamus_kbba/main/kbba.txt', delimiter='\t', names=['slang', 'formal'], header=None, encoding='utf-8')
slang_dict = dict(zip(kbba_dictionary['slang'], kbba_dictionary['formal']))
kbba_dictionary
def convert_slangword(text):
    words = text.split()
    normalized_words = [slang_dict[word] if word in slang_dict else word for word in words]
    normalized_text = ' '.join(normalized_words)
    return normalized_text
df['content_clean'] = df['content_clean'].apply(convert_slangword)

---

terdapat penambahan kata. credit and thanks to https://github.com/ramaprakoso/analisis-sentimen/blob/master/kamus/kbba.txt
