# 데이터베이스

1. DDL(데이터 정의어), DCL(데이터 조작어), DML(데이터 제어어)

2. 키

슈퍼키(유일성), 후보키(유일성 + 최소성), 주키(후보키 중 하나), 대체키(후보키에서 주키를 제외한 나머지), 외래키(다른 테이블의 주키)

3. 조인

Inner Join, Outer Join (Left, Right, Full), Cross Join, Self Join, Natural Join, Equi Join ...

4. 정규화

무손신 조인 분할, 종속성 보전 분할

데이터 중복, 삽입/삭제/갱신 이상 제거

제 1 정규형(1NF), 제 2 정규형(2NF), 제 3 정규형(3NF), 보이스-코드 정규형(BCNF)

정규화로 인해 많은 조인 연산 발생 가능 -> 반정규화

5. 인덱스

Clustered Index
데이터 순서와 인덱스 순서가 동일 - ex) 사전

Non-Clustered Index
데이터의 주소를 저장 - ex) 책의 색인

B+ Tree, Hash

6. 질의 처리

Nested Loop Join - 이중 for문처럼 동작, 내부 테이블이 조인 컬럼에 대해 인덱스를 가지고 있으면 성능 향상 가능

Sort Merge Join - 조인하려는 두 테이블 모두 조인 컬럼에 대해 정렬한 후 합병 정렬처럼 동작

Hash Join - 한 테이블에 대해 해시 테이블을 생성한 후 다른 테이블을 스캔하면서 확인하는 방식으로 동작, 해시 테이블의 크기가 커서 디스크 영역을 사용해야 한다면 성능 감소, Equi Join만 가능

7. 트랜잭션

ACID(원자성, 일관성, 고립성, 영구성)

트랜잭션 격리 수준 & 문제점

  Read Uncommitted, Read Committed, Repeatable Read, Serializable

  Dirty Read, Unrepeatable Read, Phantom Read + Lost Update

8. 동시성 제어

Shared Lock(S-Lock) - Read
Exclusive Lock(X-Lock) - Write

단순히 락을 사용하는것만으로는 해결 X

->

Two Phase Locking(2PL)
Growing Phase - Lock 단계
Shrinking Phase - Unlock 단계

Conservative 2PL - End Of Transaction에서 모든 Lock 해제

9. 데드락

데드락을 감지하는 방식은 비용이 너무 들기 때문에 사용 X

->

비선점 Wait-Die - old는 wait, new는 die (new 롤백)

선점 Wound-Wait - old는 wound (new 롤백), new는 wait
