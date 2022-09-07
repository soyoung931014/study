# 문제
방향이 있는 간선과 방향이 없는 간선들의 목록들을 받아 2차원 배열의 인접행렬을 반환하는 함수를 작성하세요.

---
### 입출력 예시
```jsx
const output1 = createMatrix([
	[0, 3, "directed"],
	[0, 2, "directed"],
	[1, 3, "directed"],
	[2, 1, "directed"],
]);

console.log(output1);
/**
 * [
 *  [0, 0, 1, 1],
 *  [0, 0, 0, 1],
 *  [0, 1, 0, 0],
 *  [0, 0, 0, 0]
 * ]
 */

const output2 = createMatrix([
	[0, 2, "directed"],
	[2, 4, "undirected"],
	[1, 3, "undirected"],
	[2, 1, "directed"],
]);

console.log(output2);
/**
 * [
 *  [0, 0, 1, 0, 0],
 *  [0, 0, 0, 1, 0],
 *  [0, 1, 0, 0, 1],
 *  [0, 1, 0, 0, 0],
 *  [0, 0, 1, 0, 0],
 * ]
 */
```
---
# 풀이
```jsx
function createMatrix(edges) {
  let max = 0
	for(let i = 0; i<edges.length; i++) {
		const curMax = Math.max(...edges[i].slice(0,2)) // slice를 해줘야 하는 이유는?
		// ✅ edges의 한 요소에는 숫자 이외에 방향성도 있으니, 숫자까지만 slice를 하여 비교해야한다. 문자열까지 포함되면 NaN나옴
		curMax>max ? (max = curMax): null
	}
	//max는 결국 3이나옴 length = 3인 매트릭스를 만들자!
✅	const matrix = new Array(max+1).fill(0).map((row) => new Array(max+1).fill(0))

✅	edges.forEach(edge => {
		const [row, column, direction] = edge
		if(direction === 'undirected') {
			matrix[column][row] = 1
		}
		matrix[row][column]=1
	})
	return matrix
}
```
----
### 수도코드
- 최대 크기를 찾아야함. matrix가 가로세로 몇줄인지.. 그건 edges를 통해 추출할 수 있음
- 최대 크기 추출한거로 0으로 가득찬 matrix를 만든다.(뼈대를 만듦)
- edges를 반복문 돌려서 각각 요소들 구조분해할당해주고 directed or undirected일 경우 나눠줘   matrix[row][column] = 1이런식으로 그려줌 
- matrix를 리턴하면 완성!

