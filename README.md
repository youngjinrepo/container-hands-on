## 📌 개요

본 프로젝트는 리눅스 커널의 핵심 기술들을 활용하여 도커(Docker)와 같은 고수준 도구 없이 컨테이너 환경을 바닥부터 직접 구현해 보는 핸즈온 가이드입니다. `chroot`, `pivot_root`, `Namespace`, `cgroups` 등의 로우레벨 API를 직접 제어하며 컨테이너의 격리 메커니즘과 자원 관리 원리를 심층적으로 이해하는 것을 목표로 합니다.

* **학습 강연:** [이게 돼요? 도커 없이 컨테이너 만들기 / if(kakao)2022](https://youtu.be/mSD88FuST80?si=im0H3nfS-VSHSGlO)

---

## 🛠️ 실습 환경 (Local Infrastructure)

호스트 OS(Windows) 환경의 제약을 벗어나 실제 리눅스 커널 시스템 콜을 안전하게 테스트할 수 있도록 **Vagrant**와 **VirtualBox**를 이용하여 독립된 가상 인프라 샌드박스를 구축했습니다.

### 1. 개발 스택 및 버전
* **Host OS:** Windows 10 / 11
* **Virtualization Provider:** Oracle VirtualBox (v7.2.x)
* **Infrastructure Automation:** HashiCorp Vagrant (v2.x)
* **Guest OS (Target):** Ubuntu 18.04 LTS (`ubuntu/bionic64`)

### 2. 가상 머신 구성 및 기동
프로젝트 루트 디렉토리에서 아래 명령어를 통해 가상 머신 인프라를 프로비저닝하고 호스트와 통신을 연결합니다.

```bash
# 가상 머신 설정 파일(Vagrantfile) 생성 (Vagrantfile 이미 있다면 생략)
$ vagrant init ubuntu/bionic64

# 가상 머신 생성 및 백그라운드 구동
$ vagrant up

# 구동된 리눅스 가상 머신 내부로 SSH 접속
$ vagrant ssh

# 구동된 머신 일시정지
$ vagrant halt

