Chapter 13. 쓰레드 Thread

# 1. 프로세스와 쓰레드

프로세스(process)란 간단히 말해서 '실행 중인 프로그램(program)'이다. 프로그램을 실행하면 OS로부터 실행에 필요한 자원(메모리)을 할당받아 프로스세스가 된다.

프로세스는 프로그램을 수행하는 데 필요한 데이터와 메모리 드으이 자원 그리고 쓰레드로 구성되어 있으며 프로세스의 자원을 이용해서 실제로 작업을 수행하는 것이 바로 쓰레드이다.

그래서 모든 프로세스에는 최소한 하나 이상의 쓰레드가 존재하며, 둘 이상의 쓰레드를 가진 프로세스를 '멀티쓰레드 프로세스(multi-threaded process)'라고 한다.

하나의 프로세스가 가질 수 있는 쓰레드의 개수는 제한되어 있지 않으나 쓰레드가 작업을 수행하는데 개별적인 메모리 공간(호출스택)을 필요로 하기 때문에 프로세스의 메모리 한계에 따라 생성할 수 있는 쓰레드의 수가 결정된다.

</br>

### 멀티태스킹과 멀티쓰레딩

윈도우나 유닉스를 포함한 대부분의 OS는 멀티태스킹(multi-tasking, 다중작업)을 지원하기 때문에 여러 개의 프로세스가 동시에 실행될 수 있다.

이와 마찬가지로 멀티쓰레딩은 하나의 프로세스 내에서 여러 쓰레드가 동시에 작업을 수행하는 것이다. CPU의 코어(core)가 한 번에 단 하나의 작업만 수행할 수 있으므로, 실제로 동시에 처리되는 작업의 개수는 코어의 개수와 일치한다. 그러나 처리해야하는 쓰레드의 수는 언제나 코어의 개수보다 훨씬 많기 때문에 각 코어가 아주 짧은 시간동안 여러 작업을 번갈아 가며 수행함으로써 여러 작업들이 모두 동시에 수행되는 것처럼 보이게 한다.

그래서 프로세스의 성능이 단순히 쓰레드의 개수에 비례하는 것은 아니며, 하나의 쓰레드를 가진 프로세스보다 두 개의 쓰레드를 가진 프로세스가 오히려 더 낮은 성능을 보일 수도 있다.

</br>

### 멀티쓰레딩의 장단점

멀티쓰레딩의 장점은 다음과 같다.

> **멀티쓰레딩의 장점**
> - CPU의 사용률을 향상시킨다.
> - 자원을 보다 효율적으로 사용할 수 있다.
> - 사용자에 대한 응답성이 향상된다.
> - 작업이 분리되어 코드가 간결해진다.

메신저로 채팅하면서 파일을 다운로드 받거나 음성대화를 나눌 수 있는 것이 가능한 이유가 바로 멀티쓰레드로 작성되어 있기 때문이다. 만일 싱글쓰레드로 작성되어 있다면 파일을 다운로드 받는 동안에는 다른 일(채팅)을 전혀 할 수 없을 것이다.

여러 사용자에게 서비스를 해주는 서버 프로그램의 경우 멀티쓰레드로 작성하는 것은 필수적이어서 하나의 서버 프로세스가 여러 개의 쓰레드를 생성해서 쓰레드와 사용자의 요청이 일대일로 처리되도록 프로그래밍해야 한다.

만일 싱글쓰레드로 서버 프로그램을 작성한다면 사용자의 요청 마다 새로운 프로세스를 생성해야 하는데 프로세스를 생성하는 것은 쓰레드를 생성하는 것에 비해 더 많은 시간과 메모리 공간이 필요하기 때문에 많은 수의 사용자 요청을 서비스 하기 어렵다.

> 쓰레드를 가벼운 프로세스, 즉 경량 프로세스(LWP, light-weight process)라고 부르기도 한다.

그러나 멀티쓰레딩에 장점만 있는 것은 아니어서 멀티쓰레드 프로세스는 여러 쓰레드가 같은 프로세스 내에서 자원을 공유하면서 작업을 하기 때문에 발생할 수 있는 동기화(synchronization), 교착상태(dead-lock)와 같은 문제들을 고려해서 신중히 프로그래밍해야 한다.

> 교착상태란 두 쓰레드가 자원을 점유한 상태에서 서로 상대편이 점유한 자원을 사용하려고 기다리느라 진행이 멈춰 있는 상태를 말한다.