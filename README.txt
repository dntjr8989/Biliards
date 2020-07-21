Name : 강우석

StudentID : 20185550

Compliation Environment 
- type : Debug mode
- version : Visual Studio 2017

 Summary of code modification.
- CSphere 클래스의 생성자 CSphere(void)에서 CSphere의 반지름인 m_radius가
  0으로 되어 있길래 m_radius = M_RADIUS로 수정하였다.

- CSphere의 메소드인 void hitBy()함수와 Cwall의 메소드인 void hitBy() 의 매개인자에 float timeDelta를 추가하였다.
 당구공 움직이는 모습이 자연스럽게 되기 위해서 Display에서 ballupdate()할 때만 timeDelta를 고려하는 것이 아닌
 공이 부딪힌 직후에도 ballupdate를 할때도 timeDelta를 사용할 수 있도록 했다.

- Csphere의 메소드 ballupdate()에서 if(vx > 0.1 || vz > 0.1) => if(vx > 0.001 || vz > 0.001)로 좀 더 움직임이 자연스롭게 하도록 바꿨다.

- Class Csphere의 hasIntersected() 메소드
  두 공이 부딪힌다는 판단은 두 공의 중심의 거리를 구한 후
  distance = sqrtf(powf(this->center_x - ball.center_x, 2.0) + powf(this->center_z - ball.center_z, 2.0));
  그것이 두 공의 반지름의 합보다 작거나 같은 경우에  부딪힌다고 판단하도록 했다. 
  if (distance <= (this->m_radius)*2)

- Class Csphere의 hitBy() 메소드
  두 공이 부딪힌다고 판단되면 부딪힌 후 두 공의 운동방향, 속도를 바꿨다.
  부딪힌 후 운동상황은 물리공식에 맞게 바꾸었다.
  그 후 그 사이의 시간 timeDelta를 구하여 ballupdate를 한다.
  ballupdate를 했는데 만약 두 공이 겹쳐있는 경우가 발생한다면 두 공을 때어내도록 했다.
  두 공이 겹치는 부분의 길이의 1/2만큼 두 공을 평행이동하여 공이 겹치는 경우 떨어지도록 했다.

- Class Cwall의 hasIntersected() 메소드
  가로벽인지 세로벽인지를 m_width와 m_depth로 구분한다.
  그 후 벽의 중심을 지나고 벽의 변 길이를 반으로 나누는 직선 중 길이가 긴 직선과
  공 중심사이의 거리가 벽 두께의 1/2와 반지름 길이의 합 보다 작거나 같으면 부딪혔다고 판단.

- Class Cwall의 hitBy() 메소드
  벽에 부딪혔다고 판단된 경우 벽을 부딪힌 후의 공의 운동을 물리법칙에 맞게 바꾼다.
  그리고 이 코드가 도는 순간 걸리는 시간 timeDelta를 구하여 ballUpdate()를 하여 공이
  자연스럽게 벽에 부딪히도록 했다.
  
  

  