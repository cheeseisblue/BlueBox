핀 연결은 다음과 같다.

<img src="https://user-images.githubusercontent.com/62240493/82744899-678c9b00-9db9-11ea-8031-7df5aa3158c2.jpg" width="300" height="300">

<img src="https://user-images.githubusercontent.com/62240493/82744901-69565e80-9db9-11ea-982e-10c207f37cbf.jpg" width="300" height="300">

파란 선이 data, 검은 선이 gnd, 붉은 선이 vcc이다.

코드는 크게 세 단계로 나누어지며 센서가 데이터를 읽어들이는 부분을 보면

1. 
![1](https://user-images.githubusercontent.com/62240493/82744902-69eef500-9db9-11ea-8c70-8cf046b62796.png)

samplingInterval마다 SensorPin의 입력값을 analogRead를 통해 가져와 저장해두고 샘플링해둔 데이터를 이용해 voltage값을 계산한다.

2. 
![2](https://user-images.githubusercontent.com/62240493/82744904-69eef500-9db9-11ea-959a-2e85db18f8b3.png)

현재 센서의 상태에 맞게 voltage가 2.67일때 pH = 4.0이 나오도록, voltage가 11.26일때 pH = 7.0이 나오도록 Estimated pH를 계산하게 만들어져있다.
urlmain에는 "http://ec2-34-238-156-25.compute-1.amazonaws.com:8001/get?"이 저장되어있으며 device_id = 1, EpH_value, voltage를 전송하도록 되어있다.

3. 
![3](https://user-images.githubusercontent.com/62240493/82744905-6a878b80-9db9-11ea-8655-fec96d47eaf9.png)

센서랑은 관계가 없지만 esp32에서 wifi를 연결하는 부분이다.


센서가 pH 전극에서 발생하는 전위차(analog)를 float값으로 전환해서 보내주기 때문에, 간단한 형태의 ADC라고 볼 수 있다.

