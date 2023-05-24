# Redis 와 Memcached

### 공통점
- 인메모리 저장소(In Memory 저장소)
- Key-Value 저장 방식

### 차이점
|  | Redis | Memcahed |
| :- | - |:- |
| 데이터 타입 | String, Set, Sorted Set, Hash, List| String |
| 데이터 저장 | Memory, Disk | Only Memory |
| 메모리 재사용 | 재사용 X  | LRU 알고리즘 |
| 스레드 | Single Thread  | Multi Thread |
| 캐시용량 | Key, Value 모두 512MB  | Key name 250 byte, Value 1MB |

</br>

## Redis 의 특징
- 다양한 데이터 구조 지원 (List, Set, Sorted Set, Hash 등)
- Snapshots 지원 : 특정 시점에 데이터를 디스크에 저장하여 파일 보관 가능, 장애상황시 복구에 사용할 수 있다.
- 복제 : Master - Slaves 구조로, 여러 개의 복제본을 만들 수 있다.
- 트랜잭션 지원
- 루아 스크립트 지원
- 위치기반 데이터 타입 지원 : 실시간 위치기반데이터를 지원. 두 위치의 거리 찾기, 사이에 있는 요소 찾기 등의 작업 수행이 가능하다. 이를 활용하여 지도기반의 고성능 서비스를 제공할 수 있다.
- 싱글 스레드 지원 : 1번에 1개의 명령어만 실행

## Memcached 의 특징
- 명료하고 단순함을 위하여 개발
- 멀티 스레드 지원 : 멀티 프로세스 코어를 사용할 수 있다. 따라서 스케일업을 통해 더욱 많은 작업처리를 할 수 있다.

</br>


## 결론
Redis 가 다양한 지원을 하기 때문에 Memcached 보다 사용하기 용이할 것 같지만 싱글스레드만을 지원하기에 속도가 중요한 서비스에서는 Memcached 사용을 고려해볼 것 같다.

예를 들어 모든 데이터 삭제, 모든 데이터 키 조회 등에서 100만건 기준 redis는 1초, memcached는 1ms 정도 소요로 속도 차이가 꽤 크다.

Redis 장애의 원인이 대부분 해당 기능에서 일어난다고 하니 사용할 때 주의하도록 하자.
