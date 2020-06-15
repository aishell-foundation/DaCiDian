# DaCiDian (大词典) 

DaCiDian is an open-sourced lexicon for Chinese Automatic Speech Recognition(ASR)

---
## Design

In mainstream ASR system, lexicon is a core component, that maps word into acoustic modeling units(such as phone).  In DaCiDian, we break the mapping into 2 independent layers:
```
word --> PinYin syllable --> phoneme
```

The purpose of this design is as follows:
* Anyone who is familiar with PinYin (basically every mandarin speaker), can enrich DaCiDian's vocabulary, by adding new entry(word) into the layer-1 mapping.

* ASR system developers can easily adapt DaCiDian to their own phone set by defining their own layer-2 mapping.

---
### Layer-1: Word -> Syllable Mapper (word_to_pinyin.txt)

* word and its pronunciation(s) are seperated by __tab__
* multiple pronunciations are seperated by __;__
* each pronunciation is a sequence of Chinese PinYin syllables, seperated by __space__
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
    
### Layer-2: Syllabel->Phone Mapper (pinyin_to_phone.txt)
pinyin_to_phone is a user-defined mapping from PinYin syllables to target phone set

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

* syllable and its phoneme representation are seperated by __tab__ 
* __$0__ is the NULL-Initial phone.

---
## Notes
* English word in Chinese context *is* a problem. An upgraded version covering both English and Chinese can be found here [BigCiDian](https://github.com/speechio/BigCiDian)
