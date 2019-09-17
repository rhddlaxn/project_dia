
# Hyperdia
> **하이퍼레저 기반 다이아몬드 보증서 등록, 조회, 수정 앱** <br>
하이퍼레저와 다이아를 결합한 단어(Hyperldger + dia)


## Getting started
> 다이아몬드는 그 **고유성**을 확인하기 위한 데이터가 40가지가 넘습니다. <br>
특성이 각각 다르기 때문에 모든 다이아몬드 하나하나가 엄청난 가치를 지니고 있습니다. <br>
그런데 이 아름다운 보석을 둘러싸고 인증서 위조, 거짓 분실로인한 보험 사기 등 많은 **범죄**가 일어나고 있다는 것 알고계시나요? <br>
이러한 문제의 가장 큰 핵심은 인증서가 **종이**라는 것 인데요. <br>
종이 인증서는 위변조가 쉽기 때문에 유통과정의 완벽한 **투명성**을 보장하기에는 한계가 있어서, <br>
이를 **블록체인 기술**을 활용하여 다이아몬드 유통의 전과정을 투명하게 **기록**하려고 합니다. <br>


## Team
* 권달형
* 고재현
* 김민선
* 김희재
* 문영선


## Prerequisites
* Ubuntu - 16.04
* Docker - latest
* Docker Compose - latest
* NPM - latest
* nvm - latest
* Node.js - latest
* Golang - latest
* Git client - latest
* HyperledgerFabric Example - branch 1.4


## Application Workflow
![main](https://user-images.githubusercontent.com/51254582/64236400-4affb880-cf35-11e9-9c9f-87e73bdad362.png)
* 제조사에서 다이아몬드 정보를 등록하거나 등록된 다이아몬드가 거래되어 Owner가 변경될 때마다 트랜잭션이 발생해 정보가 블록에 기록이 되기 때문에, 인증서의 위변조가 불가능하여 소비자 입장에서 더욱 신뢰성 높은 거래를 할 수 있다는 장점이 있습니다. <br>
다이아몬드가 분실되면 보험사는 고객이 신고한 다이아몬드가 분실된 다이아몬드라는 사실을 원장에 올립니다. 해당 다이아몬드의 Owner는 고객에게 분실보험금을 지급한 보험사로 변경되기 때문에, 거짓 분실로 인한 보험 사기를 방지할 수 있습니다.  <br>


## Installing
### 1. 파일을 클론합니다.
```
git clone https://github.com/blockchain207/project_dia.git
```
### 2. dia에 있는 startFabric.sh파일을 실행합니다.
```
./startFabric.sh
```
### 3. javascript폴더로 이동해 필요한 NPM을 설치합니다.
```
npm install
```
### 4. enrollAdmin.js와 registerUser.js파일을 실행합니다.
```
node enrollAdmin.js
node registerUser.js
```
> 이후 아래 이미지와 같이 연결됬다는 콘솔을 확인합니다.
![createKey](https://user-images.githubusercontent.com/51254582/65002642-d57dea00-d92f-11e9-9bc5-8688b1c4df60.PNG)


## Application scenario
![시나리오](https://user-images.githubusercontent.com/51254582/64939737-f812f300-d89c-11e9-8edf-72a8f050b22a.png)
### 1) 제조사에서 다이아몬드를 등록
```
node invoke.js
```
> 아래 이미지와 같은 콘솔이 확인되어야 합니다.
![invoke2](https://user-images.githubusercontent.com/51254582/65002947-26421280-d931-11e9-843e-eb25cc17ba4c.jpg)
### 2,3) 보석을 도난당한 고객이 보험사에 도난여부 신고 -> 보험사는 원장에 도난여부 트랜잭션 등록
```
node invokeLost.js
```
### 5,6) 보석을 훔친 도둑이 보석상에게 훔친 보석을 팔려고 시도 -> 보석상은 해당 보석의 Owner조회
```
node query.js
```
> Lost여부가 false에서 true로 바뀌고, Owner또한 기존 사용자에서 보험사(Insure Co)로 변경되었기 때문에 조회결과  분실된 보석이라는 사실 확인가능
![invokeLost](https://user-images.githubusercontent.com/51254582/65002711-1a098580-d930-11e9-857c-77c1cb40a84e.PNG)
### 7) 고객끼리 보석거래시 보증서의 Owner변경여부 등록 및 전체정보조회
```
node invokeAlter.js
node queryAll.js
```


## references
* HyperledgerFabric Example - fabcar
* 이승한,이요한,신태영「실전! 하이퍼레저 패브릭」(위키북스 해킹 & 보안 시리즈, 2019)
