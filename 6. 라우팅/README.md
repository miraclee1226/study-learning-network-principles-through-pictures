# 6. 라우팅
## 6-1. 라우팅

- 라우터는 데이터의 목적지가 어느 네트워크에 접속되어 있는지 판단해 다음 라우터로 전
송한다.
- 라우터가 전송하는 데이터는 ip 패킷

## 6-2. 네트워크의 연결

- 라우터로 네트워크끼리 서로 접속한다.
- 네트워크를 접속하기 위해서는 라우터의 인터페이스에 ip 주소를 설정한다.

## 6-3. 데이터의 전송처 결정

- 라우팅 대상인 IP 패킷은 다음과 같은 주소의 패킷
    - 목적지 레이어2 주소 : 라우터, 목적지 IP 주소 : 라우터 이외
- 목적지 ip 주소로 라우팅 테이블의 경로를 검색한다.

## 6-4 다음 라우터로 데이터 전송

- 넥스트 홉으로 전송하기 위해 새로운 헤더를 추가한다.
- 이더넷에서는 자동으로 ARP를 실행해 넥스트 홉의 MAC 주소를 구한다.

## 6-5. 다음 라우터의 처리

- 라우팅 처리는 라우터마다 하고, 최종적인 목적지에 직접 접속된 라우터까지 ip 패킷이 전송되어 간다.

## 6-6. 최종 목적지 데이터 전송

- 마지막 라우터는 IP 패킷의 목적지 IP 주소의 MAC 주소를 ARP로 질의해 IP 패킷을 전송
한다.
- 통신은 양방향이라는 것을 잊지 않는다.

## 6-7. 라우팅 테이블

- 라우팅 테이블에는 어떤 네트워크로 ip 패킷을 전송하려면 다음에 어느 라우터로 전송해
야 하는지 경로가 등록되어 있다.
- 라우팅 테이블에 등록되는 정보를 경로 정보라고 부른다.

## 6-8. 직접 접속

- 라우팅 테이블에 경로 정보를 등록하는 방법은 세 가지
    - 직접접속
    - 스태틱 라우팅
    - 라우팅프로토콜
- 인터페이스에 IP 주소를 설정하면 직접 접속된 경로 정보가 라우팅 테이블에 등록된다.

## 6-9. 스태틱 라우팅, 라우팅 프로토콜

- 원격 네트워크의 경로 정보를 등록하는 방법은 두 가지다.
    - 스태틱 라우팅
    - 라우팅 프로토콜
- 스태틱 라우팅은 네트워크 주소/서브넷 마스크와 넥스트 홉 주소를 커맨드 입력해서 등록한다.
- 라우팅 프로토콜은 라우터끼리 정보를 교환해 경로 정보를 등록한다.

## 6-10. 경로 요약

- 경로 요약으로 복수의 네트워크 주소를 하나로 모아 라우팅 테이블에 등록한다.
- 경로 요약을 시행하면 라우팅 테이블을 깔끔하게 정리할 수 있다.

## 6-11. 디폴트 경로

- 경로 요약을 가장 극단적으로 적용한 것: 디폴트 경로(0.0.0.0/0). 모든 네트워크를 집약한 것 이다.
    - 디폴트 경로를 라우팅 테이블에 등록해 두면, 모든 네트워크의 경로 정보를 등록한 게 된다.
- 인터넷으로 라우팅하기 위한 경로 정보로서 디폴트 경로를 이용하는 경우가 많다.

## 6-12. 레이어3 스위치

- 레이어2 스위치에 라우터 기능을 내장한 네트워크 기기가 레이어3 스위치
- 같은 네트워크에서 데이터를 전송할 때는 레이어2 스위치, 다른 네트워크 간에 데이터를
전송할 때는 라우터처럼 전송한다.

## 6-13. VLAN

- VLAN으로 레이어2 스위치에서 네트워크를 분할할 수 있다.
- 같은 VLAN에 할당된 포트 사이에서만 이더넷 프레임을 전송한다.

## 6-14. VLAN 이용의 장점

- VLAN으로 레이어2 스위치를 가상으로 네트워크를 분할할 수 있다.
- VLAN으로 분할된 레이어2 스위치끼리는 연결되어 있지 않으므로. VLAN이 다르면 통신
할 수 없다. (분할한 네트워크가 서로 통신하기 위해서는 라우터와 레이어3 스위치가 필요하다.)

## 6-15. 태그 VLAN, IEEE802.1Q

- 복수의 스위치로 VLAN을 구성할 때 스위치 간의 접속을 태그 WXN 포트 하나로 정리할
수 있다.
- 태그 VLAN 포트에서 다루는 이더넷 프레임에는 VLAN 태그가 추가된다.

## 6-16. VLAN과 태그 VLAN

- 태그 VLAN 포트는 하나의 포트를 VUXN별로 분할해서 사용할 수 있게 한다.
- VLAN 설정에 따라서 네트워크를 어떻게 분할할지 자유롭게 결정할 수 있다.

## 6-18. VLAN 간 라우팅

- 레이어3 스위치를 이용하면 라우터보다 효율적으로 VLAN끼리 연결할 수 있다.
- 레이어3 스위치에 IP 주소를 설정해서VLAN을 연결한다.
    - 레이어3 스위치 내부의 가상 인터페이스에 IP 주소를 설정
    - 레이어3 스위치의 포트 자체에 IP 주소를 설정

## 6-19. 기본 게이트웨이

- pc와 서버에도 라우팅 테이블이 있고, 라우팅 테이블에 따라 IP 패킷을 전송한다.
- IP 주소를 설정함으로써 PC의 라우팅 테이블에 직접 접속된 경로 정보가 등록된다.
- 기본 게이트웨이의 IP 주소를 설정함으로써 PC의 라우팅 테이블에 모든 네트워크를 집약
한 디폴트 경로가 등록된다.
