Name : ���켮

StudentID : 20185550

Compliation Environment 
- type : Debug mode
- version : Visual Studio 2017

 Summary of code modification.
- CSphere Ŭ������ ������ CSphere(void)���� CSphere�� �������� m_radius��
  0���� �Ǿ� �ֱ淡 m_radius = M_RADIUS�� �����Ͽ���.

- CSphere�� �޼ҵ��� void hitBy()�Լ��� Cwall�� �޼ҵ��� void hitBy() �� �Ű����ڿ� float timeDelta�� �߰��Ͽ���.
 �籸�� �����̴� ����� �ڿ������� �Ǳ� ���ؼ� Display���� ballupdate()�� ���� timeDelta�� ����ϴ� ���� �ƴ�
 ���� �ε��� ���Ŀ��� ballupdate�� �Ҷ��� timeDelta�� ����� �� �ֵ��� �ߴ�.

- Csphere�� �޼ҵ� ballupdate()���� if(vx > 0.1 || vz > 0.1) => if(vx > 0.001 || vz > 0.001)�� �� �� �������� �ڿ����Ӱ� �ϵ��� �ٲ��.

- Class Csphere�� hasIntersected() �޼ҵ�
  �� ���� �ε����ٴ� �Ǵ��� �� ���� �߽��� �Ÿ��� ���� ��
  distance = sqrtf(powf(this->center_x - ball.center_x, 2.0) + powf(this->center_z - ball.center_z, 2.0));
  �װ��� �� ���� �������� �պ��� �۰ų� ���� ��쿡  �ε����ٰ� �Ǵ��ϵ��� �ߴ�. 
  if (distance <= (this->m_radius)*2)

- Class Csphere�� hitBy() �޼ҵ�
  �� ���� �ε����ٰ� �ǴܵǸ� �ε��� �� �� ���� �����, �ӵ��� �ٲ��.
  �ε��� �� ���Ȳ�� �������Ŀ� �°� �ٲپ���.
  �� �� �� ������ �ð� timeDelta�� ���Ͽ� ballupdate�� �Ѵ�.
  ballupdate�� �ߴµ� ���� �� ���� �����ִ� ��찡 �߻��Ѵٸ� �� ���� ������� �ߴ�.
  �� ���� ��ġ�� �κ��� ������ 1/2��ŭ �� ���� �����̵��Ͽ� ���� ��ġ�� ��� ���������� �ߴ�.

- Class Cwall�� hasIntersected() �޼ҵ�
  ���κ����� ���κ������� m_width�� m_depth�� �����Ѵ�.
  �� �� ���� �߽��� ������ ���� �� ���̸� ������ ������ ���� �� ���̰� �� ������
  �� �߽ɻ����� �Ÿ��� �� �β��� 1/2�� ������ ������ �� ���� �۰ų� ������ �ε����ٰ� �Ǵ�.

- Class Cwall�� hitBy() �޼ҵ�
  ���� �ε����ٰ� �Ǵܵ� ��� ���� �ε��� ���� ���� ��� ������Ģ�� �°� �ٲ۴�.
  �׸��� �� �ڵ尡 ���� ���� �ɸ��� �ð� timeDelta�� ���Ͽ� ballUpdate()�� �Ͽ� ����
  �ڿ������� ���� �ε������� �ߴ�.
  
  

  