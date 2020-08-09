![](https://media.vlpt.us/images/devgosunman/post/41d02313-58a2-44d6-8034-069bab41024c/docker%20whale.png)

> "그거 내 노트북에서는 잘 돌아갔었는데!!"
> "클라우드 시대에 코드를 가장 안전하게 개발하여 배포할 수 있는 방법!!"

---

# 🙃 Docker란 정의?

## 독립된 운영환경을 가장 빠르게 구축해주는 기술!!

## 호스트 OS를 공유하는 기술!!

> 원래 서버는 절대 죽으면 안되는 operation이었지만,
> 컨테이너, 도커, 쿠버네티스 덕분에 언제든 죽어도 되는 것이 되었다.

## 데이터만 살려두면 된다.

# 🥳 도커 엔진 덕분에 촉발된 "컨테이너화" 개발 운동

> 도커 엔진은 리눅스와 윈도우 서버 OS에서 작동하는 업계 표준 컨테이너 프로그램이다.
> 도커는 프로그램의 모든 의존 관계(application dependencies)를 컨테이너 내부에 집약시킨다.
> 이렇게 집약된 컨테이너를 실행시키는 프로그램이 도커 엔진이다.
> 도커 엔진 덕분에 컨테이너화 된 모든 프로그램은 어떠한 실행 환경에서도 작동시킬 수 있다.

---

![](https://images.velog.io/images/devgosunman/post/63e32a46-9e9b-45a5-9f90-2cfd0d8dd423/docker%20engine.png)

# 😜 필요한 배경지식?

## 컨테이너 기술

## Virtual Machine

## Kubernetes, Swarm

## docker --help

- (ctl+p) + (ctl+q) : 켜놓은 상태로 나가기, exit without halt

---

# 😗 구현에 사용된 기술

- 도커는 Go 언어로 작성되어서 리눅스 커널의 다양한 기능을 사용할 수 있다.

## 네임스페이스s

- 도커는 컨테이너라고 불리는 독립된 workspace를 만들기 위해 네임스페이스를 씁니다.
- 컨테이너 하나마다 새로운 네임스페이스 조합을 부여합니다.
  1. PID: process isolation
  2. NET: managing network interfaces
  3. IPC: managing access to IPC(Inter Process Communication) resources
  4. MNT: managing filesystem mount points
  5. UTS: isolating kernel and version identifiers(Unix Timesharing System)

## 컨트롤 그룹s

- 도커 엔진은 cgroups라는 기술을 사용합니다.
- 이는 도커 엔진이 하드웨어를 컨테이너 별로 할당할 수 있게 합니다.

## 통합 파일 시스템s

- 도커 엔진은 통합 파일 시스템을 사용하여 컨테이너 별로 파일 시스템을 갖게 할 수 있다.

## 컨테이너 포맷

- 도커 엔진은 네임스페이스와 컨트롤 그룹 그리고 통합 파일시스템을 하나로 합쳐 컨테이너 포맷으로 만든다.
- 기본 컨테이너 포맷은 libcontainer라고 불린다.
- 추후 BSD jail 기능 등을 통합한 새로운 컨테이너 포맷을 제공할 예정이다.

---

![](https://images.velog.io/images/devgosunman/post/1068e362-fb54-4799-9c87-1193b27798e2/image.png)

# 😋 도커에 아키텍쳐

## 도커는 클라이언트-서버 아키텍쳐를 따른다.

## 도커 클라이언트를 통해 데몬과 소통하며 도커 컨테이너를 조작한다.

## 소통은 유닉스 소켓 통신 기반의 REST API를 이용하여 수행한다.

---

# 🤣 도커 엔진(데몬, 런타임)

- dockerd라고도 불리는 데몬
- API 요청에 따라 도커 객체(Obeject: 컨테이너, 이미지, 네트워크, 볼륨)을 관리한다.
- 데몬끼리도 소통할 수 있다.

# 😇 도커 클라이언트

- docker라고도 불리는 클라이언트
- 도커와 소통하기 위한 핵심 도구이다.
- 당신이 "docker run"과 같은 명령어를 쓰면 클라이언트가 데몬에 이를 API로 전달한다.
- 도커 클라이언트는 여러 데몬과 소통할 수 있다.

# 😆 도커 레지스트리s

- 도커 레지스트리는 도커 이미지를 저장하고 있다.
- 그 중 가장 대표적인 것은 도커 허브이다.
- 도커 허브에는 누구나 접근하여 다운로드 받고 업로드 할 수 있다.
- 물론 개인용 레지스트리를 운영할 수도 있다.

---

# 😁 도커 오브젝트

## 이미지

- 이미지는 도커 컨테이너를 생성할 때 필요한 지시사항이 포함되어 있는 읽기 전용 파일이다.
- 이미지는 다른 이미지 파일을 수정하여 만들 수도 있다.
- 그래서 당신이 직접 만든 이미지를 써도 되고, 다른 사람이 만든 이미지를 가져다 써도 된다.
- 네가 직접 만들고 싶다면 Dockerfile에 필요한 것들을 절차에 맞게 기입하고 이를 실행하면 된다.

## 컨테이너

- 컨테이너는 실행할 준비가 끝난 이미지 파일의 객체이 파일이다.
- 컨테이너는 다른 컨테이너나 호스트 머신으로부터 비교적 잘 격리되어 있다.
- "docker run -it ubuntu /bin/bash" 실행 시, 내부 구동 단계

  1. 만약 네 컴퓨터에 ubuntu 이미지가 없다면, 설정된 레지스트리에 가서 받아온다.
     - "docker pull ubuntu"를 실행한 것처럼
  2. 도커가 새로운 컨테이너를 생성한다.
     - "docker container create"을 실행한 것처럼
  3. 도커가 읽고 쓸 수 있는 파일시스템을 생성하여 컨테이너에게 전달한다.
     - 컨테이너는 그렇게 독립된 파일시스템을 갖게 된다.
  4. 도커는 컨테이너에 네트워크 인터페이스를 붙여준다.
  5. 도커가 컨테이너를 실행하고 /bin/bash 명령어를 실행한다.
     - i 옵션은 "running interactively"를 의미한다
     - t 옵션은 "attached to your terminal"을 의미한다.
  6. 만약 당신이 "exit"을 치켠 컨테이너는 중지되지만 삭제되지는 않는다.

  ***

# 😩 도커 설치 및 실행

## curl -sSL http://get.docker.com | sh

- curl은 CLI 기반 브라우저
- 원래는 url 다음에 "/script"가 생략되어 있다
- 마지막 sh는 쉘로 켜라는 의미이고, bash를 쓸 수도 있다

## systemctl start docker (도커 실행)

- systemctl enable docker (도커 자동 실행 | 컴 껐다가 켜도)

## docker version (도커 실행 확인)

## usermod -aG docker user1

- 옵션 설명 a:add, G:group
- user1을 docker 그룹에 소속시킨다.
- docker 그룹에 소속된 유저만 client 측 뿐만 아니라 server 쪽까지 조작이 가능하다.

- linux에서 유저만들고 전환하기
  - useradd user1
  - passwd user1
  - su user1 (계정 전환하기)

---

# 😇 컨테이너 생성 및 실행

## docker run -it --name con1 ubuntu /bin/bash

- 옵션 it는 interactive 라는 의미로 OS 컨테이너를 만들 때 쓴다
- 이름을 con1으로 해라
- 이때 켤 프로그램은 /bin/bash이다
- /bin/bash는 생략해도 된다

## docker run -d --name myweb -p 80:80 httpd

- 옵션 d는 detach를 의미해서 백그라운드로 켠다는 것으로 일반 프로그램을 켤 때 쓴다
- httpd는 apache 서버 프로그램이다
- p 옵션 다음에 " : " 를 기준으로
- 왼쪽 숫자는 docker 호스트 port 번호이다
- 프로그램에 따라 다르게 설정해줘야 한다
- 오른쪽 숫자는 container 호스트 port 번호이다
- 이미지에 따라 지정되어 있다.
- docker history "이미지 이름"
- 위 명령어로 이미지에 지정된 포트 번호를 알아낼 수 있다
- 그런데 다 하나의 80포트만 쓰고 싶으니 어떻게 해야할까?
- 실무에서는 프록시 서버로 전부 다 받아서 실제로 배분해준다

---

# 😝 docker 이미지 만들고 업로드 하기

- docker run -it --name myalpine alpine
- docker commit myalpine myOwnImage
- docker tag myOwnImage gosunman/"희망이름"
  - 이름은 꼭 "내 아이디/이미지 이름" 형식을 지켜야한다.
- docker login -u "아이디"
  - 로그인을 한다.
- docker push gosunman/"희망이름"

---

# 😊 Dockerfile을 사용하여 docker image 생성하기

## Dockerfile에 포함될 명령어

- FROM: 원본 이미지 이름 사용(<이미지 이름>:<태그>)
- MAINTAINER: 작성자 이름
- RUN: Shell Script 또는 Linux Command (이미지를 만드는 과정에서 실행할 명령어)
- VOLUME: 공유할 호스트의 디렉토리(컨테이너 수행중 영구적으로 저장할 데이터를 위해)
- CMD: Container가 실행되자마자 실행할 실행 파일 혹은 Shell Script
- WORKDIR: CMD에서 설정한 실행 파일이 실행될 Default Directory
- EXPOSE: 호스트와 연결할 포트 번호

## Dockerfile 예시

    - FROM ubuntu
    - MAINTAINER Yongshik Lee
    - RUN apt-get update -y
    - RUN apt-get install nginx -y
    - RUN echo "daemon off;" >> /etc/nginx/nginx.conf
    - RUN chown -R www-data:www-data /var/lib/nginx
    - VOLUME ["/data", "/etc/nginx/site-enabled", "/var/log/nginx"]
    - WORKDIR /etc/nginx
    - CMD ["nginx"]
    - EXPOSE 80
    - EXPOSE 443

---

# 😛 Data Volume이란?

- 도커 데이터 볼륨은 컨테이너에 저장될 데이터를 컨테이너가 아닌 도커 호스트에 저장하기 위한 것
- 그 결과 데이터 볼륨은 컨테이너 간의 데이터를 공유할 때 활용한다.
- 컨테이너를 실행할 때 데이터 볼륨을 지정해야 한다.

# 😎 Volume 쓰는 법

- docker volume create convol
- docker volume ls
- find / -name "convol"
- docker run -it --name con100 -v convol:/data alpine
- "/ # cd /data"
- "/data # touch secret.file"
- docker run -it --name con200 -v convol:/data alpine
- "/ # cd data/"
- "/data # ls"

---

# 😘 docker0

- 기본적으로 docker container가 host 외부와 통신할 때는 docker0라는 virtual bridge로 이루어진다.
- container를 생성할 때 network를 지정하지 않으면 기본적으로 docker0의 virtual bridge에 연결된다

# 🤗 docker network 생성하기

- docker network create --driver bridge --subnet 10.10.10.0/24 mynet

# 😏 docker run -d --name myweb2 -p 8080:80 --net host httpd

---

# 🤫 의문사항

- Docker로 운영체제를 켜면 지원되지 않는 기능이 있는게 맞나?
