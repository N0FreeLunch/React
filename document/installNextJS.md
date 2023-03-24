## NextJS 설치하는 법
- [공식 가이드 예제 문서](https://github.com/vercel/next.js/tree/canary/examples/with-docker)
- 이 때 프로젝트 폴더명을 `next-app`으로 했는데 폴더명에 대문자가 와서는 안된다는 룰이 있다.
- 현재 폴더에 설치할 수는 없기 때문에 하위 폴더에 설치한 후 현재 폴더로 옮기는 방식을 사용한다.

### NextJS 도커 예제 설치
```
npx create-next-app --example with-docker nextjs-docker
```

### nextjs-docker 폴더 내의 파일 및 폴더를 프로젝트 루트로 옮기기
```
mv nextjs-docker/* ./
```
- 위 명령으로 옮겨지지 않는 `.gitignore` `.dockerignore` 파일을 옮기기
```
mv nextjs-docker/.* ./
```
- 빈 폴더 삭제
```
rm -r nextjs-docker
```

