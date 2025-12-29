# HappyNewYear

# 🎍 새해 덕담 주고받기 프로젝트

새해를 맞아,  
**랜덤한 덕담을 메일로 받고, 다시 덕담을 남길 수 있는 간단한 웹 서비스**입니다.

회원가입 없이 이메일만으로 참여할 수 있고,  
누군가에게 받은 덕담에 다시 한마디를 남기는 흐름에 초점을 맞췄습니다.

---

## ✨ 주요 기능

- 📩 이메일 입력 시 **랜덤 새해 덕담 메일 발송**
- 🔁 메일 내 링크를 통해 **덕담 남기기**
- 🗂️ 주인장 전용 페이지에서 **받은 덕담 확인**
- 🛠️ Django Admin에서 덕담 문구 관리 가능

---

## 🖥️ 기술 스택

### Backend
- Python 3.12
- Django 6.0

### Mail
- Gmail SMTP (App Password)

### Deployment
- AWS EC2 (Ubuntu 22.04)
- Gunicorn
- Nginx
- systemd

### Database
- SQLite

---

## 🗺️ 서비스 흐름

1. 사용자가 사이트에 접속
2. 이메일 입력 후 덕담 받기
3. 서버에서 랜덤 덕담 선택 → 메일 발송
4. 메일의 “나도 덕담하기” 버튼 클릭
5. 덕담 작성 후 전송
6. 주인장 인박스 페이지에 누적 저장

---

## 📁 프로젝트 구조

```

HappyNewYear/
├── config/
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── blessings/
│   ├── models.py
│   ├── views.py
│   ├── templates/
│   └── admin.py
├── staticfiles/
├── manage.py
└── venv/

````

---

## 🗃️ 데이터 모델

### PresetBlessing
- 미리 준비된 덕담 문구
- 활성화된 덕담만 랜덤 선택

### UserBlessing
- 사용자가 남긴 덕담
- 작성자 이메일과 내용 저장

---

## ⚙️ 환경 변수 설정

서비스 실행을 위해 아래 환경 변수가 필요합니다.

```env
DJANGO_SECRET_KEY=your-secret-key
DJANGO_DEBUG=0
DJANGO_ALLOWED_HOSTS=15.164.221.89,localhost,127.0.0.1

SITE_BASE_URL=http://15.164.221.89

EMAIL_HOST_USER=god.gy0321@gmail.com
EMAIL_HOST_PASSWORD=gmail-app-password
````

> ⚠️ Gmail SMTP는 **앱 비밀번호(App Password)** 사용이 필수입니다.

---

## 🚀 로컬 실행 방법

```bash
python -m venv venv
source venv/bin/activate

poetry install

python manage.py migrate
python manage.py collectstatic
python manage.py runserver
```

---

## 🧱 배포 관련 메모

* Gunicorn은 systemd 서비스로 등록
* 환경변수는 `/etc/*.env` 파일을 통해 전달
* IP 기반 HTTP 서비스로 운영 중
  (도메인 + HTTPS는 추후 적용 예정)

---

## ⚠️ 주의 사항

* 대량 메일 발송 시 Gmail SMTP 제한에 걸릴 수 있습니다.
* 현재는 간단한 프로젝트 성격으로 rate limit을 두지 않았습니다.

---

## 📝 프로젝트 목적

* 아이디어 → 구현 → 배포 → 실제 사용까지의 **완주 경험**
* Django 기반 서비스 배포 전 과정 정리
* 복잡하지 않은 구조로도 충분히 “쓸 수 있는 서비스” 만들기

---

## 📌 앞으로 개선할 점

* 도메인 연결 및 HTTPS 적용
* 메일 템플릿 디자인 개선
* 스팸 방지용 rate limit 추가

---

## 📬 미리보기

현재 서비스는 아래 주소에서 확인할 수 있습니다.

```
http://15.164.221.89
```

(HTTPS는 추후 적용 예정)

---

## 🙌 마치며

기술적으로 대단한 서비스는 아니지만,
작은 아이디어를 실제로 배포하고 사람들이 사용할 수 있게 만드는 경험을 목표로 한 프로젝트입니다.

