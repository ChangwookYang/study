PathVariable & Query Parameter

### PathVariable�� Query Parameter�� �����ϱ�?

#### 1. Query Parameter

�������� ���� �� ���������� �ĺ��� �Ķ���� ��ΰ� �ʿ��ϴ�.  
������ ���� get �Ķ���͸� ����Ͽ� �����͸� �ѱ� �� �ִ�.  
  
> /users?id=123    # ���̵� 123�� ����ڸ� �����´�.
  
������ ���� id������ ���� �� �ִ�.


#### 2. Path Variable  
  
�����͸� �ѱ�� �ٸ� ��� �� �ϳ��� Path Variable�� �ִ�.

> /users/123       # ���̵� 123�� ����ڸ� �����´�.

123��  ������ �����Ѵ�.  
**��θ� ������** ����� �� �ִ�.  

#### 3. Path Variable & Query Parameter�� ���� ����ϴ°�!

resource�� �ĺ��ϰ� ������ Path Variable  
�����̳� ���͸��� �Ѵٸ� Query Parameter�� ����ϴ� ���� BestPractice�̴�.

> /users	# ����� ����� �����´�.
> /users?occupation=programmer # ���α׷����� ����� ����� �����´�.
> /users/123	# ���̵� 123�� ����ڸ� �����´�.
  
���� �⺻���� CRUD ����� ���ؼ� query parameter�� ������ �ʿ�� ����.  
��� ���ϴ� ��ɿ� �°� HTTP �޼ҵ带 �ٲپ�� �Ѵ�.  

> /users [GET] # ����� ����� �����´�.
> /users [POST] # ���ο� ����ڸ� �����Ѵ�.
> /users/123 [PUT] # ����ڸ� �����Ѵ�.
> /users/123 [DELETE] # ����ڸ� �����Ѵ�.

#### 4. ����

���� ������ ���� �ʾƵ� API�� ���� �� ������  
�ٸ� �����ڵ���� ������ ���� ȿ���� ����ϸ� BestPractice�� �����°� ����!



[��ó](https://ryan-han.com/post/translated/pathvariable_queryparam/)
