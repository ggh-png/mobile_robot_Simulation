모바일 로봇 시뮬레이션
이 프로젝트는 ROS와 Gazebo 시뮬레이터를 이용하여 모바일 로봇을 제어하는 방법을 배우고, 로봇을 자율주행하도록 프로그래밍하는 것을 목표로 합니다.

필요한 소프트웨어
이 프로젝트를 실행하기 위해서는 다음 소프트웨어가 필요합니다.

ROS (Robot Operating System) : 로봇 소프트웨어를 개발하기 위한 프레임워크입니다.
Gazebo : 로봇 시뮬레이터로, 가상 환경에서 로봇을 시뮬레이션할 수 있습니다.
설치 방법
ROS 설치
ROS 설치 방법은 ROS 공식 사이트에서 확인할 수 있습니다.

Gazebo 설치
Gazebo 설치 방법은 Gazebo 공식 사이트에서 확인할 수 있습니다.

프로젝트 다운로드 및 빌드
터미널에서 다음 명령어를 실행하여 프로젝트를 다운로드합니다.

shell
Copy code
$ git clone https://github.com/ggh-png/mobile_robot_Simulation.git
catkin_make 명령어를 이용하여 빌드합니다.

shell
Copy code
$ cd mobile_robot_Simulation
$ catkin_make
사용 방법
Gazebo 시뮬레이터 실행
다음 명령어를 실행하여 Gazebo 시뮬레이터를 실행합니다.

ruby
Copy code
$ roslaunch mobile_robot_simulation gazebo.launch
로봇 제어
teleop_twist_keyboard 패키지를 이용하여 로봇을 제어할 수 있습니다. 다음 명령어를 실행합니다.

ruby
Copy code
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py
제어 방법은 다음과 같습니다.

위쪽 화살표 : 전진
아래쪽 화살표 : 후진
왼쪽 화살표 : 좌회전
오른쪽 화살표 : 우회전
스페이스바 : 정지
로봇 자율주행
로봇을 자율주행하도록 만들기 위해서는 다음과 같은 노드를 실행해야 합니다.

ruby
Copy code
$ roslaunch mobile_robot_simulation amcl_demo.launch
위 명령어를 실행하면 로봇이 자율주행을 시작합니다. 로봇은 map 파일을 이용하여 자신의 위치를 파악하고, move_base 노드를 이용하여 목표 지점까지 이동합니다.


맵 파일 변경
로봇의 자율주행에 사용될 맵 파일을 변경하려면 다음과 같이 합니다.

새로운 맵 파일을 준비합니다. 새로운 맵 파일은 pgm 또는 yaml 형식이어야 하며, mobile_robot_simulation/maps 디렉토리에 저장합니다.

mobile_robot_simulation/amcl_demo.launch 파일을 수정합니다. 다음과 같이 맵 파일 경로를 수정합니다.

javascript
Copy code
<arg name="map_file" default="$(find mobile_robot_simulation)/maps/새로운_맵_파일.pgm"/>
로봇 목표 지점 변경
로봇의 자율주행 목표 지점을 변경하려면 다음과 같이 합니다.

mobile_robot_simulation/config/move_base_params.yaml 파일을 수정합니다. 다음과 같이 목표 지점을 수정합니다.
yaml
Copy code
- {x: 목표_x좌표, y: 목표_y좌표, z: 0.0, yaw: 0.0}
로봇을 다시 시작합니다.
참고 자료

ROS 공식 사이트 : http://wiki.ros.org
Gazebo 공식 사이트 : http://gazebosim.org
teleop_twist_keyboard 패키지 : https://github.com/ros-teleop/teleop_twist_keyboard




[end.mp4](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1267c16e-d021-46ed-816c-e62d17439528/end.mp4)

### Mobile Robot Hardware

