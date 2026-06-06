**✅ IPv4**  
인터넷에서 사용하는 32비트 주소 체계 (예: 192.168.0.1)
약 43억 개 주소를 지원하지만 주소 고갈 문제가 있음
점(dot)으로 구분된 4개의 10진수로 표현

**✅IPv6**  
128비트 주소 체계로, 사실상 무한대에 가까운 주소 공간 제공
IPv4 고갈 문제를 해결하기 위해 개발됨
콜론(:)으로 구분된 8개의 16진수 그룹으로 표현

**✅Socket**  
네트워크 상에서 통신을 위한 양쪽 끝단(End-point)
IP주소 + 포트번호를 통해 연결을 설정하고 데이터 전송
TCP, UDP 등 다양한 프로토콜 기반 통신에 사용

**✅Node**  
네트워크에 연결된 하나의 장치 또는 컴퓨터를 의미
각각 고유한 IP 주소를 가짐
서버, 클라이언트, 라우터 등이 모두 노드에 해당

**✅Hub**  
여러 장치를 단순히 연결하는 기본 네트워크 장치
들어온 데이터를 모두 연결된 포트로 그대로 전달 (브로드캐스트)
지능이 없어 충돌이 자주 발생함 (효율성 낮음)

**✅TCP (Transmission Control Protocol)**  
연결 기반(신뢰성 있는) 통신 프로토콜
데이터 전송 시 순서 보장, 오류 검출 및 재전송 기능 제공
웹, 이메일, 파일 전송 등에 사용 (HTTP, FTP 등)

**✅UDP (User Datagram Protocol)**  
연결 없는(비신뢰성) 통신 프로토콜
빠르지만 데이터 순서 보장이나 재전송을 하지 않음
스트리밍, 게임, 실시간 통신 등에 주로 사용  

**📕 ROS2 통신 구조**  
**📖 Topic (토픽)**  
- 1:N 통신 구조 (Publisher 1명, Subscriber 여러 명 가능)
- 하나의 토픽을 여러 노드가 동시에 구독할 수 있음
- 비동기식 → 발행자는 수신 여부 신경 안 씀, 계속 송출만 함

**📖 Service (서비스)**  
- 1:1 통신 구조 (Client <-> Server)
- 요청을 보내는 쪽과 응답하는 쪽이 명확히 1:1로 연결됨
- 동기식 → 요청을 보내면 결과를 기다릴 때까지 블로킹(멈춤)

**📖 Action (액션)**  
- 기본적으로 1:1 통신 구조 (Client <-> Server)
- 하지만 목표(Goal)를 보내고, 진행 상황(Feedback)과 결과(Result)를 비동기로 주고받음
- 비동기형 → 작업 중간에 취소하거나, 결과를 기다리며 다른 일도 가능  


**✅ ROS1 vs ROS2 비교**

1. 통신 프로토콜:  
    ◦ ROS1: TCP/IP 기반, Pub/Sub 방식.  
    ◦ ROS2: DDS(데이터 분산 시스템) 기반, 고급 통신 기능 지원.  

2. 실시간 지원:  
    ◦ ROS1: 실시간 성능 미지원.  
    ◦ ROS2: 실시간 성능 지원, RTOS 사용 가능.  

3. 보안:  
    ◦ ROS1: 보안 기능 미지원.  
    ◦ ROS2: 보안 기능 내장, 데이터 암호화 및 인증 지원.  

4. 멀티 플랫폼:  
    ◦ ROS1: Linux 중심.  
    ◦ ROS2: Linux, Windows, MacOS 지원.  

5. 노드 관리:  
    ◦ ROS1: 기본적인 노드 관리.  
    ◦ ROS2: 고급 노드 관리 및 분산 시스템 지원.  

6. 버전 및 업데이트:  
    ◦ ROS1: 정기적인 업데이트와 지원 종료 예정.  
    ◦ ROS2: 지속적인 업데이트와 롱텀 서포트(LTS) 제공.  

