# week5

### 기초 백엔드 스터디 5주차 ###

- ** Model의 역할 **
    models.py에 클래스 생성 시, 장고가 클래스를 토대로 DB 테이블을 생성한다.
    DB 테이블에서 값을 조회할 때 models.py에 만들어놓은 클래스의 객체에 값을 담아 반환한다.

- ** Class와 객체 **
    models.py에 만들어놓은 클래스 / DB에서 정보를 조회하면 만들어지는 객체
    클래스에 따라 객체가 만들어진다

    models.py에 만들어놓은 클래스 / 장고는 클래스를 보고 DB 테이블을 만든다
    장고는 조회한 데이터를 넣은 객체를 만든다.

- ** SQL vs ORM **
    Structured Query Language vs Object Relational Mapping

- ** 장고 ORM 사용법 **
    - 클래스이름(e.g. Student).objects 를 이용해 DB에 저장된 값에 접근한다.
    - 클래스이름(e.g. Student).objects.all()이라는 함수를 사용하면 모든 테이블 정보를 객체로 만들어 리스트에 넣어 반환한다.
    - 클래스이름(e.g. Student).objects.get()이라는 함수를 사용하면 조건에 맞는 데이터를 객체로 만들어 반환한다.
    - 클래스이름(e.g. Student).objects.filter()이라는 함수를 사용하면 조건에 맞는 정보들을 객체로 만들어 리스트에 넣어 반환한다.

- ** 동적 html 생성 **
    def index(request):
        name = 'KIM'
        context = {'name' : name}
        return render(request, 'index.html', context)
    
    - render 함수 html 파일 경로 뒤(여기서는 context)에는 html에 넣고 싶은 정보를 딕셔너리에 담아 넘겨줄 수 있다.
    - render 함수 앞의 request는 장고에서 만들어서 넣어준 HTTP request 객체
    - render 함수 2번째 인자는 응답할 html 파일 이름(여기서는 'index.html')
    - render 함수 3번째 인자는 html 파일에서 사용할 딕셔너리(여기서는 context)

- ** HTML **
    HTML은 우리가 보는 웹페이지가 어떻게 구조화되어 있는지 브라우저로 하여금 알 수 있도록 하는 마크업 언어. - 태그를 이용해 내용을 꾸미거나 기능을 추가한다.

- ** CSS **
    웹페이지를 꾸미려고 작성하는 코드
    HTML의 요소에 선택적으로 스타일을 적용할 수 있다 - HTML로 뼈대를 만들고 CSS로 살을 붙임(CSS는 프론트엔드의 일)

- ** 간단한 태그 **
    - h1, h2, h3 : 제목 생성 (폰트 크기 h1 > h2 > h3)
    - p : 문단 생성 (앞 뒤로 붙임)
    - a : 하이퍼링크 걸어줌 (앞 뒤로 붙임)
    - ul, ol, li : li 리스트 만들어주는 태그 (ol - ordered, ul - unordered)
    - div : 레이아웃 나눔 (CSS와 함께 사용)
    - form, input : 데이터 입력(input) 및 전송(form) 태그

- ** 장고 템플릿 **
    장고 HTML 동적 생성 가능 but 태그는 만들 수 없음 -> 태그 안의 내용을 동적으로 바꿔줄 수 있음 => {{key}} 넣어 사용할 수 있다.
    객체 내부 데이터에 접근하려면, '객체이름.객체변수이름'으로 사용한다.

- ** 실습 **
    1. 가상환경 실행 필수 - cd venv/bin -> source activate
    2. DB 내용 전달
    def question_detail(request, question_id):
        question = Question.objects.get(id = question_id)
        context = {'question' : question}
        return render(request, 'question_detail.html', context)

    3. TEMPLATE 생성
    <h1>{{question.subject}}</h1>
    <p>{{question.content}}</p>
    <p>{{question.created_date}}</p>

    4. 하이퍼링크 HTML 생성
    <ol>
      {% for question in questions %}
      <a href="/questions/{{question.id}}"><li>{{question.subject}}</li></a>
      {% endfor %}
    </ol>
    //<a>사이에 리스트 삽입</a>

    5. urls.py
    path('questions/<int:question_id>/', views.question_detail), 삽입
