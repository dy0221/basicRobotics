# Information
로봇공학입문설계라는 과목에서 진행한 termproject정리.  
2023.03.01~2023.06.16 진행했고(2학년 1학기) 총 3가지 프로젝트를 진행하였다.  
전부 아두이노를 기반으로 제작했다.  
원두연 (로봇공학과/2022..)
배민성 (로봇공학과/2022..)
최민우 (로봇공학과/2022..)
1. pixy카메라를 이용한 도로주행과 odometry를 이용한 장애물피하기
2. 로봇팔을 이용하여 볼트 끼우기
3. 자율주제 (balancing tray와 object detect mobile robot을 합침)  
4. termProject0이라고 적었는데, 매주 있던 과제중 하나로 라인트레이싱이다.  

## termProject0
[![Video Label](http://img.youtube.com/vi/ghHa1IlgGxM/0.jpg)](https://youtu.be/ghHa1IlgGxM)


blue pill board로만든 모터드라이버 아두이노메가를 연결하여 모바일로봇을 제작하였다.  
그후 모터에 pid제어를 한후 두 보드 사이의 uart protocol를 구상하여서 로봇을 제어하며  
라인트레이싱을 진행하였다.

## termProject1
[![Video Label](http://img.youtube.com/vi/mAp53yD6Okc/0.jpg)](https://youtu.be/mAp53yD6Okc)

termproject0에 사용한 모바일로봇을 바탕으로 pixy를 이용하여 도로주행과 odometry를 활용하여 주차라는 크게  
2가지의 미션을 진행하였다.  
그중 도로주행에서는 표지판의 바코드를 인식하여 감가속하는 미션과 주차 부분에서는 장애물을 피하는 미션이 존재 했고,  
그 사이에 rgb led를 활용한 신호등미션이 존재했다.  

도로주행에서는 도로의 외각 선을 검출하여 선의 vector를 구하여 그 선안에서 움직일수 있도록 코드를 구현하였고,  
주차의 경우 uart protocol를 통하여 얻은 정보로 odomerty 수식을 직접 구현하고 
Stack처럼 일정한 우선순위속에서 장애물을 만나면 만난 횟수를  
기억하여 마지막으로 피한 반대 방향으로 움직이면서 주차지점에 도착하는 알고리즘을 구현하였다.

## termProject2
[![Video Label](http://img.youtube.com/vi/IdN1mbT2LjY/0.jpg)](https://youtu.be/IdN1mbT2LjY)

로봇팔을 이용하여 볼트를 넣는 알맞은 곳에 넣는 미션을 진행하였다.  
볼트를 넣는 곳과 볼트의 위치는 모드 랜덤으로 진행하였다.  

로봇이 움직이는 workspce를 이해하고 inverse kinematics를 계산한 값을 바탕으로 이미 있는 볼트나 움직일수 없는 위치를  
피해 Trajectory Planning을 진행하였다.  
색을 인식한 방법은 똑같이 pixy를 사용하여 픽시의 픽셀을 나누어서 한번에 4새씩 3번 총 12칸의 rgb를 인식하고 각각의  
맞는 볼트를 찾아 넣는 알고리즘으로 진행하였다.

## termProject3
[![Video Label](http://img.youtube.com/vi/ILr9IeQixqk/0.jpg)](https://youtu.be/ILr9IeQixqk)

마지막 termproject는 자율주제였다.  
우리는 balancingtray와 mobile로봇을 합쳐 움직이면서 벨런스를 잡는 로봇을 생각하였다. 

balancingtray경우 imu센서를 접시 뒤에 붙여 접시의 기울기를 바탕으로 시스템PID를 적용하여서   
balancing을 잡는 알고리즘을 제작하였다.  

moblie 로봇의 경우 매카넘휠을 사용하여 회전을 최대한으로 줄이면서 움직일 수 있도록 하였다.  
또한 pixy카메라를 활용하여서 물체를 감지하여 물체를 따라서 움직이도록 하였다.  

또한 둘을 합쳐놓으므로써 접시의 기울기에 따른 힘만 고려하는 것이 아닌 molie로봇에의하여 생기는  
가속도로 생기는 힘또한 접시의 balance를 잡는데 고려를 해주어야 한다.  
따라서 가속도의 90도 방향으로 reference각도를 지정해주어 이를 해결하였다.
