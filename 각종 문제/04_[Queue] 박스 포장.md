# 문제
----
마트에서 장을 보고 박스를 포장하려고 합니다. 박스를 포장하는 데는 폭이 너무 좁습니다. 그렇기에 한 줄로 서 있어야 하고, 들어온 순서대로 한 명씩 나가야 합니다.

불행 중 다행은, 인원에 맞게 포장할 수 있는 기구들이 놓여 있어, 모두가 포장을 할 수 있다는 것입니다. 짐이 많은 사람은 짐이 적은 사람보다 포장하는 시간이 길 수밖에 없습니다.

뒷사람이 포장을 전부 끝냈어도 앞사람이 끝내지 못하면 기다려야 합니다. 앞사람이 포장을 끝내면, 포장을 마친 뒷사람들과 함께 한 번에 나가게 됩니다.

만약, 앞사람의 박스는 5 개고, 뒷사람 1의 박스는 4 개, 뒷사람 2의 박스는 8 개라고 가정했을 때, 뒷사람 1이 제일 먼저 박스 포장을 끝내게 되어도 앞사람 1의 포장이 마칠 때까지 기다렸다가 같이 나가게 됩니다.

이때, 통틀어 최대 몇 명이 한꺼번에 나가는지 알 수 있도록 함수를 구현해 주세요.

 ### 예시
 ```jsx
 const boxes = [5, 1, 4, 6];
const output = paveBox(boxes);
console.log(output); // 3

const boxes2 = [1, 5, 7, 9];
const output2 = paveBox(boxes2);
console.log(output2); // 1
```

---
# 풀이
```jsx
function paveBox(boxes) {
let count = 1
let array = []
let criteria = boxes[0]
for(let i =1; i< boxes.length; i++) {
  if(criteria < boxes[i]) {
    array.push(count)
    count = 1
    criteria = boxes[i] 
  }
  else if(criteria >= boxes[i]) { ✅ = 을 추가해줘야 테스트 모두 통과할 수 있었다
    count= count+1
  }
  
}
array.push(count)
return Math.max(...array)
}

```