**✅ ROS2 interface 패키지**  
- msg, srv, action 파일을 정의하는 전용 패키지
- 토픽, 서비스, 액션 노드 간의 통신을 위해 데이터 구조를 정의하는 목적으로 사용
- 일반적으로 다른 패키지에서 재사용할 수 있도록 인터페이스만 따로 분리  


**✅ 패키지 설계 흐름**  
- 패키지 생성 : `ros2 pkg create 패키지명 --build-type ament_python # 또는 ament_cmake`
- 생성된 패키지 내 코드 작성(python or c++)
- 실행 설정 파일 수정
- Python : setup.py + package.xml   
    ◾`setup.py`에서 실행할 스크립트를 entry point에 등록  
    ◾`package.xml`에서 의존성(`rclpy`)등 설정  
- C++ : CMakeLists.txt + package.xml  
    ◾`CMakeLists.txt`에서 add_executable() 및 install(TARGETS) 설정  
    ◾`package.xml`에 의존성 추가 (`rclcpp`, `std_msgs` 등)  
- 빌드(Build) : `colcon build --packages-select 패키지명(파이썬)  # 또는 패키지명(C++)`  
    ◾빌드 후에는 꼭 환경설정하기 : `source install/setup.bash`  
- 실행(Run) : `ros2 run 패키지이름 실행파일이름`  

**✅ package.xml**  
- ROS 패키지의 기본 정보와 의존성을 정의하는 파일  
- 누가 만들었는지, 어떤 기능을 포함하는지, 어떤 라이브러리를 사용하는지를 명시  
- 인터페이스 패키지의 경우, 메시지 생성과 관련된 패키지에 의존성을 반드시 추가  

**✅ CMakeLists.txt**  
- 실제로 인터페이스 파일을 빌드하고, 사용할 수 있도록 변환해주는 설정 파일  
- `.msg`, `.srv`, `.action` 파일을 컴파일해서 ROS에서 사용할 수 있는 형태로 만들어 줌  
- 인터페이스를 사용할 다른 패키지가 참조할 수 있게 연결도 관리  

**✅ setup.py**  
- 파이썬으로 작성된 ROS 노드를 만들 때 사용하는 설정 파일   

**✅ rclpy란?**  
> ROS 2의 Python 클라이언트 라이브러리로, Python 코드에서 ROS2 기능을 사용할 수 있도록 해주는 인터페이스.  
> Node, Publisher, Subscriber, Service, Action 등을 구현할 수 있음.  
- Node: ROS2 실행 단위, 이름을 가지고 pub/sub/service 등 수행
- Publisher / Subscriber: 토픽 기반 비동기 통신
- Service / Client: 요청-응답 구조의 동기 통신
- Action: 장시간 작업을 위한 Goal/Feedback/Result 통신 구조
- Parameter Server: 노드 설정 값을 동적으로 관리  

**✅ Executor & Multi Thread**  
> 콜백(callback) 함수들을 실행시키는 역할을 담당하며, ROS2의 핵심 실행 구조.  
> 노드가 이벤트(토픽 수신, 서비스 요청, 타이머 등)를 감지하면 해당 콜백을 실행함.  
- `rclpy.spin(node)`: 단일 노드 실행
- `MultiThreadedExecutor()`: 여러 콜백을 병렬로 실행
- 긴 콜백으로 인해 지연이 생기지 않도록 병렬 처리에 활용
- 주의: 타이머 주기를 너무 짧게 설정 시 CPU 부하 발생 가능  

**✅ launch 프로그래밍**  
> 여러 노드를 한 번에 실행하고, 인자나 설정을 함께 전달할 수 있는 ROS2 실행 스크립트.  
- 파일형식: `.launch.py`
- 노드 실행 자동화, 로그 관리, 파라미터 전달 등을 수행  

