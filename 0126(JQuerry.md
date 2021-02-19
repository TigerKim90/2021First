# 1/26

# jQuery

- Bootstrap 사용해서 example 중에 한 가지 Frame 골라서 사용한다.

- ```javascript
  $(document).on('ready',function(){
      $('h1').on('click',function(event){
          alert('클릭')
      })
  
  })
  
  $(documnet).ready()   << 이렇게 사용한다. document는 html을 전부 읽은 뒤 함수를 적용한다. 원래는 html을 읽는 순서로 함수가 호출된다.
  ```

