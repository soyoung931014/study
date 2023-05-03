n=1일 경우 // 1가지

n=2일 경우 // 2가지

n=3일 경우// 3가지

n=4일 경우// 5가지

n=5가지일 경우 //8가지가 나온다.

1,2,3,5,8,...으로 변화하고 있는데 '피보나치 수열'
피보나치 수열을 재귀함수로 구현할 때 콜 스택에 굉장히 무리가 가게 되는데 이는 동일한
계산을 계속 반복하기 때문이다. 때문에 이를 해결하기 위해 메모이제이션이라는 방식을 사용하게 되는데 쉽게 말하면 
DP(Dynamic Programming)과 유사하다. 또한  ‘경우의 수가 많아 질 수 있으므로, 경우의 수를 1,000,000,007으로 나눈 나머지를 return해주세요.’라는 조건이
적혀있는걸로 보아 이러한 문제는 보통 DP와 같은 이전 값을 활용하여 누적하는 방식의 문제인 경우가 많다. 물론 아닐 가능성도 있기때문에 그냥 접근 방향을 결정할 때 한 번 스치듯 생각해보고 지나가자.
- 내 풀이
```jsx
function solution(n) {
    let dy = Array.from({length: n+1}, () => 0)
    dy[0]=1
    dy[1]=1
    for(let i=2; i<dy.length; i++){
       dy[i] = (dy[i-2]+dy[i-1]) % 1000000007 
    }
    
    return dy[n] 
}
```

- 다른 사람 풀이
```jsx

function solution(n) {
  const arr = [0, 1, 2];
  for (let i = 3; i <= n; i++) {
    arr[i] = (arr[i - 2] + arr[i - 1]) % 1000000007;
  }

  return arr[n];
}
```
### 규칙찾기

<img src="https://user-images.githubusercontent.com/80194405/235822207-82e71327-3b82-4e98-9d82-5575bbce2d97.jpg" width="500" height="650"/>

### 같이 참고하면 좋을 자료
https://happy-time-daily-blog.tistory.com/47 



