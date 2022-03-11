# SynthTIGER
## 1. Introduction

- image와 text 쌍을 포함한 large-sacel data를 통해 학습함으로써 OCR의 성능이 dramatically하게 향상되었다. 일반적으로 텍스트 길이나, 폰트, 배경 등의 다양한 특징의 조합들을 cover할 수 있는 real text이미지를 모으고 어노테이션하기는 불가능하기 때문에, OCR은 synthetic text image를 포함한 large-scale data를 사용한다.
- OCR에는 두가지 task가 있다. Scene Text Detatcin(STD)와 Scene Text Recognition(STR)이다.
    - STD : 배경으로 부터 text araea를 localize
        
        학습이미지는 다양한 텍스트를 포함한 raw scene또는 document snapshot
        
    - STR : single word나  line of word를 포함한 word box image path로 부터 문자 sequence를 식별
        
        실세계에 존재할 것 같은 문자와 다양한 스타일을 cover하는 수많은 synthetic data필요
        
- 본 논문에서는 word box 이미지에 존재하는 다양한 텍스트 모양을 해결하기 위한 STR 생성에 초점을 둔다.
