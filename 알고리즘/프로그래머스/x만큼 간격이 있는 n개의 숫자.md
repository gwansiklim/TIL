# 문제 설명

함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다.<br/>
다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.

### 제한 조건

* x는 -10000000 이상, 10000000 이하인 정수입니다.
* n은 1000 이하인 자연수입니다.

### 입출력 예

<table>
  <td>x</td>
  <td>n</td>
  <td>answer</td>
  <tr>
    <td>2</td>
    <td>5</td>
    <td>[2,4,6,8,10]</td>
  </tr>
  <tr>
  <td>4</td>
  <td>3</td>
  <td>[4,8,12]</td>
  </tr>
  <tr>
  <td>-4</td>
  <td>2</td>
  <td>[-4, -8]</td>
  </tr>
</table>

### 초기 코드

```
function solution(x, n) {
    var answer = [];
    return answer;
}
```

### 풀이

```
function solution(x, n) {
    var answer = [];
    for(let i = 1; i <= n; i++){
        answer.push(x * i);
    }
    return answer;
}
```

## 느낀 점 or 배운 점

아직 멀었다.. 내가 스스로 푸는 능력이 부족하고 문제 해석 능력이 부족하다...