![https://user-images.githubusercontent.com/71277820/170191836-0b1cefe5-b2b6-45c6-9915-f3dea1278243.jpg](https://user-images.githubusercontent.com/71277820/170191836-0b1cefe5-b2b6-45c6-9915-f3dea1278243.jpg)

![https://user-images.githubusercontent.com/71277820/170191826-dcc7bd48-6806-4162-b6e9-e49afd1760df.jpg](https://user-images.githubusercontent.com/71277820/170191826-dcc7bd48-6806-4162-b6e9-e49afd1760df.jpg)

![https://user-images.githubusercontent.com/71277820/170191832-453d42c3-9179-4249-a641-0b193a5a76c8.jpg](https://user-images.githubusercontent.com/71277820/170191832-453d42c3-9179-4249-a641-0b193a5a76c8.jpg)

![https://user-images.githubusercontent.com/71277820/170191821-1ebf32ce-593e-4377-bda6-5f816f77cc51.jpg](https://user-images.githubusercontent.com/71277820/170191821-1ebf32ce-593e-4377-bda6-5f816f77cc51.jpg)

### Model URDF - for gazebo

![https://user-images.githubusercontent.com/71277820/170191818-bec54ade-c090-4f9b-8dff-647936362e32.jpg](https://user-images.githubusercontent.com/71277820/170191818-bec54ade-c090-4f9b-8dff-647936362e32.jpg)

### URDF for rqt

![https://user-images.githubusercontent.com/71277820/170191817-26b87704-868d-4d79-9176-d0c2f96279e6.jpg](https://user-images.githubusercontent.com/71277820/170191817-26b87704-868d-4d79-9176-d0c2f96279e6.jpg)

URDF for GAZEBO

![https://user-images.githubusercontent.com/71277820/170191812-d1e96261-78c4-4a81-98e7-3a1c8fffedc1.jpg](https://user-images.githubusercontent.com/71277820/170191812-d1e96261-78c4-4a81-98e7-3a1c8fffedc1.jpg)

### GAZEBO MAP - 스크린 골프장 구현

![https://user-images.githubusercontent.com/71277820/170191806-96700a09-4500-4758-8ff0-e459439eb53a.jpg](https://user-images.githubusercontent.com/71277820/170191806-96700a09-4500-4758-8ff0-e459439eb53a.jpg)

![https://user-images.githubusercontent.com/71277820/170191798-51ab1df9-7191-4d7d-be77-522042c40b6b.jpg](https://user-images.githubusercontent.com/71277820/170191798-51ab1df9-7191-4d7d-be77-522042c40b6b.jpg)

![https://user-images.githubusercontent.com/71277820/170191787-a6249360-4cda-470c-87e3-88800a930190.jpg](https://user-images.githubusercontent.com/71277820/170191787-a6249360-4cda-470c-87e3-88800a930190.jpg)

![https://user-images.githubusercontent.com/71277820/170191780-e412128c-c903-4277-8029-5f7d6c95e260.jpg](https://user-images.githubusercontent.com/71277820/170191780-e412128c-c903-4277-8029-5f7d6c95e260.jpg)

![https://user-images.githubusercontent.com/71277820/170191770-29c827ad-38b1-4b27-b66f-68ab4282d2e0.jpg](https://user-images.githubusercontent.com/71277820/170191770-29c827ad-38b1-4b27-b66f-68ab4282d2e0.jpg)

![https://user-images.githubusercontent.com/71277820/170191761-cfbcaf8e-3853-47e6-ad82-3813360a0090.jpg](https://user-images.githubusercontent.com/71277820/170191761-cfbcaf8e-3853-47e6-ad82-3813360a0090.jpg)

![https://user-images.githubusercontent.com/71277820/170191753-30455dbb-59ec-4126-8ddc-6b0f9995973f.jpg](https://user-images.githubusercontent.com/71277820/170191753-30455dbb-59ec-4126-8ddc-6b0f9995973f.jpg)

### Slam/Navi - Mapping

![https://user-images.githubusercontent.com/71277820/170191748-e9f94810-f373-4da3-b538-c0a3fd25a19f.jpg](https://user-images.githubusercontent.com/71277820/170191748-e9f94810-f373-4da3-b538-c0a3fd25a19f.jpg)

![https://user-images.githubusercontent.com/71277820/170191744-57b4fc6a-7fcd-45f4-ade0-f4af417873b5.jpg](https://user-images.githubusercontent.com/71277820/170191744-57b4fc6a-7fcd-45f4-ade0-f4af417873b5.jpg)

### Slam/Navi - Navi

![https://user-images.githubusercontent.com/71277820/170191741-0117ffc9-39df-4f47-b768-c532710d9d67.jpg](https://user-images.githubusercontent.com/71277820/170191741-0117ffc9-39df-4f47-b768-c532710d9d67.jpg)

### Object Detection - darknet_ros

![https://user-images.githubusercontent.com/71277820/170191735-5a9c0f2e-ce94-423a-89eb-5e85e5f57873.jpg](https://user-images.githubusercontent.com/71277820/170191735-5a9c0f2e-ce94-423a-89eb-5e85e5f57873.jpg)

![https://user-images.githubusercontent.com/71277820/170191731-85496114-8bb6-430f-8b47-b496063f214b.jpg](https://user-images.githubusercontent.com/71277820/170191731-85496114-8bb6-430f-8b47-b496063f214b.jpg)

![https://user-images.githubusercontent.com/71277820/170191729-5e12a261-2621-42f6-a05d-e94644de624f.jpg](https://user-images.githubusercontent.com/71277820/170191729-5e12a261-2621-42f6-a05d-e94644de624f.jpg)

### RQT Graph

### Topic → camera → darknet_ros

![https://user-images.githubusercontent.com/71277820/170191724-fcd35193-6f2a-4ff9-ba09-7cc17d57ca3e.jpg](https://user-images.githubusercontent.com/71277820/170191724-fcd35193-6f2a-4ff9-ba09-7cc17d57ca3e.jpg)

![https://user-images.githubusercontent.com/71277820/170191701-edbab6e6-cd30-470f-9b20-69707b9bb541.jpg](https://user-images.githubusercontent.com/71277820/170191701-edbab6e6-cd30-470f-9b20-69707b9bb541.jpg)
