# 문제
----
개발자가 되고 싶은 김코딩은 자료구조를 공부하고 있습니다. 인터넷 브라우저를 통해 스택에 대해 검색을 하면서 다양한 페이지에 접속하게 되었는데 "뒤로 가기", "앞으로 가기"를 반복하면서 여러 페이지를 참고하고 있었습니다.

그런데 새로운 페이지를 접속하게 되면 "앞으로 가기" 버튼이 비활성화돼서 다시 보고 싶던 페이지로 갈 수 없었습니다. 이러기를 반복하다가 김코딩은 스택 자료구조를 떠올리게 되었습니다.

브라우저에서 "뒤로 가기", "앞으로 가기" 기능이 어떻게 구현되는지 궁금해진 김코딩은 몇 가지 조건을 아래와 같이 작성하였지만, 막상 코드를 작성하지 못하고 있습니다.

### 조건
새로운 페이지로 접속할 경우 prev 스택에 원래 있던 페이지를 넣고 next 스택을 비웁니다.

뒤로 가기 버튼을 누를 경우 원래 있던 페이지를 next 스택에 넣고 prev 스택의 top에 있는 페이지로 이동한 뒤 prev 스택의 값을 pop 합니다.

앞으로 가기 버튼을 누를 경우 원래 있던 페이지를 prev 스택에 넣고 next 스택의 top에 있는 페이지로 이동한 뒤 next 스택의 값을 pop 합니다.

브라우저에서 뒤로 가기, 앞으로 가기 버튼이 비활성화일 경우(클릭이 되지 않을 경우)에는 스택에 push 하지 않습니다.

인터넷 브라우저에서 행동한 순서가 들어있는 배열 actions와 시작 페이지 start가 주어질 때 마지막에 접속해 있는 페이지와 방문했던 페이지들이 담긴 스택을 반환하는 솔루션을 만들어 김코딩의 궁금증을 풀어주세요.


# 풀이
---
```jsx
function browserStack(actions, start) {
  if(typeof start !== 'string') {
    return false;
  }
  let prev = []
  let cur = [start]
  let next = []

  for(let i = 0; i<actions.length; i++) {
    if(typeof actions[i] === 'string') {
      prev.push(cur[0])
      cur.pop()
    //  next.pop()
      cur.push(actions[i])
      next=[]
    }
    if(actions[i] === -1 && prev.length !==0) {
      next.push(cur[0])
      cur.pop()
      cur.push(prev[prev.length-1])
      prev.pop()
    }
    if(actions[i] === 1 && next.length !==0) {
      prev.push(cur[0])
      cur.pop()
      cur.push(next[next.length-1])
      next.pop()
    }
  }
  

  return [prev, cur[0], next]
}
```
