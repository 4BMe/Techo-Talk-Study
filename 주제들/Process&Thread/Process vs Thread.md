# Process vs Thread

### 1. Process & Thread

​	Process 가 실행 되면 Memory에 Process 실행에 필요한( code data heap stack ) 들이 올라감

​	그리고 Process에 대한 정보를 가지고 있는 Process Control Block가 생성됨

​	여러 프로그램을 동시에 실행하면 각 Process 들이 조금씩 번갈아가면서 실행이 됨 =>context switch

​	이러한 Context Switch 비용을 줄이기 위해 경량화된 Thread가 이용됨

​	Thread는 부모 Process의 ( code data heap )을 공유하고 각자의 stack만 구분해서 사용함 => 캐시적중률 상승



### 2.Multi-Process & Multi-Thread

​	M_P

​	여러 작업을 해야하는 경우 M_P는 부모 Process가 Fork를 하여 작업을 수행

​	각 프로세스가 독립적 / IPC 통신 / 자원소모, 개별 메모리 / Context Switch 비용이 큼 / 동기화 덜필요

​	Thread는 한 Process 내에서 구분지어진 실행 단위 M_T는 

​	각 쓰레드가 연결 / 공유된 자원으로 통신 비용 절감 / 공유자원으로 메모리 효율적 / C S 비용이 적음 / 공유자원 관리(동기화) 필요



​	M_P는 하나가 나가도 문제 없음 M_T는 하나가 뻑나면 나머지도 뻑



### 3. Multi-Core

​	하드웨어 측면의 동시성과 병렬처리



### 4. 리눅스에서 Process와 Thread

​	Thread는 사용자와 커널로 나뉘어짐

​	커널과 사용자간의 연관 관계 대다대 1대1 등등

​	리눅스는 1대1 모델을 이용. 때문에 각각의 Thread 가 하나의 프로세스임 근데 이전과 다르게 Process간 메모리를 공유해서 이를 light weight process라고 부름 

​	리눅스의 PID에는 TGID와 TID 가 있음 사용자는 TGID가 PID 커널은 TID가 PID가 됨  