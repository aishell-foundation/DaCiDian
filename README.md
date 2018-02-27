# DaCiDian (大词典) 

DaCiDian is an open-sourced chinese mandarin lexicon for Automatic Speech Recognition

---

The lexicon is structured by two mappers:

### 1. Word -> Syllabel Mapper (DaCiDian.txt)

* word and its pronunciations are seperated by __tab__
* multiple pronunciations are seperated by __;__
* each pronunciation is a sequence of Chinese PinYin syllabels, which are seperated by __space__
* tone infomation are encoded into 0,1,2,3,4

examples:

```
...
裤子    KU_4 ZI_0
好事    HAO_4 SHI_4;HAO_3 SHI_4
教授    JIAO_1 SHOU_4;JIAO_4 SHOU_4
...
语音识别  YU_3 YIN_1 SHI_2 BIE_2
傅里叶变换 FU_4 LI_3 YE_4 BIAN_4 HUAN_4
```
    
### 2. Syllabel->Phone Mapper (pinyin_to_if.txt)
pinyin_to_if is a user-defined mapping from PinYin syllabels to desired phone set

Take traditional PinYin's Initial-Final structure for example, a mapping should be defined as follows:
```
A	$0 a
AI	$0 ai
AN	$0 an
ANG	$0 ang
AO	$0 ao
BA	b a
BAI	b ai
BAN	b an
BANG	b ang
BAO	b ao
...
...
...
ZONG	z ong
ZOU	z ou
ZU	z u
ZUAN	z uan
ZUI	z ui
ZUN	z un
ZUO	z uo
```

* __tab__ is used to seperate syllable and its phoneme representation
* __$0__ is the NULL-Initial phone

## Notes
* users can customize syllable->phone mapper to construct a Chinese lexicon with their own phone set.

* English word pronunciation in Chinese context *is* a problem, at the moment, we would rather leave it alone. 
