## 도커 설치
- [도커 공식 홈페이지](https://docs.docker.com/get-docker/)에서 도커 프로그램을 다운 받아서 설치한다.

## 도커 빌드하기
- 먼저 NestJS 예제 파일 및 폴더가 생성되어 있는 상태여야 한다. [installNextJS.md](./installNextJS.md) 파일을 보고 설치가 되어 있는지 확인하자.
- 프로젝트 폴더를 클론 했다면 예제 폴더 및 파일이 세팅되어 있으므로 위 과정을 건너 뛰어도 된다.
- 다음 명령어로 빌드해 보자.
```
docker build -t nextjs-docker .
```
- `-t` 옵션은 빌드된 도커 이미지에 `nextjs-docker`라는 이름을 붙인 것이며 마지막의 `.`은 현재 디렉토리를 대상으로 빌드를 한다는 의미이다. 현재 디렉토리에서 `Dockerfile`을 찾아서 그 안에 정의된 명령에 따라서 도커 이미지를 만든다.

## 빌드된 도커 이미지 인스턴스화하기
```
docker run -p 3000:3000 nextjs-docker
```

### 빌드된 서버에 접속해 보기
```
http://localhost:3000/
```
- 위 주소로 접근하면 웹 페이지가 나오는 것을 확인할 수 있다.

### 도커 서버 중지하기
- 도커 서버를 중지하기 위해서는 사용되고 있는 도커 인스턴스의 명칭을 알아야 한다.
```
docker ps
```
- 다음과 같은 리스트가 뜬다.
```
CONTAINER ID   IMAGE           COMMAND                  CREATED        STATUS        PORTS                                NAMES
22efdcf1ad7d   nextjs-docker   "docker-entrypoint.s…"   15 hours ago   Up 15 hours   0.0.0.0:3000->3000/tcp               hungry_shamir
```
- nextJS가 실행중인 서버는 IMAGE 명칭이 `nextjs-docker`인 대상이고 이 대상의 컨테이너 아이디는 `22efdcf1ad7d`이다. 도커 인스턴스 아이디는 도커 인스턴스를 실행할 때 마다 바뀌기 때문에 위 예시의 아이디와 일치하지 않는다.
- 도커를 인스턴스를 중지시키는 명령어는 ID로 중지할 도커 인스턴스를 선택한다. 다음 명령어로 도커를 정지시켜 보자.
```
docker stop 22efdcf1ad7d
```
- 삭제 되었는지를 확인하려면 `docker ps`라는 명령어를 실행하여 `22efdcf1ad7d   nextjs-docker   "docker-entrypoint.s…"   15 hours ago   Up 15 hours   0.0.0.0:3000->3000/tcp` 부분이 사라졌는지 확인하자.
