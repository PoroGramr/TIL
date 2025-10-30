# Garbage Collection in JVM

Garbage Collection(GC)은 Java Virtual Machine(JVM)에서 메모리 관리를 자동화하는 중요한 기능입니다. GC는 더 이상 참조되지 않는 객체를 식별하고 제거하여 메모리를 회수함으로써 메모리 누수를 방지하고 애플리케이션의 성능을 향상시킵니다.

## heap 메모리 구조

JVM의 힙 메모리는 여러 영역으로 나뉘며, 각 영역은 객체의 생애 주기와 관련된 역할을 합니다. 주요 영역은 다음과 같습니다:

- **Young Generation**: 새로 생성된 객체가 할당되는 영역입니다. Young Generation은 다시 Eden 영역과 두 개의 Survivor 영역(S0, S1)으로 나뉩니다. 대부분의 객체는 이 영역에서 생성되고, 일정 시간이 지나면 더 이상 참조되지 않는 객체는 GC에 의해 제거됩니다.

- **Old Generation(또는 Tenured Generation)**: Young Generation에서 살아남은 객체가 이동하는 영역입니다. 이 영역의 객체는 상대적으로 오래 지속되며, GC가 덜 빈번하게 실행됩니다.

### Young Generation의 GC
Young Generation에서는 주로 Minor GC가 발생합니다. Minor GC는 Eden 영역과 Survivor 영역에서 더 이상 참조되지 않는 객체를 식별하고 제거합니다. 살아남은 객체는 Survivor 영역으로 이동하며, 일정 횟수 이상 생존한 객체는 Old Generation으로 이동합니다.

### Old Generation의 GC
Old Generation에서는 Major GC 또는 Full GC가 발생합니다. 이 GC는 Old Generation에 있는 객체를 대상으로 하며, 메모리 회수를 위해 더 많은 시간을 소요할 수 있습니다. Major GC는 애플리케이션의 성능에 영향을 미칠 수 있으므로, 주의해서 관리해야 합니다.


## 가비지 컬렉션 알고리즘

JVM은 다양한 가비지 컬렉션 알고리즘을 제공합니다. 주요 알고리즘은 다음과 같습니다:
- **Mark-and-Sweep**: 이 알고리즘은 먼저 모든 객체를 탐색하여 살아있는 객체를 표시(Mark)한 후, 표시되지 않은 객체를 제거(Sweep)합니다. 이 방법은 단순하지만, 메모리 단편화가 발생할 수 있습니다.
- **Generational Garbage Collection**: 이 알고리즘은 객체의 생애 주기에 따라 메모리를 관리합니다. Young Generation과 Old Generation으로 나누어, Young Generation에서 자주 발생하는 GC를 통해 빠르게 메모리를 회수하고, Old Generation에서는 덜 빈번한 GC를 수행합니다.
- **G1 (Garbage-First) Collector**: G1은 대규모 힙 메모리를 효율적으로 관리하기 위해 설계된 알고리즘입니다. G1은 힙을 여러 개의 작은 영역(Region)으로 나누고, 각 영역을 독립적으로 관리합니다. G1은 짧은 일시 중단 시간을 목표로    하며, 애플리케이션의 응답성을 향상시킵니다. 

