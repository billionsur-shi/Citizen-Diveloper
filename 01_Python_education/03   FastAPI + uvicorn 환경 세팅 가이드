# 🚀 FastAPI + uvicorn 환경 세팅 가이드

ML 모델을 API로 서빙하기 위한 Python 가상환경 세팅 가이드입니다.

---

## 📁 가상환경 구조

| 환경 | 용도 |
|------|------|
| `venvPython1` | 데이터 분석, 모델 학습 (`pandas`, `sklearn` 등) |
| `venvPython2` | 모델 서빙 전용 (`fastapi`, `uvicorn`) |

> 환경을 분리하면 패키지 버전 충돌 없이 배포 환경을 깔끔하게 유지할 수 있습니다.

---

## ⚙️ 환경 전환 방법

```powershell
# 현재 환경 비활성화
deactivate

# venvPython2 활성화
& d:\venv\venvPython2\Scripts\Activate.ps1
```

프롬프트가 `(venvPython2) PS D:\venv>` 로 바뀌면 성공입니다.

---

## 📦 패키지 설치

```powershell
pip install fastapi
pip install "uvicorn[standard]"
```

### FastAPI란?
어떻게 요청을 처리할지 **정의하는 프레임워크**입니다. (레시피 역할)

### uvicorn이란?
실제로 HTTP 요청을 **받아서 FastAPI에 전달하는 서버**입니다. (서버 역할)

> `[standard]` 옵션: websockets, httptools 등 고성능 옵션이 포함된 버전. 실제 서비스 배포 시 권장.

---

## 🏗️ ML 모델 서빙 흐름

```
[클라이언트 요청]
      ↓
   uvicorn        ← 실제 HTTP 서버 역할
      ↓
   FastAPI        ← 요청 파싱 & 라우팅
      ↓
  ML 모델 예측    ← predict() 호출
      ↓
  결과 반환 (JSON)
```

---

## 💡 예시 코드

```python
from fastapi import FastAPI
import pickle

app = FastAPI()
model = pickle.load(open("model.pkl", "rb"))

@app.post("/predict")
def predict(data: dict):
    result = model.predict([data["features"]])
    return {"prediction": result[0]}
```

---

## 🛠️ Data Science 팁

- `pip list` — 현재 환경에 설치된 패키지 확인
- `pip freeze > requirements.txt` — 환경 스냅샷 저장 (재현 가능한 실험 환경 구성)
