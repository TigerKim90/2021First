# 2/1	

- 프로젝트 시작하기(Shopping mall 게시판)

1. 프로젝트 생성

   1) conda prompt에서 프로젝트 생성하기!

   2) 파이참 아래쪽 터미널에서 python manage.py startapp bbs

   3) setting 에서 ALLOWED_HOSTS = ['localhost', '127.0.0.1']

   - Installed_Apps에서 'bbs.apps.BbsConfig' 추가

   4) Templates 밑 dirs에 [os.path.join(BASE_DIR, 'templates')]

   5) TIME_ZONE = 'Asia/Seoul'

   6) 맨 밑에 STATICFILES_DIRS = [os.path.join(BASE_DIR, 'static')]

   7) 파이참 아래쪽 터미널에서 python manage.py migrate

   8) python manage.py runserver

   9) models.py 가서 만들어준다

   ```python
   class Post(models.Model):
       author = models.CharField('작성자', max_length=20)
       contents = models.CharField('내용', max_length=200)
       
   
   ```

   10) admin.py에서 사이트에서 확인할 수 있도록 등록

   ```python
   from django.contrib import admin
   from bbs.models import Post
   
   admin.site.register(Post)
   ```

   11) 그리고 나서 python manage.py makemigration

   그리고 python manage.py migrate



2. 작업 시 주의

- <form> 사용하면 꼭 있어야함. 보안상의 이유
      {% csrf_token %}
  </form>

- 