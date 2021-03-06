# 오늘 배운 것
___

* 팀원들끼리 각자 공부했던것들 발표(synchronous, asynchronous))
* 동기와 비동기 공부
___

## synchronous(동기)와 asynchronous(비동기)란?
___

### synchronous(동기)

자바 스크립트는 동기적인 런타임이다. 즉 , **호스팅** 한 순서 부터 실행을 한다.

직렬방식으로 값을 나오게 한다.

* 호스팅이란?
var(const, let), function declaration 이라는 함 선언들이 자동적으로 제일 위로 올라가 값을 나타내게 하는법.

예를들면 
내가 상대한테 카톡을 보내고나서 답장이 올 때까지 기다리면서 아무것도 못하는 상태에서 답장이 오기까지 기다리는것을
동기 방식이라고 생각하면 편함.

### asynchronous(비동기)
동기와는 다르게 작업이 동시다발적으로 이행하는 것.

동기방식은 위에서 순차적으로 차례로 값을 가져올때 까지 기다려야 하는 반면 비동기방식은 값이 오길 기다리면서 다른 값을 나타나게 해준다.

예를들면
카톡을 상대에게 보내고 나서 상대에게 답장이 올때까지 기다리는게 아니라 그 과정에서 내가 게임을 하던가 , 
영상을 보는 중에 답장이 오는 것. 즉 여러가지 일을 다방면으로 할 수 일을 비동기 방식이라고 한다.
___

## synchronous(동기)방식의 예
___

예를들면

```console.log(’1’)
console.log(’2’)
console.log(’3’)
```

결과 값
```1
2
3
```
순차적으로 찍힐 것입니다.
___

## asynchronous(비동기)방식의 예
___

콜백 함수를 이용하여 작업을 하여 일을 좀 더 원할하게 수행 할수 있는데

```console.log(’1’) 
setTimeout(functiom(){
	console.log(’2’)
})
console.log(’3’)
```
결과 값
```1
3
2
```
2라는 결과 값이 오기 까지 3이 결과가 나오고 2를 부르게 된다. 만약 엄청 많은 결과 값이 있다고 가정했을 경우 3 다음이 아니라 무수히 많은 값을 가져오는 도중에 2라는 값을 중간에 넣을 것이다.

___

## synchronous(동기)와 asynchronous(비동기)의 장단점
___

synchronous(동기)방식
장점 : 설계를 할때 굉장히 간단하고 직관적이다.
단점 : 결과 값을 반환 될때까지 아무것도 못하고 기다려야 한다.

asynchronous(비동기)방식
장점 : 결과 값이 반환 되는것이 시간이 오래걸리지만 그동안에 다른 것을 할 수 있다.

단점 : 동기 방식보다 복잡하다.
___

## 느낀 점
___

동기와 비동기를 공부하면서 이번 팀작업에서 발표를 할때 구체적으로 공부를 해보니깐
동기와 비동의기 편리성과 중요성을 깨달았다. 앞으로도 항해를 하면서 모르겠거나 알고싶은걸 집중적으로 공부해서 다른 사람에게 전달 할 때
정확한 기능과 정보를 줄 수 있도록 노력해야겠다.

참고로 node.js는 비동기 방식으로 운영이 되어 비동기 방식의 문법인 promise -> async or awatie에 대해서도 TIL을 올려야 겠다.
