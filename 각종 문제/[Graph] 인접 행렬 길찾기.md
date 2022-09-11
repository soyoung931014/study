# 문제
주어진 인접행렬에서 한 정점으로부터 다른 정점으로 이어지는 길이 존재하는지 반환해야 합니다.

## 출력
boolean 타입을 리턴해야 합니다.
## 예시
```jsx
const result = getDirections(
	[
		[0, 1, 0, 0],
		[0, 0, 1, 0],
		[0, 0, 0, 1],
		[0, 1, 0, 0],
	],
	0,
	2
);
console.log(result); // true
// 정점 0에서 2로 가는 길이 존재하는지 확인합니다.
// 0 --> 1 로 가는 간선이 존재하고, 1 --> 2 로 가는 간선이 존재하기 때문에 true를 반환합니다.

const result2 = getDirections(
	[
		[0, 1, 0, 0, 0],
		[0, 0, 0, 1, 0],
		[0, 1, 0, 0, 0],
		[0, 1, 1, 0, 0],
		[1, 1, 1, 1, 0],
	],
	1,
	4
);
console.log(result); // false

// 정점 1에서 4로 가는 길이 존재하는지 확인합니다.
// 1 --> 3,
// 3 --> 1 (정점 1을 다녀왔으니 다시 돌아가지 않습니다),
// 3 --> 2,
// 2 --> 1 (정점 1을 다녀왔으니 다시 돌아가지 않습니다)
// ...으로, 4에 도달할 수 없습니다.
```

## 풀이
```jsx
function getDirections(matrix, from, to) {

  // queue를 간단하게 생성하고, 첫 시작점으로 from을 할당합니다.
  const queue = [from];
  const enqueue = (n) => queue.push(n);
  const dequeue = (n) => queue.shift();

  // 방문했다는 것을 표시하기 위해 1차원 행렬을 생성합니다.
  const isVisited = new Array(matrix.length).fill(false);

  // 첫 정점 방문 여부를 표시합니다.
  isVisited[from] = true

  // queue(방문할 곳)의 사이즈가 0이 될 때까지 반복합니다.
  while (queue.length > 0) {

    // queue에서 정점을 하나 빼서 now에 할당합니다.
    const now = dequeue();

    // 목적지인지 검사하고, 목적지라면 true를 반환합니다.
    if (now === to) return true;

    // 해당 정점의 간선들을 확인합니다.
    for (let next = 0; next < matrix[now].length; next++) {
      // 만약, 간선이 있고 방문하지 않았다면
      if (matrix[now][next] && !isVisited[next]){
        // queue에 next를 넣습니다. (다음 정점으로 가기 위해)
        enqueue(next);
        // 해당 정점을 방문했다는 것을 표시합니다.
        isVisited[next] = true
      }
    }
    
  }

  // 길이 없다면 false를 반환합니다.
  return false;
}
```

---
어제부터 안풀려서 답답했는데, 레퍼런스 보니 내가 접근한 방법과는 전혀 달랐다. 위의 풀이는 레퍼런스를 가져왔다.
알고리즘 풀 때, 함수 만들어서 사용하는게 좀 어색하다. enqueue랑 dequeue도 간단한 함수를 할당해준 변수일 뿐이지만 왜 이리 낯설까?
아무튼 레퍼런스 처음에 봤을때 머릿속에 잘 안그려졌었는데 디버깅하면 이해는 가니까 다행이다. 역시 사고 확장에는 디버깅이 짱
계속해서 확장시켜나가보자!
![스크린샷 2022-09-11 오후 11 01 03](https://user-images.githubusercontent.com/80194405/189531626-9bf0c7e5-1634-40ce-ae66-4389d0672632.jpg)
![스크린샷 2022-09-11 오후 11 01 18](https://user-images.githubusercontent.com/80194405/189531640-daa29c21-aa63-4529-8fa5-ca627b419428.jpg)




