# SynthTIGER
## 1. Introduction

- image와 text 쌍을 포함한 large-sacel data를 통해 학습함으로써 OCR의 성능이 dramatically하게 향상되었다. 일반적으로 텍스트 길이나, 폰트, 배경 등의 다양한 특징의 조합들을 cover할 수 있는 real text이미지를 모으고 어노테이션하기는 불가능하기 때문에, OCR은 synthetic text image를 포함한 large-scale data를 사용한다.
- OCR에는 두가지 task가 있다. Scene Text Detatcin(STD)와 Scene Text Recognition(STR)이다.
    - STD : 배경으로 부터 text araea를 laoclize
        
        학습이미지는 다양한 텍스트를 포함한 raw scene또는 document snapshot
        
    - STR : single word나  line of word를 포함한 word box image path로 부터 문자 sequence를 식별
        
        실세계에 존재할 것 같은 문자와 다양한 스타일을 cover하는 수많은 synthetic data필요
        
- 본 논문에서는 word box 이미지에 존재하는 다양한 텍스트 모양을 해결하기 위한 STR 생성에 초점을 둔다.
- synthesis engine에는 두가지 유명한 engine이 있다. MJ와 ST
    - MJ : 여러개의 rendering module(font rendering, border/shadow rendering, base-color rendering, projective distortion, neatural data blending, noise injection) 처리를 통해 word box 이미지를 생성, 즉 scene text image보다 wor box이미지 생성에 초점
        
        ➕ : 여러 모듈을 통해 모든 텍스트 스타일을 control가능 
        
        ➖ : 살제 장면이미지로부터 cropped된 text region을 완전히 표현할 수 없음
        
    - ST : 하나의 scene 이미지 안에 여러개의 word box들을 포함한 scence text image를 생성, text region을 식별하고, 여러 랜더링을 통해 region위에 text를 작성
        
        ➕ : word box는 scene text image로부터 crop되었기 때문에, 식별된 word box image는 real STR 예시처럼 다른 word box의 text noise를 포함할 수 있음
        
        ➖ : 텍스트 렌더링을 위해 식별된 배경 영역이 일부 텍스트 렌더링 기능과 호환되지 않을 수 있기 때문에 텍스트 스타일을 선택하는 데 제약 존재
        
- ⇒ SynthTIGER이 MJ와  ST, MJ + ST보다 성능이 높았음
    : MJ(스타일 제약 없이 word box생성) + ST(다른 텍스트 영역으로부터noise 존재)
    
- 빈도가 낮은 길거나 짧은 단어에 대한 왜곡된 데이터 분포를 완화하기 위해 두가지 방법 제안
    - length augmentation & infrequent character augmentation