**📕 ROS2 Bag 파일이란?**  
- ROS2 시스템에서 주고받는 **토픽 데이터를 저장(기록)하고 재생할 수 있는 기능**
- 센서, 로봇 상태, 카메라 등 다양한 토픽 메시지를 데이터베이스 형태로 저장
- 모델 테스트나 시뮬레이션을 재현할 때 유용 (ex. 동일 데이터로 재학습, 재검증 가능)

**🎥 핵심 명령어 정리**  
✅ ros2 bag record  
- 현재 퍼블리시 중인 토픽 데이터를 **기록(record)**
- 예)  `ros2 bag record /turtle1/cmd_vel -o turtle_bag`  
              → `/turtle1/cmd_vel` 토픽 데이터를 `turtle_bag` 파일로 저장  
- 여러 토픽을 동시에 기록 가능 (`ros2 bag record /topic1 /topic2 /topic3`)
- 실행 중지 시 `Ctrl + C`로 종료, `.db3` 파일이 생성됨  

✅ `ros2 bag play`  
- 기록된 Bag 데이터를 **재생(play)** → 저장된 `/turtle1/cmd_vel` 토픽 데이터를 동일한 주기로 재전송
- 실제 센서나 로봇이 없어도 동일한 데이터 흐름을 재현

✅ `ros2 bag info`  
- Bag 파일의 토픽 이름, 타입, 메시지 수, 시작/종료 시간 등을 조회  


**📕 인터페이스 패키지**  
**📘 인터페이스(Interface)**  
- ROS2에서 노드(Node) 간 통신 시 사용하는 데이터 형식 정의
- “어떤 데이터를 어떤 구조로 주고받을지”를 정의하는 역할  


**📘 3가지 인터페이스 종류**  
| 종류 | 사용 통신 | 특징 | 사용 예 |
| :--- | :--- | :--- | :--- |
| .msg | Topic | 단방향 데이터 전달 | 센서 데이터 |
| .srv | Service | 요청 → 응답 구조 | 두 숫자 더하기 |
| .action | Action | 장시간 작업 처리 | 로봇 이동 |

**📘 Topic / Service / Action 차이**  
| 종류 | 특징 | 통신 구조 | 사용 예 |
| :--- | :--- | :--- | :--- |
| Topic | 지속적인 데이터 송수신 | Publisher ↔️ Subscriber | 카메라, 센서 데이터 |
| Service | 요청 후 즉시 응답 | Request ↔️ Response | 계산기 기능 |
| Action | 오래 걸리는 작업 처리 | Goal/Feedback/Result | 로봇 이동, 경로 추적 |

**📘 인터페이스 패키지를 따로 만드는 이유**  
여러 패키지에서 공통으로 사용할 msg / srv / action 파일을 별도로 관리하기 위함  
```
my_robot_interfaces/
 ├── msg/
 ├── srv/
 └── action/
```

**📘 인터페이스 패키지 생성**
```
ros2 pkg create --build-type ament_cmake my_robot_interfaces
```
⚠️ 중요  
🐍 Python 기반 개발이어도 인터페이스 패키지는 보통 `ament_cmake` 사용   

**📘 인터페이스 파일 위치**
```
msg/Status.msg
srv/AddTwoInts.srv
action/Navigate.action
action/SwitchControl.action
```
⚠️ 파일명은 CamelCase 사용🐫

**📘 인터페이스 정의 예시**  
**📌 msg**
```
int32 battery_level
bool is_charging
string robot_name
```

**📌 srv**
```
int64 a
int64 b
---
int64 sum
```
→ ---  :arrow_up: 위 = Request / :arrow_down: 아래 = Response  

**📌 action**
```
# Goal
float64 target_x
float64 target_y

---
# Result
bool success

---
# Feedback
float64 progress_percent
```
→ Goal/Result/Feedback 구조 사용  

**📘 반드시 수정해야 하는 설정 파일**  
📌 CMakeLists.txt  
- msg / srv / action 파일 등록
- rosidl_generate_interfaces() 설정  

