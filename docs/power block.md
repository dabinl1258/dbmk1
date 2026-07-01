전원 회로는 LDO를 사용 하여 설계한다. 

이 프로젝트에서는 MCU 구동을 위해서 3.3V가 필요하고 보드에는 쉽게 구할 수 있는 USB 5V로 전원을 공급 할 예정이다.



# LDO (Low dropout)

LDO는 Low Linear Dropout Regulator를 말한다.

높은 입력 전압을 낮은 출력 전압으로 낮추는 소자이다.

Low가 앞에 Low는 출력 전압과 입력전압의 차가 작다는 것을 의미한다.

High Voltage DC를 Low Voltage DC로 낮추는 다른 소자로는 Buck  Down Converter도 있다. Buck Down Converter와  LDO는 특성이 다르다.

LDO는 입력/출력의 전압 차이 만큼 열로 소진 시킨다. 

따라서 노이즈는 적지만, 저전력에 불리하고, 전압 차이가 큰 경우 사용 할 수 없다. 

그에 반해 Buck은 스위칭을 통해서 전압을 낮춤으로 열로 전력이 소진 되지 않는다. 하지만 스위칭에 따른 노이즈 발생이 생긴다. 



# 전원 회로에서의 Capacitor의 역할

이상적인 Voltage Source 경우 회로에서 요구하는 전력을 깨끗하게 지속적으로 공급해 주면 좋겠지만 현실을 그렇지 않다. 

회로에서 어떤 기능(Ex, 플래시 라이트를 켜거나, 모터를 돌리거나)을 사용 하면서 순간 전력을 더 사용하면 전압 하강이 발생 할 수 있다. 이것을 보정하기 위해서 Capacitor를 전류 백업 용도로 사용한다.

또한 실제 Voltage Source는 미세한 노이즈를 가지고 있다. 이중 고주파 성분 거르기 위해서 Capacitor을 LPF(Low Pass Filter), 즉 디커플링용으로 사용한다.

LPF(Low Pass Filter) : 저주파(DC 성분)은 통과 시킨다. 

디커플링(Decoupling) : 고주파(AC 성분)과 분리 한다. 

따라서 LDO 양단에 Capacitor을 연결 한다.

회로 - Cap - GND 

회로 - Cap - GND 

이렇게 하면 회로에서 GND 쪽으로 고주파 성분이 빠져 나간다.

GND는 보통 넓게 설게 하기 때문에 LDO에서 나오는 고주파를 충분히 커버한다. 하지만 고주파에 약한 회로(Ex 아날로그 회로)와 GND를 같이 사용하는 경우 주의 해야 한다.

또한 IC에도 전력을 보완 하기 위한 Capacitor를 달게 된다.



# 참고 자료

[LDO 위키백과](https://en.wikipedia.org/wiki/Low-dropout_regulator)

[규칙으로 배우는 임베디드 시스템 설계 회로편 LDO](https://m.blog.naver.com/PostView.naver?blogId=sohnet&logNo=222626723562&navType=by)

[DC-DC Rohm 리니어 레귤레이터 기초](https://techweb.rohm.co.kr/product/power-ic/dcdc/70/)


