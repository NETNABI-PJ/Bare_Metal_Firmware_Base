# Bare_Metal_Firmware_Base
Bare Metal Firmware Base code.

Bare Metal 펌웨어는 Polling 방식으로 구현됩니다.

지켜야 할 수칙.
1. Function 수행 시간은 Main Loop 총 누적시간을 준수하여 개발



CPU 사용률 측정방식.
1. 1초 동안 Main Loop 횟수를 기준으로 0% ~ 100% 구분.
2. 측정간격은 100ms 단위로 측정.
3. 사용률 기준 방법
   - 최소한의 MAIN LOOP를 코드를 작성하여 
