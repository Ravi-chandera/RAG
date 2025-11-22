# How to select right encoding system?

When we scrape data from web, we may get many unkown terms or symbols in our content. I did same and when i tried to save this content into text file, I got below error. I put encoding name as **utf-8** while storing file. This error went away but it made me curious about which system to use. So I started reading about it more.

```python 
File ~\AppData\Local\Programs\Python\Python311\Lib\encodings\cp1252.py:19, in IncrementalEncoder.encode(self, input, final)
     18 def encode(self, input, final=False):
---> 19     return codecs.charmap_encode(input,self.errors,encoding_table)[0]

UnicodeEncodeError: 'charmap' codec can't encode character '\u0141' in position 1963: character maps to <undefined>
```

### Reason of above error

The character \u0141 is Ł. This is the Latin Capital Letter L with Stroke. It is primarily used in the Polish language.

Example: It appears in the Polish currency "Złoty" or the name "Mikołaj".

Why this caused error?

traceback reveals the exact problem here: File ...\Lib\encodings\cp1252.py

Our code is running on Windows and, because we didn't specify an encoding, Python defaulted to CP1252 (Windows-1252).

### When to use utf-8 and when to utf-16?

My error got resolved but then i got curious about other encoding systems. There is utf-16 also. 

**UTF-8**

Uses 1 byte to store english charcters 

Uses 3 bytes to store non-english characters

**UTF-16**

Uses 2 byte to store for all characters

So if your data has more than 50% text of non-english characters, go for utf-16 otherwise go for utf-8. This will save lot of storage cost.