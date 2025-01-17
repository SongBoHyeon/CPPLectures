# Array Declaration and initialization (배열 선언  초기화)

## 배열 선언

변수를 사용하기 위해서는 변수를 선언하였다. 배열의 경우도 **배열을 사용하기 위해서는 배열을 선언하여야 한다.** 
배열 선언을 통해 컴파일러에게 배열 요소의 개수와 요소의 자료형을 함께 선언해야 한다. 
배열의 선언은 변수의 선언과 같이 자료형이 먼저 지정되어야 한다. 그 후 **배열 이름**과 **자료형의 저장공간 개수(배열의 크기)**를
명시하기 위해 대괄호(**[]**)를 이용한다.

```C++
자료형 배열이름[배열크기];
 ```

* 다섯 명의 학생 성적을 저장할 int형 저장공간 5개를 할당하기 위한 배열 score를 선언한다. 

```C++
int score[5];  // 5개의 int 형 저장장소를 할당하는 배열 score
```

![image](./images/score_array.png)    

* 문자형(char) 데이터 10개를 저장할 수 있는 배열 name의 선언은 다음과 같다.

``` C++
char name[10]   // 10개의 char형 저장장소를 할당하는 배열 name
```

![image](./images/name_array.png) 


* 배열을 선언하면 메모리에 지정한 갯수만큼 저장공간을 메모리에 **연속적으로 할당한다.** 
* score와 name은 배열의 이름이며 이는 연속적으로 할당된 메모리 저장공간의 시작주소를 의미한다.
* 배열 score 선언을 통해 학생 성적 다섯 개를 저장할 수 있는 저장공간이 할당되면 다섯 개의 저장공간 각각을 식별하는 방법이 필요하다.

### 배열의 인덱스

* 배열의 전체 저장공간 내 각 요소를 구분하기 위해서 각 요소에 대한 저장공간 각각에 유일한 **번호(인덱스)**를 부여합니다. 
* 배열의 첫 번째 요소의 인덱스는 **0**이다.   
* 배열 인덱스의 최대 값은 **'배열크기 -1'** 이다. - 앞의 배열 score와 name의 경우 최대 인덱스 값은 각각 4, 9 이다.
* **((배열 인덱스 >= 0) && (배열 인덱스 <= 배열크기 - 1))** 

* 배열을 선언할 때 사용하는 대괄호는 선언하는 변수가 배열이라는 것을 명시하며 **대괄호**안에 할당할 저장공간의 크기를 규정한다. 
**배열의 크기는 반드시 0 보다 큰 정수형 상수로 설정해야 한다.**
* **배열의 크기에 변수를 사용하는 것은 불가능하다.** 
* 또한 초기화하지 않으면서 배열의 크기를 설정하지 않으면 안된다. 

배열의 크기를 지정할 때 앞에서와 같이 리터럴 상수 또는 다음과 같은 매크로 상수를 사용할 수 있다. 
```C++
#define MAX 5   // 매크로 상수
int score[MAX];
```

sizeof 연산자를 배열이름에 적용하면 배열의 바이트 크기를 구할 수 있다. 
배열 score에 sizeof 연산자를 적용한 연산식은 **sizeof(score)** 이고 연산결과는 배열 score를 위해 메모리에 할당한 저장공간 전체의 바이트 크기이다. 

* sizeof 연산자를 통해 배열 score의 크기를 계산하는 방법
 ```C++
 sizeof(score)/sizeof(score[0])
```

다음 프로그램은 sizeof 연산자를 사용하여 배열 score, department의 바이트 단위의 메모리 저장공간의 크기를 얻어 출력한다. 

```C++
#include <iostream>

using namespace std;

int main(int argc, char const *argv[])
{
	int score[5];
	char department[] = "Game_Engineering";

	cout << "size of score[]: " << sizeof(score) << endl;
	cout << "size of department[]: " << sizeof(department) << endl;
	return 0;
}
```
앞의 프로그램의 결과는 다음과 같다. 

![image](./images/sizeofArray_result.png)

##  배열의 초기화

배열의 선언과 동시에 저장공간을 초기화하는 것은 다음과 같다.
```C++
int score[5] = {10, 20, 30};  // 배열 score에는 10, 20, 30, 0, 0 이 저장됨 
char name[10] = "John";       
// 배열 name의 저장 장소는 10개 이고 name[0]: 'J', name[1]:'o', name[2]:'h', name[3]:'n', name[4]:'\0'
```

배열의 선언과 동시에 초기화를 하는 경우에는 배열의 크기를 다음과 같이 명시적으로 표현하지 않아도 된다.
```C++
double area[] = {10.1, 20.2, 30.4, 40.4}; // 초기화하는 데이터가 4개 이므로 배열 area의 크기는 4 임
char department[] = "Game_Engineering";   // 초기화하는 문자열의 문자 수가 16개이고 문자열을 저장하므로 배열 department의 크기는 17 임

배열의 모든 요소를 0으로 초기화 하는 방법
```C++
int score[5] = {0};
```

### 초기화 관련 에러 

* 배열의 크기보다 많은 데이터로 초기화할 경우 컴파일 에러 발생 
```C++
int score[5] = {10, 20, 30, 40, 50, 60};   // 컴파일 에러 발생
```

* 배열을 초기화할 때 중괄호({}) 안이 비워있는 경우 컴파일 에러 발생
```C++
int score[5] = {};
```

* 배열의 크기가 생락하고 데이터의 초기화가 이루어지지 않는 경우
```C++
int score[];
```


