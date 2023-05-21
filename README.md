# kamus_kbba
Kamus Bahasa Bahasa Alay.

kamus bahasa indonesia khusus bahasa alay (slang) untuk melakukan analisis sentimen pada tahap slang word standardization.

## example of how to use:

### table :
|               | content_clean |
| ------------- | ------------- |
|       0       | ko jadi ngaco ya sekarang udh harus beli tiket...  |
|       1       | tingkatin performa dong dari gua jaman maba am...  |



### code :
```python
kbba_dictionary = pd.read_csv('https://raw.githubusercontent.com/insomniagung/kamus_kbba/main/kbba.txt', delimiter='\t', names=['slang', 'formal'], header=None, encoding='utf-8')

slang_dict = dict(zip(kbba_dictionary['slang'], kbba_dictionary['formal']))
kbba_dictionary

def convert_slangword(text):
    words = text.split()
    
    normalized_words = [slang_dict[word] if word in slang_dict else word for word in words]
    normalized_text = ' '.join(normalized_words)
    return normalized_text

df['content_clean'] = df['content_clean'].apply(convert_slangword)

df[['content_clean']]
```

### table :
|               | content_clean |
| ------------- | ------------- |
|       0       | `kok` jadi `kacau` iya sekarang `sudah` harus beli t...  |
|       1       | `tingkatkan` performa dong dari `saya` `zaman` mahas...  |

---

terdapat penambahan kata. silakan gunakan dengan bijak.

credit and thanks to https://github.com/ramaprakoso/analisis-sentimen/blob/master/kamus/kbba.txt
