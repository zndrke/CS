## Git Flow란

- 개발 방법론 / 브랜치 관리 전략



#### Branch의 종류

- master
  - 기준이 되는 브랜치로 **제품을 배포하는 브랜치**
- developer
  - 개발 브랜치로 개발자들이 **이 브랜치를 기준으로 merge**
- feature
  - **단위 기능을 개발**하는 브랜치
  - 기능 개발이 완료되면 develop 브랜치에 합침 
  - develop -> feature -> develop
- release 
  - 배포를 위해 master 브랜치로 보내기 전에 먼저 **QA를 하기위한 브랜치**
  - 모든 기능이 완료되면 develop브랜치를 release로 만듦.
  - QA를 완료하면 release 브랜치를 master와 develop 브랜치로 보냄
  - develop -> release -> master -> develop
- hotfix
  - master 브랜치로 배포를 했는데 **버그가 생겼을 때 긴급 수정하는 브랜치**
  - master -> hotfix -> master -> develop



![image-20210607130554711](C:\Users\083726\AppData\Roaming\Typora\typora-user-images\image-20210607130554711.png)





#### 테스트

1. master와 develop 브랜치 생성
2. first commit : 커밋
3. second commit (feature) : feature finish 후 develop에 병합
4. third commit (release)  : release finish 후 master에 병합 & develop에 병합
5. fourth commit (hotfix) : hotfix finish 후 master에 병합 & develop에 병합