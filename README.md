# 코딩규칙 250305
01.　 a = array variable　　　　　　e.g. a_Data[]  
02.　 b = bit fields　　　　　　　　 e.g. b_Data  
03.　 c = const　　　　　　　　　　　e.g, c_Data  
04.　 d = define　　　　　　　　　　 e.g. d_Data  
05.　 e = enum Type　　　　　　　　 e.g. e_Data  
06.　 f = Function　　　　　　　　　e.g. f_Data  
07.　 g = file global　　　　　　　 e.g. gv_Data (static)   
08.　 i = Inline　　　　　　　　　　e.g. i_Data  
09.　 l = local static variable　　e.g. lv_Data  
10.　 m = enum member　　　　　　 　e.g. m_Data  
11.　 p = Pointer　　　　　　　　 　e.g. p_Data  
12.　 s = struct　　　　　　　　　　 e.g. s_Data  
13.　 t = typedef　　　　　　　　　　e.g. t_Data  
14.　 u = Union　　　　　　　　　　　e.g. u_Data  
15.　 v = variable　　　　　　　　　 e.g. v_Data  
16.　 x = Extern variable　　　　 　e.g. xv_Data  

1) 접두어사용 소문자_  이게 변수인지 함수이지 바로 알기 위해 위에표 기준으로 작성
2) 헤더 파일에 (*.h) 내부 Define은 다음과 같이 정의  
   D_CODEC_H   파일명은 Codec.h 이며 d는 헤더파일 Define 시 대문자로 표기  
   이는 일반 d_ 하고 구분하기 위한 조치  
   #ifndef D_CODEC_H   
   #define D_CODEC_H   
4) 헤더 파일은 2가지로 지정  
   - xxxx_type.h 헤더파일  
   Struct, enum 는 데이터 형태만 선언 순수 데이터 구조만 사용  
   type.h 내부에 다른 type.h를 참조금지  
   다른 Type을 참조 하면서 struct 등 만들어야 되는 경우는   
   xxxx.h 헤더파일에 작성.  

   - xxxx.h 헤더 파일  
   함수타입선언 과 extern을 사용  
   소스코드상에 extern 사용 금지 헤더를 통해서 변수를 공유  

5) 소스코드 내에서 변수 공유는 함수를 통해 변수를 접근.  
   xxxxx_Set();  
   data = xxxxx_Get();   
   
# Bare_Metal_Firmware_Base  
Bare Metal Firmware Base code.  
Bare Metal Firmware Base 는 NOOS로 별칭으로 이야기 하겠습니다.  

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
      - 1안. 최소한의 MAIN LOOP를 코드를 작성 카운터 된 값을 0%로 백분률 계산  
             (단점 CPU 사용률 0% 표시 불가능, CPU 처리속도 관점으로 본 경우)
      - 2안. 기본 구현된 Function Maim loop 카운터값을 0%로 백분률 계산  
             ( CPU 사용률이 0% 표시 가능, 이벤트 처리관점으로 본 경우)
4. BASE TIME  
   (1) DWT(Debug Waitch Timer): 32Bit 카운터 Cortex-M4 급 이상  
   (2) SYSTICK : 24Bit 카운터
   (3) CNTPCT_EL0 : 64Bit 카운터 /2분주비 클럭소스 선택 (미확인)
   
