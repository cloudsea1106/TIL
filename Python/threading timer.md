# 📌threading timer

일정 시간이 지났을 때 함수 실행 / 일정 시간마다 함수 실행

-----------------------



### ✨threading timer

- 일정 시간이 지났을 때 함수 실행

  ```python
  from threading import Timer
  
  def <함수이름>():
      
  	<실행동작>
      
  Timer(<타이머시간(초)>, <함수이름>).start()
  ```

- 일정 시간마다 함수 실행

  ```python
  from threading import Timer
  
  def <함수이름>():
      
      <실행동작>
  	
      Timer(<타이머시간(초)>, <함수이름>).start()
  
  <함수이름>()
  ```

  