# GPT-SoVITS - 캐릭터 음성 학습 및 추론 프로젝트


본 프로젝트는 GPT-SoVITS를 활용하여 캐릭터 음성을 학습하고, 텍스트를 해당 캐릭터 음성으로 추론하는 음성 합성 시스템입니다.  
캐릭터 종류 : **짱구, 케로로, 코난**

<br>

---

## 프로젝트 구조

```
GPT-SoVITS/
├── GPT_SoVITS/
│   ├── pretrained_models/     # 사전학습 모델 위치
│   ├── inference_cli.py       # 추론 CLI
│   └── download.py            # 기타 리소스 다운로드
├── webui.py                   # WebUI 실행 파일
├── requirements.txt           # 의존 패키지 목록
└── logs/                      # 학습 로그
```

<br>

---


## 사용한 데이터

- **데이터 유형** : 직접 수집한 음성 조각 파일
- **수집 대상** : 캐릭터별 음성 (케로로, 코난, 짱구)
- **파일 구성** : **3~10초 분량**의 짧은 클립으로 구성
- **총 분량** : 캐릭터당 약 45분


<br>

---

## 학습 파라미터
    
- SoVITS
  - 배치 사이즈 : 1
  - epochs : 10
  - LoRA Rank : 32
    
- GPT
  - batch size : 7
  - total epochs : 30
  - Enable DPO training


<br>

---



## 케로로

**입력 텍스트**  
저는 케롱별에서 온 케로로 중사라고 합니다. 전 퍼렁별 침략을 위해서 왔죠.


### GPT-SoVITS V4


https://github.com/user-attachments/assets/5caae9b8-c606-4aa2-ae1c-2415cd6fece1



### GPT-SoVITS V2ProPlus

- reference X  

https://github.com/user-attachments/assets/a486b46d-c149-4f3a-bb3b-c2b395b1800e


- reference O  

https://github.com/user-attachments/assets/1c00dff0-374c-414f-afbc-237c1879393d

<br>

---

## 코난

**입력 텍스트**  
안녕하세요. 제 이름은 코난, 탐정이죠. 오늘은 또 무슨 일이 벌어질까 궁금하네요.

### GPT-SoVITS V4


https://github.com/user-attachments/assets/341edb6f-8957-469f-bbc8-8388644c576c



### GPT-SoVITS V2ProPlus

- reference X  


https://github.com/user-attachments/assets/1ebeb000-1473-460d-9db2-9bda95c3941e



- reference O  


https://github.com/user-attachments/assets/39505ab9-2cc9-4d10-bb76-46628586711e

<br>

---

## 짱구

**입력 텍스트**  
안녕, 나는 짱구! 너도 액션가면 좋아해? 그럼 우리 흰둥이 산책 시키고 같이 액션가면 볼래?


### GPT-SoVITS V4 


https://github.com/user-attachments/assets/a2b3efb3-8cfc-47b5-a5de-1af520624ea6




### GPT-SoVITS V2ProPlus

- reference X  


https://github.com/user-attachments/assets/1492c268-eb7b-42f7-b766-10df91bfe5de



- reference O  


https://github.com/user-attachments/assets/6d5277e0-62ef-43ea-bc62-c976f7635232

<br>

---

## 최종 비교 및 결론

**성능 순위**  
GPT-SoVITS V2ProPlus < GPT-SoVITS V4

-> GPT-SoVITS V4가 loss 수렴, 진동 폭, 음질에서 가장 우수한 성능을 보임





---

<br>

## 추론 CLI 예시

```bash
mkdir -p output

PYTHONPATH=/content/GPT-SoVITS \
python /content/GPT-SoVITS/GPT_SoVITS/inference_cli.py \
  --gpt_model conan_v4-e30.ckpt \
  --sovits_model conan_v4_e5_s3205_l32.pth \
  --ref_audio conan1.wav \
  --ref_text 1.txt \
  --ref_language "韩英混合" \
  --target_text target.txt \
  --target_language "韩英混合" \
  --output_path output
```

> `韩英混合`는 한국어-영어 혼합을 의미하며, 필요 시 `inference_cli.py`에 직접 지정해줘야 합니다.



<br>

---

## 관련 자료

- [프로젝트 결과 정리 (Notion)](https://typhoon-psychology-bec.notion.site/TTS-21b87aeb4a27801fa484d63873acb4fb?pvs=74)
- [모델 다운로드 (Hugging Face)](https://huggingface.co/gahyunlee/GPT-SoVITS-ko-character)

---
