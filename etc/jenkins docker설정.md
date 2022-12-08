# jenkins docker 설정



![architecture](jenkins_docker_setting.assets/architecture.svg)



### 목차

1. [방화벽 설정](#방화벽-설정)
2. [Docker 설치](#docker-설치)
3. [젠킨스 설치 및 계정 생성](#젠킨스-설치-및-계정-생성)
4. [젠킨스 프로젝트 생성, 웹훅 설정, 자동 빌드 테스트](#젠킨스-프로젝트-생성-웹훅-설정-자동-빌드-테스트)
5. [젠킨스 도커 이미지 빌드](#젠킨스-도커-이미지-빌드)
6. [젠킨스에서 SSH 명령어를 통해 저장한 도커 이미지로 컨테이너 생성](#젠킨스에서-ssh-명령어를-통해-저장한-도커-이미지로-컨테이너-생성)



### 방화벽 설정

- 사전 준비: AWS EC2

- ubuntu 계정 접속

  - Session - SSH
  - Remote host: host 주소 입력
  - Specify username: ubuntu 입력
  - Advanced SSH settings
  - Use private key: pem 파일 등록

- 방화벽 설정

  ```bash
  sudo ufw default deny incoming
  sudo ufw default allow outgoing
  
  sudo ufw allow ssh
  sudo ufw allow http
  sudo ufw allow https
  
  sudo ufw allow 8080
  sudo ufw allow 9090  # jenkins
  
  ...
  ```

- 방화벽 설정 확인

  ![firewall](jenkins_docker_setting.assets/firewall.png)

  ```bash
  sudo ufw status
  Status: inactive
  ```

  - 기본적으로 비활성화 된 상태

  ```bash
  sudo ufw enable
  Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
  Firewall is active and enabled on system startup
  ```

  - 방화벽 활성화

  ```bash
  sudo ufw status
  Status: active
  
  To                         Action      From
  --                         ------      ----
  22/tcp                     ALLOW       Anywhere
  80/tcp                     ALLOW       Anywhere
  443/tcp                    ALLOW       Anywhere
  8080                       ALLOW       Anywhere
  9090                       ALLOW       Anywhere
  8000                       ALLOW       Anywhere
  3000                       ALLOW       Anywhere
  3306                       ALLOW       Anywhere
  3306/tcp                   ALLOW       Anywhere
  22/tcp (v6)                ALLOW       Anywhere (v6)
  80/tcp (v6)                ALLOW       Anywhere (v6)
  443/tcp (v6)               ALLOW       Anywhere (v6)
  8080 (v6)                  ALLOW       Anywhere (v6)
  9090 (v6)                  ALLOW       Anywhere (v6)
  8000 (v6)                  ALLOW       Anywhere (v6)
  3000 (v6)                  ALLOW       Anywhere (v6)
  3306 (v6)                  ALLOW       Anywhere (v6)
  3306/tcp (v6)              ALLOW       Anywhere (v6)
  ```



### Docker 설치

- 사전 패키지 설치

  ![Docker_install1](jenkins_docker_setting.assets/Docker_install1.png)

  ```bash
  sudo apt update
  sudo apt-get install -y ca-certificates \
      curl \
      software-properties-common \
      apt-transport-https \
      gnupg \
      lsb-release
  ```

- gpg 키 다운로드

  ![Docker_install2](jenkins_docker_setting.assets/Docker_install2.png)

  ```bash
  sudo mkdir -p /etc/apt/keyrings
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
  ```

- Docker 설치

  ```bash
  sudo apt update
  sudo apt install docker-ce docker-ce-cli containerd.io docker-compose
  ```

  

### 젠킨스 설치 및 계정 생성

- docker-compose 이용하여 젠킨스 컨테이너 생성

  ![jenkins_install1](jenkins_docker_setting.assets/jenkins_install1.png)

  ```bash
  vim docker-compose.yml
  ```

  ```yaml
  version: '3'
  
  services:
      jenkins:
          image: jenkins/jenkins:lts
          container_name: jenkins
          volumes:
              - /var/run/docker.sock:/var/run/docker.sock
              - /jenkins:/var/jenkins_home
          ports:
              - "9090:8080"
          privileged: true
          user: root
  ```

  - volumes
    - aws `/var/run/docker.sock`와 컨테이너의 `/var/run/docker.sock` 연결
    - aws `/jenkins`와 컨테이너의 `/var/jenkins_home` 연결
  - ports
    - aws 9090 포트와 컨테이너의 8080 포트 연결
  - user
    - 젠킨스에 접속할 유저 계정
  - 작성 후 `esc` + `:wq` + `enter`

- 컨테이너 생성

  ```bash
  sudo docker-compose up -d
  ```

- 컨테이너 확인

  ![jenkins_install2](jenkins_docker_setting.assets/jenkins_install2.png)

  ```bash
  sudo docker ps
  ```

  - django와 react는 젠킨스 설정 후 추가됨

- 젠킨스 계정 생성 및 플러그인 설치

  ![jenkins_install3](jenkins_docker_setting.assets/jenkins_install3.png)

  - `{ip 주소}:9090` 으로 접속

  ![jenkins_install4](jenkins_docker_setting.assets/jenkins_install4.png)

  - Administrator password 확인 및 입력

    ```bash
    sudo docker logs jenkins
    ```

  ![jenkins_install5](jenkins_docker_setting.assets/jenkins_install5.png)

  - `Install suggested plugins` 클릭

  ![jenkins_install6](jenkins_docker_setting.assets/jenkins_install6.png)

  - 플러그인 설치 모습

  ![jenkins_install7](jenkins_docker_setting.assets/jenkins_install7.png)

  - 젠킨스 계정 생성 `Save and Continue` 클릭
  - `Save and Finish` 및 `Start using Jenkins` 클릭

  ![jenkins_install8](jenkins_docker_setting.assets/jenkins_install8.png)

  - `Jenkins 관리` 탭 클릭

  ![jenkins_install9](jenkins_docker_setting.assets/jenkins_install9.png)

  - `플러그인 관리` 클릭

  ![jenkins_install10](jenkins_docker_setting.assets/jenkins_install10.png)

  - `gitlab` 검색 후 표시된 플러그인 체크
  - `Install witout restart`

  ![jenkins_install11](jenkins_docker_setting.assets/jenkins_install11.png)

  - `docker` 검색 후 표시된 플러그인 체크
  - `Install witout restart`

  ![jenkins_install12](jenkins_docker_setting.assets/jenkins_install12.png)

  - `SSH` 검색 후 표시된 플러그인 체크
  - `Install witout restart`

- 모든 설치 완료



### 젠킨스 프로젝트 생성, 웹훅 설정, 자동 빌드 테스트

- 사전 준비: 깃랩 레포지토리 생성

  ![jenkins_project1](jenkins_docker_setting.assets/jenkins_project1.png)

  - 구성: `BE`(장고 프로젝트),  `FE/bom`(리액트 프로젝트)

- 젠킨스 프로젝트 생성

  ![jenkins_project2](jenkins_docker_setting.assets/jenkins_project2.png)

  - `+ 새로운 Item` 클릭

  ![jenkins_project3](jenkins_docker_setting.assets/jenkins_project3.png)

  - 프로젝트 이름 작성 (`thundervolt`), `Freestyle project` 클릭 및 `OK`

  ![jenkins_project4](jenkins_docker_setting.assets/jenkins_project4.png)

  - `구성 - 소스 코드 관리`에서 `None`을 `Git`으로 변경
  - `Repository URL`에 깃랩 레포지토리 URL 입력
  - 에러메시지 출력 정상

  ![jenkins_project5](jenkins_docker_setting.assets/jenkins_project5.png)

  - `Credentials - Add - Jenkins` 클릭

  ![jenkins_project6](jenkins_docker_setting.assets/jenkins_project6.png)

  - Kind: Username with password
  - Username: 깃랩 아이디
  - Password: 깃랩 비밀번호
  - ID: Credential 구별할 텍스트
  - 입력 후 `Add` 클릭

  ![jenkins_project7](jenkins_docker_setting.assets/jenkins_project7.png)

  - 생성된 Credentials 를 클릭했을 때 오류가 사라지면 성공

  ![jenkins_project8](jenkins_docker_setting.assets/jenkins_project8.png)

  - `Branches to build` 빌드할 브랜치 설정
  - dev 브랜치를 빌드하기 위해 `*/dev` 작성

  ![jenkins_project9](jenkins_docker_setting.assets/jenkins_project9.png)

  - `빌드 유발` 탭에서 `Build when a change is pushed to GitLab` 체크

  ![jenkins_project10](jenkins_docker_setting.assets/jenkins_project10.png)

  - `고급` 클릭

  ![jenkins_project11](jenkins_docker_setting.assets/jenkins_project11.png)

  - `Secret token`에서 `Generate` 클릭하여 토큰 생성
  - 이 토큰을 통해 깃랩 웹훅 연결하기 때문에 저장해두기

  ![jenkins_project12](jenkins_docker_setting.assets/jenkins_project12.png)

  - `Build Steps` 탭에서 `Add build step` 클릭
  - `Execute shell` 선택

  ![jenkins_project13](jenkins_docker_setting.assets/jenkins_project13.png)

  - 명령어 입력 칸이 생성됨
  - 연결 테스트를 위해 간단한 명령어만 작성
  - `저장` 클릭

  ![jenkins_project14](jenkins_docker_setting.assets/jenkins_project14.png)

  - 프로젝트 화면에서 `지금 빌드`를 클릭하여 수동 빌드 진행

  ![jenkins_project15](jenkins_docker_setting.assets/jenkins_project15.png)

  - 완료 표시가 뜨면 성공

  ![jenkins_project16](jenkins_docker_setting.assets/jenkins_project16.png)

  - `Console Output`을 통해 콘솔 출력 확인 가능

  ![jenkins_project17](jenkins_docker_setting.assets/jenkins_project17.png)

  - 빌드에 성공한 콘솔 창

- 깃랩 웹훅 설정 및 자동 빌드 테스트

  ![jenkins_project18](jenkins_docker_setting.assets/jenkins_project18.png)

  - 깃랩 레포지토리에서 `설정 - 웹훅` 클릭

  ![jenkins_project19](jenkins_docker_setting.assets/jenkins_project19.png)

  - URL: 연결할 젠킨스 프로젝트 주소
  - Secret token: 젠킨스 프로젝트 생성할 때 저장한 토큰 값
  - Trigger: `Push events`와 `Merge request events` 체크
  - 대상 브랜치는 `dev`

  ![jenkins_project20](jenkins_docker_setting.assets/jenkins_project20.png)

  - `Add webhook` 클릭
  - `테스트` 클릭, `Push events` 선택

  ![jenkins_project21](jenkins_docker_setting.assets/jenkins_project21.png)

  - 코드 200 확인

  ![jenkins_project22](jenkins_docker_setting.assets/jenkins_project22.png)

  - 젠킨스에서 빌드 성공 확인
  - 젠킨스와 깃랩 연결 끝



### 젠킨스 도커 이미지 빌드

젠킨스에서 도커 빌드를 하기 위해 젠킨스 컨테이너 안에 도커 설치

EC2에 도커 설치할 때와 동일하게 진행

- Jenkins bash shell에 접근

  ![jenkins_docker_image_build1](jenkins_docker_setting.assets/jenkins_docker_image_build1.png)

  ```bash
  sudo docker exec -it jenkins bash
  ```

- 사전 패키지 설치

  ```bash
  apt update
  apt-get install -y ca-certificates \
      curl \
      software-properties-common \
      apt-transport-https \
      gnupg \
      lsb-release
  ```

  - 루트 계정이기 때문에 명령어에 sudo 넣지 않기

- gpg 키 다운로드

  ```bash
  mkdir -p /etc/apt/keyrings
  curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
  ```

- Docker 설치

  ```bash
  apt update
  apt install docker-ce docker-ce-cli containerd.io docker-compose
  ```

- 프로젝트에 Dockerfile 작성

  - 파일명 `Dockerfile`
  - 확장자 없음
  - 프로젝트가 위치한 곳에 작성

  ```dockerfile
  # Django
  
  FROM python:3.9.15
  ENV PYTHONUNBUFFERED 1
  
  RUN apt-get update && apt-get install default-libmysqlclient-dev
  
  WORKDIR /var/jenkins_home/workspace/thundervolt/BE
  
  COPY . .
  RUN pip install --upgrade pip
  RUN pip install --upgrade setuptools
  
  RUN pip install -r requirements.txt
  
  CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
  ```

  ```dockerfile
  # React
  
  FROM node:16.16.0 as build-stage
  ENV WDS_SOCKET_PORT=443
  WORKDIR /var/jenkins_home/workspace/thundervolt/FE/bom
  
  COPY package*.json ./
  RUN npm install
  
  COPY . .
  RUN npm run build
  
  EXPOSE 3000
  
  CMD ["npm", "start"]
  ```

- 젠킨스에서 Dockerfile을 이용하여 도커 이미지 생성

  ![jenkins_docker_image_build2](jenkins_docker_setting.assets/jenkins_docker_image_build2.png)

  - 젠킨스 프로젝트에서 `구성` 클릭

  ![jenkins_docker_image_build3](jenkins_docker_setting.assets/jenkins_docker_image_build3.png)

  - `Build Steps`로 이동하여 기존의 명령어 삭제

  ```bash
  docker image prune -a --force
  mkdir -p /var/jenkins_home/images_tar
  
  cd /var/jenkins_home/workspace/thundervolt/BE/
  docker build -t django .
  docker save django > /var/jenkins_home/images_tar/django.tar
  
  cd /var/jenkins_home/workspace/thundervolt/FE/bom/
  docker build -t react .
  docker save react > /var/jenkins_home/images_tar/react.tar
  
  # ls /var/jenkins_home/images_tar (확인용)
  ```

  - 위 명령어로 변경 후 저장

  ![jenkins_docker_image_build4](jenkins_docker_setting.assets/jenkins_docker_image_build4.png)

  - `지금 빌드`를 통해 수동 빌드

  ![jenkins_docker_image_build5](jenkins_docker_setting.assets/jenkins_docker_image_build5.png)

  - 빌드 성공 확인



### 젠킨스에서 SSH 명령어를 통해 저장한 도커 이미지로 컨테이너 생성

- 사전 준비: EC2 root, ubuntu 비밀번호 설정

  ```bash
  sudo passwd root
  New password:  # 비밀번호 입력
  Retype new password:  # 비밀번호 재입력
  passwd: password updated successfully  # 설정 완료
  ```

  ```bash
  sudo passwd ubuntu
  New password:  # 비밀번호 입력
  Retype new password:  # 비밀번호 재입력
  passwd: password updated successfully  # 설정 완료
  ```

- 젠킨스 SSH 설정

  ![jenkins_container1](jenkins_docker_setting.assets/jenkins_container1.png)

  - 젠킨스 홈페이지에서 `Jenkins 관리` 클릭
  - `시스템 설정` 클릭

  ![jenkins_container2](jenkins_docker_setting.assets/jenkins_container2.png)

  - `Publish over SSH`에서 `SSH Servers`의 `추가` 버튼클릭

  - Name: 이름
  - Hostname: EC2 IP
  - Username: EC2 접속 계정 이름 (ubuntu)
  - `고급`버튼 클릭

  ![jenkins_container3](jenkins_docker_setting.assets/jenkins_container3.png)

  - `Use password authentication, or use a different key` 체크
  - `Key`에 pem 파일 값 입력
    - pem 파일을 VSCode 로 열기
    - 전체 복사하여 붙여넣기

  ![jenkins_container4](jenkins_docker_setting.assets/jenkins_container4.png)

  - `Test Configuration` 클릭, `Success`가 나오면 성공
  - SSH 연결 완료, `저장` 버튼 클릭

- 젠킨스 빌드 후 조치로 SSH 명령어 전송 (EC2에 도커 컨테이너 생성)

  ![jenkins_container5](jenkins_docker_setting.assets/jenkins_container5.png)

  - 젠킨스 프로젝트 페이지에서 `구성` 클릭

  ![jenkins_container6](jenkins_docker_setting.assets/jenkins_container6.png)

  - `빌드 후 조치 추가`클릭, `Send build artifacts over SSH` 선택

  ![jenkins_container7](jenkins_docker_setting.assets/jenkins_container7.png)

  - Source files: 컨테이너에서 AWS로 파일을 전송하는 부분 (중요X)

  ![jenkins_container8](jenkins_docker_setting.assets/jenkins_container8.png)

  ```bash
  sudo docker load < /jenkins/images_tar/django.tar
  sudo docker load < /jenkins/images_tar/react.tar
  
  if (sudo docker ps | grep "django"); then sudo docker stop django; fi
  if (sudo docker ps | grep "react"); then sudo docker stop react; fi
  
  sudo docker run -it -d --rm -p 8000:8000 --name django django
  # echo "Run BE"  (확인용)
  sudo docker run -it -d --rm -p 3000:3000 --name react react
  # echo "Run FE"  (확인용)
  ```

  - `Exec command`에 명령어 입력
  - `sudo docker load < /jenkins/images_tar/django.tar`
    - `django.tar`를 압축 해제하여 docker 이미지로 등록
  - `if (sudo docker ps | grep "django"); then sudo docker stop django; fi`
    - django 컨테이너가 동작중이면 멈춤
  - `sudo docker run -it -d --rm -p 8000:8000 --name django django`
    - django 이름으로 컨테이너 생성, 8000번 포트로 연결
  - `저장` 클릭
  - `지금 빌드`를 통해 빌드, 콘솔 창에서 결과 확인