# Pandas

- Pandas는 2개의 자료구조를 사용한다.
- Numpy를 기본으로 한다.
- Series와 DataFrame이라는 자료구조를 정의해서 사용한다.



## 1. Series 

- 동일한 데이터 타입의 복수개의 성분으로 구성

- ndarray + 알파인 자료구조이다.

- 1차원 자료구조

- 같은 데이터 타입이 들어와요(문자도 가능,Numpy는 숫자만 가능)

- s = pd.Series([])

- s = pd.Series([1,2,3,4,5],dtype=np.float64)

  == > 이런식으로 만든다. Series는 클래스

  ```python
  0    1.0
  1    2.0
  2    3.0
  3    4.0
  4    5.0
  dtype: float64
  앞은 Index 뒤는 값
  ```

- 값만 가져오고 싶으면 ==>

  ``` python
  print('Series의 값만 가져오고 싶어요 : {}'.format(s.values))
  ```

- Series에서는 Index를 문자로도 만들 수 있다.

  ```python
  s = pd.Series([1,5,8,10], dtype=np.int32, index=['a','b','c','d'])
  여기서 5의 값을 얻고 싶으면 Index를 소환한다.
  print(s['b']), print(s[1]) 숫자Index는 유효하다.
  ```

- Slicing (데이터 일부만 가져오는거)

```python
s = pd.Series([1,5,8,10], dtype=np.int32, index=['a','b','c','d'])
print(s['a':'d']) => [1,5,8]만 나와야하는데, 문자열일 경우 [1,5,8,10] 전부 나온다.
```

- Fancy Indexing

``` python
print(s[[0,2]]) [] list 형태의(0,2 두개이기때문에) 데이터를 뽑아온다. 
```

- boolean indexing

```python
print(s[s%2 == 0])
```

- Series를는 dict를 이용해서 만들수도 있다.

```python
my_dict = {'서울' : 1000, '인천' : 2000, '수원' : 3000}

s = pd.Series(my_dict)
print(s)
s.name = '지역별 가격 데이터'
s.index = ['Seoul', 'Incheon', 'Suwon']
s.index.name = '지역명'
```





## 1). 날짜 관리하기

```python
from datetime import datetime

start_day = datetime(2020,1,1)
```



# 2. DataFrame 

-  Table 형식으로 데이터를 저장하는 자료구조
- Dict을 이용해서 dataframe 만든다.
- 출력할 때 Print() 대신 display()를 사용한다.

```python
my_dict = { 'name' : ['홍길동','신사임당','김연아','강감찬'],
          'year' : [2015, 2016, 2019, 2016], 
          'point' : [3.5, 1.4, 2.0, 4.5]}

df = pd.DataFrame(my_dict)
display(df)
print(df.shape)
print(df.size)
print(df.ndim)
print(df.index)
print(df.columns)
print(df.values) --> 데이터만 뽑아서 2차원 np형태로 출력
df.index.name = '학생정보'
df.
                      
                
```

- Dict로는 아주 작은양의 데이터를 처리할때만 적합하다.

- 많은 양의 데이터는 파일, Database, Open API를 이용해서 얻는다.

- 일반적으로 많이 사용되어지는 데이터 표현방식(3가지)

  #### 1. CSV(Comma Seperated Valuese)

  ex) 홍길동,20,서울,김길동,30,인천,최길동,50,제주

  - 데이터의 크기가 크고, 데이터가 잘 변하지 않는 경우 사용

  장점 : 용량이 작다. 많은 데이터를 표현하기에 적합

  단점 : 데이터 구성을 알기 어렵다. 구조적 표현이 힘들다.

  ​          사용이 힘들다, 데이터처리를 위해 따로 프로그램을 만들어야 한다.데이터가 변경되면 프로그램도 변경 ==> 유지보수 문제

  #### 2. XML(eXtended Markup Language)

  ex) <person><name>홍길동</name><age>20</age><address>서울</address></person>

  장점 : 구성을 알기 쉽다. 사용하기 편하다. 유지보수가 쉽다.

  단점 : 부가적인 데이터가 많다. 

  #### 3. JSON(JaveScript Object Notation) : 가장 일반적인 방식

  예) { name : '홍길동', age : 20, address : '서울' }

  장점 : 데이터 구성을 알기 쉽다. 사용하기 편하다. 유지보수 쉽다.

  단점 : CSV 보다는 데이터가 많다. 

  # 3. MY SQL

  cmd로 들어가서 mysqld

  종료할 때는 새로 cmd 들어가서 bin폴더 주소 들어가서 

  mysqladmin -u root shutdown