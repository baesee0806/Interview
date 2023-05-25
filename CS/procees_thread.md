### 프로세스란?

프로세스는 운영체제로 부터 자원을 할당받은 `작업`의 단위이다.

### 스레드란?

스레드는 프로세스가 할당받은 자원을 이용하는 `실행 흐름`의 단위이다.

### 프로그램의 정의

> 프로그램이란, 파일이 정장 장치에 저장되어 있지만 `메모리에는 올라가있지 않은` `정적인 상태`를 말한다
> 

`메모리에 올라가 있지 않은` : 아직 운영체제가 프로그램에세 독립적인 메모리 공간을 할당해주지 않았다는 뜻이다. 모든 프로그램은 운영체제가 실행 되기 위한 메모리 공간을 할당해 줘야 실행될 수 있다.

`정적인 상태` : 정적이라는 단어 그대로, 움직이지 않는 상태라는 뜻 한마디로 아직 실행되지 않고 가만히 있다는 뜻이다.

🟣 프로그램이라는 단어는 아직 실행되지 않은 파일 그자체를 가리키는말

> 윈도우의 `*.exe 파일`이나 MacOS의 `*.dmg 파일` 등등 사용자가 눌러서 실행하기 전의 파일을 말한다. 쉽게 말해서 **그냥 코드 덩어리**다.
> 

### 프로그램 → 프로세스 → 스레드

- 프로그램 → 프로세스
    
    프로그램을 실행하는 순간 해당 파일은 컴퓨터 메모리에 올라가게 되고, 이상태를 `동적`인 상태라고 하며 이상태의 프로그램을 `프로세스`라고 한다.
    
    프로세스에 정의를 내릴 떄 그냥 `실행되고 있는 컴퓨터 프로그램`이라고 정의를 내고 있다.스케줄링 단계에서의 `작업`과 같은 단어라고 봐도 무방하다. 실제로 프로세스라는 단어가 작업 중인 프로그램을 의미하는 단어이기 때문이다.
    
    🟣 `프로그램`은 코드 덩어리 파일, 그 프로그램을 실행한게 `프로세스`
    

- 프로세스 → 스레드
    
    과거에는 프로그램을 실행할 때 실행 시작부터 실행 끝까지 프로세스 하나만을 사용해서 진행했다고 한다. 하지만 시간이 흐를수록 프로그램이 복잡해지고 프로세스 하나만을 사용해서 프로그램을 실행하기는 벅차게 되었다. 실제로 이제는 프로그램 하나가 단순히 한 가지 작업만을 하는 경우는 없다. 그러면 이제 어떻게 해야할까?
    
    쉽게 떠오르는 방법은, "한 프로그램을 처리하기 위한 프로세스를 여러 개 만들면 되지 않을까?" 생각이 들지만 이는 불가능한 일이었다. 왜냐하면 운영체제는 안전성을 위해서 프로세스마다 자신에게 할당된 메모리 내의 정보에만 접근할 수 있도록 제약을 두고 있고, 이를 벗어나는 정보에 접근하려면 오류가 발생하기 때문이다.
    
    아무튼 프로세스와는 다른 더 작은 실행 단위 개념이 필요하게 되었고, 이 개념이 바로 **스레드**다.
    
    스레드는 위에서 언급한 프로세스 특성의 한계를 해결하기 위해 만들어진 개념이기 때문에 스레드의 특성은 쉽게 유추해낼 수 있을 것이다. 스레드는 프로세스와 다르게 스레드 간 메모리를 공유하며 작동한다. 스레드끼리 프로세스의 자원을 공유하면서 프로세스 실행 흐름의 일부가 되는 것이다. 아까 프로그램이 코드 덩어리라고 했는데, 스레드도 코드에 비유하자면 스레드는 코드 내에 선언된 함수들이 되고 따라서 main 함수 또한 일종의 스레드라고 볼 수 있게 되는 것이다.
    
    - 요약 정리
        
        프로그램 실행에 대해 이야기할 때 본질적으로 컴퓨터의 프로세서에 의해 실행되는 일련의 명령에 대해 이야기하고 있습니다. 과거에는 이러한 명령어가 단일 프로세스를 사용하여 실행되었으므로 한 번에 하나의 명령어 세트만 실행할 수 있었습니다. 그러나 프로그램이 복잡해짐에 따라 하나의 프로세스만 사용하여 프로그램을 실행하는 것이 효율적이지 않다는 것이 분명해졌습니다.
        
        이 문제에 대한 한 가지 해결책은 여러 프로세스를 사용하여 프로그램을 처리하는 것입니다. 그러나 이 방법에는 한계가 있습니다. 각 프로세스는 자신에게 할당된 메모리 내의 정보에만 액세스하도록 제한되며, 프로세스가 이 제한을 벗어난 정보에 액세스하려고 하면 오류가 발생할 수 있습니다.
        
        이 문제를 해결하기 위해 더 작은 실행 단위 개념이 필요했고 여기에서 스레드가 등장합니다. 스레드는 동일한 프로세스 내에서 여러 명령 세트를 실행하여 효율성을 높이고 리소스를 더 잘 사용할 수 있는 방법입니다.
        
        프로세스와 달리 스레드는 서로 간에 메모리를 공유하므로 동일한 프로그램의 일부로 함께 작업할 수 있습니다. 스레드는 다른 스레드와 병렬로 실행될 수 있는 프로그램 코드 내에서 선언된 함수로 생각할 수 있습니다.
        
        요약하자면 스레드는 프로세스의 코드에 정의된 절차에 따라 실행되는 특정 실행 경로입니다. 동일한 프로세스 내에서 여러 명령 집합을 동시에 실행할 수 있으므로 효율성이 높아지고 리소스를 더 잘 사용할 수 있습니다.
        
    
    🟣 `스레드` 는 프로세스의 코드에 정의된 절차에 따라 실행되는 특정한 수행 경로다.