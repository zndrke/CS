### EUC-KR

- 2byte
- 한글로만 작성하는 경우 유리



### UTF-8

- 3byte
- 모든 문자 작성 가능



#### 변환방법

- test.txt 파일을 utf-8로 변환하여 모니터링 하는 경우

1. 리눅스
   - luit -encoding EUCKR -- tail -f test.txt
2. 유닉스
   - tail -f test.txt | iconv -f cp949 -t utf8
   - tail -f test.txt | pgconv (alias)



- luit는 서로다른 character set을 사용하는 터미널 에뮬레이터를 번역하기 위한 유틸 프로그램
- luit는 input과 output이 상호작용하는 프로그램을 전환
- iconv는 고정된 스트링이나 문자파일을 전환하기 위해 사용
