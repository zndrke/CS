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
