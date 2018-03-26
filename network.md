Network Configuration
======

## 네트워크 설정 파일
1. /etc/hosts
> 호스트 이름을 기록하는 파일. 다른 방법으로는 해결할 수 없는 호스트 이름(DNS 서버가 없는 소규모 네트워크 등)의 이름을 확인할 경우에 사용한다. 네트워크 유형에 관계없이 파일에는 **lo(127.0.0.1)** 의 IP 주소를 *localhost.localdomain* 으로 지정해는 줄이 존재해야 한다.

2. /etc/resolv.conf
> DNS 서버 및 검색 도메인의 IP 주소를 지정하며, 별도로 기록하지 않은 경우에는 네트워크 초기화 스크립트의 설정을 불러온다.

3. /etc/sysconfig/network
> 모든 네트워크 인터페이스에 대한 라우팅 및 호스트 정보를 지정한다. [참고](https://www.centos.org/docs/5/html/5.1/Deployment_Guide/s2-sysconfig-network.html)

4. /etc/sysconfig/network-scripts/ifcfg-**< interface-name >**
> 각 네트워크 인터페이스별로 세부 설정이 가능하다. [참고](https://www.centos.org/docs/5/html/5.1/Deployment_Guide/s1-networkscripts-interfaces.html)

## 이더넷 인터페이스 설정 파일
- NIC를 제어하며, 여러 NIC가 있을 경우에는 *ifcfg-eth[]* 형태로 존재한다(특정 인터페이스에 해당하는 고유 번호). 각 장치마다 구성 파일이 존재하므로 관리자는 각 인터페이스가 개별적으로 작동하는 방식을 제어할 수 있다. [참고](https://www.centos.org/docs/5/html/5.1/Deployment_Guide/s2-networkscripts-interfaces-eth0.html)
- 여러 항목 중 *ONBOOT=* 항목을 **yes** 로 설정해야 시스템 재시작 시 네트워크 연결이 유지된다.
</br>
기타 네트워크 인터페이스(IPSec, channel bonding 등)의 설정방법은 [참고](https://www.centos.org/docs/5/html/5.1/Deployment_Guide/s1-networkscripts-interfaces.html)
- 네트워크 인터페이스 제어는 주로 *ifup*, *ifdown* 을 사용하며, 각각 해당 인터페이스를 up/down 하는 용도로 사용한다. [참고](https://www.centos.org/docs/5/html/5.1/Deployment_Guide/s1-networkscripts-control.html)
