# week3

### 기초 백엔드 스터디 3주차 ###

- ** MTV 패턴 **
    M : Model (데이터 입출력) / T : Template (응답 내용 관리) / V : View (흐름 제어)

- ** 장고 **
    user -> URL -> view -> templates -> user
    view <-> models
    
- ** URL **
    http(프로토콜), www.~~~.com(주소), 80(포트), /path/to/~ (path to the file), ?key1=value (parameters)

- ** 프로젝트 vs 어플리케이션 **
    프로젝트 - 소프트웨어 전체
    어플리케이션 - 프로젝트 내에서 기능별로 쪼개놓은 단위

- ** 실습 내용 ** (띄어쓰기 ^로 대체)
    1. new terminal
    2. 가상 환경 생성 = python3^-m^venv^venv / 실행 = cd^venv/bin -> source^ activate
    3. 장고 설치 = pip3^install^django
    4. 프로젝트 생성 = mkdir^project
    5. 프로젝트 시작 = django-admin^startproject^config^.
    6. 프로젝트 실행 = python^manage.py^runserver -> 웹에 127.0.0.1:8000 입력
    7. setting.py 변경 = LANGUAGE_CODE = 'ko-kr' / TIME_ZONE = 'Asia/Seoul'
    8. 어플리케이션 생성 = django-admin^startapp^questions
    9. setting.py 앱 등록 = 'questions.app.QuestionsConfig' 입력
    10. urls.py = from^questions^import^views 추가 / path('questions/',views.index), 추가
    11. views.py = def^index(request): render(request,'index.html') 추가
    12. templates 만들기

- ** 명령어 요약 **
    - cd (change directory)
    - mkdir (make directory)