📌 package.xml  
- 의존성 추가  
    ◦ 예: rosidl_default_generators, builtin_interfaces  

**📘 빌드 및 확인**
```
cd ~/ros2_ws
colcon build --packages-select my_robot_interfaces
source install/setup.bash
```
⚠️ 안 하면 인터페이스 인식 안 되는 경우 많음  

**📘 인터페이스 확인 명령어**  
```
ros2 interface show my_robot_interfaces/msg/Status
``` 

**📘 인터페이스 사용 실습 흐름**
1. 인터페이스 패키지 생성
2. msg / srv / action 작성
3. build 수행
4. Python 패키지 생성
5. Publish / Subscribe 또는 Service / Action 연결
```
ros2 pkg create --build-type ament_python ros_study_py
```

**📘 예제 프로젝트 구조**  

- 예시 프로젝트(ex_calculator)  
    ◦ Topic → 연산 인자 전달  
    ◦ Service → 연산 수행  
    ◦ Action → 연산 결과 검증  

- 인터페이스 사용  
    ◦ ArithmeticArgument.msg  
    ◦ ArithmeticOperator.srv  
    ◦ ArithmeticChecker.action  



**✅ Intra-Process Communication (IPC)**
> ROS2에서 같은 프로세스 안에 있는 Publisher와 Subscriber 간 통신 최적화  
- 일반적인 ROS2 통신은 DDS 미들웨어를 통해 데이터를 주고받음
- 그러나 같은 프로세스 안이라면 DDS를 거치지 않고 메모리 직접 공유로 통신 가능 -> IPC  

**📌장점**
- **메모리 복사(copy) 최소화** → 속도 빠름
- **CPU 사용량 감소** → 성능 최적화  

**📌사용 방법**
- 특별한 설정 없이, Publisher와 Subscriber가 같은 노드(또는 같은 프로세스) 안에 있으면 자동 활성화 가능
- 더 명시적으로 조절하고 싶으면 launch 파일이나 코드에서 옵션 설정 가능  
예: use_intra_process_comms=True 옵션을 노드 생성 시 적용

**✅ DDS의 QoS (Quality of Service)**  
> DDS는 ROS2의 기반 통신 프로토콜입니다. 데이터 통신 품질을 세밀하게 조정하는 기능이 QoS(서비스 품질)입니다.  

**📌주요 Qos 정책**
- **Reliability** : 데이터 전송 보장 여부
    ◦ Reliable: 데이터 전송을 보장합니다. 전송 실패 시 데이터를 재전송하여, 중요한 메시지가 손실되지 않도록 보장  
    ◦ Best Effort: 데이터 전송을 시도하지만, 실패한 경우 재전송을 하지 않으며, 가능한 빨리 전송  
- **Durability** : 구독자가 생긴 이후 과거 데이터 제공 여부  
    ◦ Transient Local: 데이터를 보존하여 새로운 구독자가 구독을 시작할 때 이전 데이터를 받을 수 있음  
    ◦ Volatile: 데이터를 저장하지 않고, 구독자가 연결되면 최신 데이터만 제공  
- **History** : 저장할 메시지 수  
    ◦ Keep All: 모든 데이터를 저장하며, 구독자가 데이터를 받을 때 모든 데이터가 전달  
    ◦ Keep Last: 지정된 개수의 최근 데이터만 저장하며, 이전 데이터는 삭제  
- **Deadline** : 데이터 전송 주기 요구  
    ◦ 정해진 시간 내에 데이터의 발신 및 수신이 이루어지지 않으면, 이벤트가 발생하거나 경고를 보냄  
- **Lifespan** : 메시지 유효 시간 설정  
    ◦ 데이터가 유효한 기간을 설정하여, 지정된 기간 내에만 데이터를 유효하게 처리하고, 기간이 지나면 데이터를 삭제  




