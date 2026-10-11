# ---------------------------------------------------------------
# 학생 과제: 아래 각 줄이 무엇을 하는지 주석으로 설명을 달아보세요.
# ---------------------------------------------------------------

# 파이썬 3.12 경량화(slim) 버전을 기반 이미지(Base Image)로 지정합니다.
FROM python:3.12-slim

# 컨테이너 내에서 명령어가 실행될 기본 작업 디렉토리를 /app으로 설정합니다.
WORKDIR /app

# 로컬의 requirements.txt 파일을 컨테이너 작업 디렉토리(/app)로 복사합니다.
COPY requirements.txt .

# 캐시를 남기지 않고(--no-cache-dir) requirements.txt에 명시된 파이썬 패키지들을 설치합니다.
RUN pip install --no-cache-dir -r requirements.txt

# 현재 로컬 디렉토리의 모든 소스 파일 및 폴더를 컨테이너 내부로 복사합니다.
COPY . .

# 일반 사용자 계정 'appuser'를 새로 생성(-m: 홈 디렉토리 포함)합니다.
RUN useradd -m appuser

# 보안을 위해 root 대신 방금 생성한 'appuser' 계정으로 사용자를 전환합니다.
USER appuser

# 컨테이너 내에서 사용할 환경변수(앱 제목 및 테마 색상 기본값)를 설정합니다.
ENV APP_TITLE="나만의 특별한 방명록V2" \
    THEME_COLOR="#2E7D32"

# 컨테이너가 5000번 포트를 사용할 것임을 문서화/명시합니다.
EXPOSE 5000

# 컨테이너가 시작될 때 실행할 기본 명령어로 파이썬 애플리케이션(app.py)을 실행합니다.
CMD ["python", "app.py"]
