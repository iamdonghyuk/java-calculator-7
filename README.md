# java-calculator-precourse
# 문자열 덧셈 계산기 📟

## 과제 진행 요구 사항 📋
- 미션은 문자열 덧셈 계산기 저장소를 포크하고 클론하는 것으로 시작한다.
- 기능을 구현하기 전 README.md에 구현할 기능 목록을 정리해 추가한다.
- Git의 커밋 단위는 앞 단계에서 README.md에 정리한 기능 목록 단위로 추가한다.
    - AngularJS Git Commit Message Conventions을 참고해 커밋 메시지를 작성한다.
- 자세한 과제 진행 방법은 프리코스 진행 가이드 문서를 참고한다.

## 기능 요구 사항 🎯
입력한 문자열에서 숫자를 추출하여 더하는 계산기를 구현한다.

- 쉼표(,) 또는 콜론(:)을 구분자로 가지는 문자열을 전달하는 경우 구분자를 기준으로 분리한 각 숫자의 합을 반환한다.
    - 예: "" => 0, "1,2" => 3, "1,2,3" => 6, "1,2:3" => 6
      앞의 기본 구분자(쉼표, 콜론) 외에 커스텀 구분자를 지정할 수 있다. 커스텀 구분자는
- 문자열 앞부분의 "//"와 "\n" 사이에 위치하는 문자를 커스텀 구분자로 사용한다.
    - 예를 들어 "//;\n1;2;3"과 같이 값을 입력할 경우 커스텀 구분자는 세미콜론(;)이며, 결과 값은 6이 반환되어야 한다.
- 사용자가 잘못된 값을 입력할 경우 IllegalArgumentException을 발생시킨 후 애플리케이션은 종료되어야 한다.

## 입출력 요구 사항 🖨️
입력
- 구분자와 양수로 구성된 문자열

출력
- 덧셈 결과

`결과 : 6`

실행 결과 예시
```
덧셈할 문자열을 입력해 주세요.
1,2:3
결과 : 6
```
# 문제 해결 방안
- 사용자로부터 입력 받은 문자열을 구분자로 분리 후 문자열 배열에 담아 숫자로 변환 후 누적합을 구한다.

# 문제 풀이법
- 입력 받으면 문자열이 있는지 확인 
- 분리 할 구분자를 기본 구분자(",",":")로 지정
- 문자열 문두에 "//" 일 경우 "//"과 "\n" 사이 구분자를 분리 할 구분자로 지정
- 지정된 분리 할 구분자를 통해 문자열을 분리
- 분리 된 문자열은 숫자로 변환
- 변환된 숫자는 반복문을 통해 누적합을 구하여 출력

# 주의 할 점
- 입력 받은 문자열이 없을 경우 0 으로 출력
- 문자열에 공백을 제거
- "//"과 "\n" 사이에 구분자가 없을 경우
```
//\n1;2;3     IllegalArgument 에러 발생
```
- "//"는 있지만 "\n"이 없는 경우
```
//1;2;3     IllegalArgument 에러 발생
```
- 누적합을 하기 전 trim()으로 인해 비어있는 요소가 있는 경우 continue
- 숫자로 변환된 값이 음수일 경우 IllegalArgument 에러 발생
