# node를 적은 이유는 npm을 포함하고 있는 이미지이기 때문에 적어준다. 버전은 상관 X
FROM node:10

WORKDIR /usr/src/app

# 파일을 복사해 주어야 npm install 이 가능하다 package.json을 보기 때문에
# docker run -p 포트:맵핑포트 <컨테이너아이디/이름>
# volume을 사용해서 어플리케이션을 실행하는 방법
# docker run -p 5000:8080 -v /usr/src/app/node_modules -v $(pwd):/usr/src/app <이미지 아이디>
# 첫번째는 호스트 디렉토리에 node_module은 없기에 컨테이너에 맵핑을 하지 말라고 하는 것 (맵핑 하지말 것)
# 두번째는 pwd 경로에 있는 디렉토리 혹은 파일을 /usr/src/app 경로에서 참조하라는 것 (맵핑 할 것)
COPY package*.json ./

RUN npm install

# bundle
# 위에서 한번에 COPY를 적어주게 되면 종속성 문제로 소스코드를 수정하게 되면 npm install을 한번더 하게됨.
# 이렇게 해줘야 모듈은 모듈에 변화가 생길때만 다시 다운받아주며, 소스 코드에 변화가 생길때 모듈을 다시 받는 현상을 없애줌.
COPY . .

CMD ["npm","start"]