**Transformations (좌표 변환)**
- 로봇의 여러 링크(팔, 바퀴 등) 사이의 상대적인 위치와 방향을 정의
- 주로 tf2 라이브러리를 통해 프레임 간 변환을 브로드캐스팅하거나 계산
- 예: “base_link → camera_link” 변환은 로봇 본체 기준으로 카메라 위치를 계산

**URDF (Unified Robot Description Format)**
- 로봇의 구조와 링크/조인트 연결 정보를 XML 형식으로 기술하는 표준 포맷
- 각 부품의 위치, 질량, 관절 타입 등을 정밀하게 정의
- RViz, Gazebo 같은 시각화/시뮬레이션 툴과 연동되며, ROS의 기본 모델링 방식

**Xacro (XML Macro)**
- URDF의 중복 코드 문제를 해결하기 위한 확장 포맷
- 매크로, 변수, 조건문 등을 지원하여 복잡한 URDF를 간단하게 관리
- .xacro 파일은 사용 전에 .urdf로 변환해서 사용

**RViz**
- ROS2에서 사용하는 3D 시각화 툴
- 로봇의 모델, 좌표 프레임, 센서 데이터(LiDAR, 카메라), 경로 등을 시각적으로 확인
- 디버깅이나 로봇 동작 확인용으로 매우 유용

**Gazebo**
- 실제 물리 환경을 흉내내는 3D 물리 기반 시뮬레이터=
- URDF나 SDF를 기반으로 로봇의 동작, 센서, 환경과의 상호작용을 테스트 가능
- ROS2와 함께 동작하며, 실제 하드웨어 없이도 개발 및 실험이 가능

**Simulation (시뮬레이션)**
- 실제 로봇 없이 가상의 로봇을 실행하여 동작을 시험해보는 전체 과정
- RViz는 시각화, Gazebo는 물리 시뮬레이션 역할을 하며 둘 다 함께 사용
- 센서 데이터, 네비게이션, 제어 알고리즘 등을 시뮬레이션으로 먼저 검증

**Gazebo World**
- 로봇이 움직이고 탐색할 수 있는 가상의 3D 환경
- .world 파일 형식으로 구성되며, 건물, 장애물, 조명, 센서 환경 등을 포함
- 로봇 모델(URDF)와 함께 로딩되어 시뮬레이션의 기반 환경

**SLAM (Simultaneous Localization and Mapping)**
- 로봇이 지도를 만들면서 동시에 자신의 위치를 추정하는 기술
- Lidar 또는 RGB-D 센서를 이용하여 알려지지 않은 공간을 자율적으로 탐색
- ROS2에서는 slam_toolbox, gmapping, cartographer 같은 패키지 사용

**NAV2 (Navigation2)**
- ROS2에서 자율주행을 수행하는 공식 네비게이션 스택
- 경로 계획(Global/Local Planner), 장애물 회피, 목표 이동, SLAM 연동 등을 담당
- map → plan → control → move 전체 흐름을 통합 관리하며, 실제 로봇 또는 시뮬레이터 모두에서 사용 가능

**Visual SLAM (비주얼 슬램)**
- 카메라 영상 기반으로 SLAM을 수행하는 기술
- RGB 또는 RGB-D 이미지에서 특징점을 추출하여 로봇의 위치를 추정하고 지도를 생성
- 대표적인 패키지는 ORB-SLAM2, RTAB-Map, VSLAM with OpenVSLAM 등이며, 라이더 없이도 동작 가능

🧭전체 흐름 예시 (시뮬레이션 기반 자율주행)
1. Gazebo에서 로봇 + 환경(world) 실행
2. SLAM 노드 실행 → 실시간 맵 생성
3. RViz에서 로봇 위치, 경로, 목표 설정
4. Nav2가 로봇의 위치를 기반으로 경로 생성 및 주행 제어
5. (선택) Visual SLAM을 카메라 센서로 대체하여 라이다 없이 SLAM 수행
