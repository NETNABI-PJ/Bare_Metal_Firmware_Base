# Bare_Metal_Firmware_Base  
Bare Metal Firmware Base code.  
  
Bare Metal 펌웨어는 Polling 방식으로 구현됩니다.  

지켜야 할 수칙.  
1. Function 수행 시간은 Main Loop 총 누적시간을 준수하여 개발  


2. 기능  
   (1) 모든 로그 및 상태 정보는 100ms 단위로 수집을 수행  
   (2) 저사양 경우 200ms, 500ms, 1s 단위로 설정  
   
3. CPU 사용률 측정방식.  
   (1) 1초 동안 Main Loop 횟수를 기준으로 0% ~ 100% 구분.  
   (2) 측정간격은 100ms (기본)  
   (3) 사용률 기준 방법  
      - 최소한의 MAIN LOOP를 코드를 작성 카운터 된 값을 0%로 백분률 계산  
        (단점 CPU 사용률 0% 표시 불가능, CPU 처리속도 관점으로 본 경우)
      - 기본 구현된 Function Maim loop 카운터값을 0%로 백분률 계산  
        ( CPU 사용률이 0% 표시 가능, 이벤트 처리관점으로 본 경우)
