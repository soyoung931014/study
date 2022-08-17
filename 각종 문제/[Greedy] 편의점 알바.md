# 문제
---
편의점에서 아르바이트를 하고 있는 중에, 하필이면 피크 시간대에 손님에게 거스름돈으로 줄 동전이 부족하다는 것을 알게되었다. 현재 가지고 있는 동전은 1원, 5원, 10워, 50워, 100원, 500원으로 오름차순으로 정렬되어있고, 각 동전들은 서로 배수 관계에 있다.

동전 개수를 최소화하여 거스름돈 K를 만들어야 한다. 이 때, 필요한 동전 개수의 최솟값을 구하는 함수를 작성해주세요


# 풀이
---

```jsx
-레퍼런스 풀이
function partTimeJob(k) {
  let result = 0;
  const wallet = [500, 100, 50, 10, 5, 1];
  for(let i = 0; i < wallet.length; i++) {
    if(k > 0) {
      const sum = Math.floor(k / wallet[i]);
      result += sum;
      k = k - (wallet[i] * sum);  //✅ 이렇게도 나머지를 구할 수 있구나
    }
  }
  return result;
}

- 내 풀이
function partTimeJob(k) {  
  let coin = [500, 100, 50, 10, 5, 1]
  let count = 0
  for(let i = 0; i < coin.length; i++) {

    if(k%coin[i] > 0){
      count = count + Math.floor(k/coin[i])
      k = k%coin[i]
    }else{
      count = count + Math.floor(k/coin[i])
      break
    }
    
  }
return count
}

- 수정된 내 풀이
function partTimeJob(k) {

  let coin = [500, 100, 50, 10, 5, 1]
  let count = 0
  for(let i = 0; i < coin.length; i++) {

    if(k>0){
      count = count + Math.floor(k/coin[i])
      k = k%coin[i]
    }

  }
return count
}

- 수도코드 
각각의 동전을 배열에 집어 넣는다.
let coin = [500, 100, 50, 10, 5, 1]
let count = 0
 반복문을 돌려서 
  k / coin[i] 의 몫은  count에 더해지고
 k = k % coin[i]의 나머지값까지 구하고 count 더해주고 break 추가시킨다.
```
