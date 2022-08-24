# 문제
https://school.programmers.co.kr/learn/courses/30/lessons/42748

# 풀이
```jsx
function solution(array, commands) {
    
    let result =[]
    for(let i =0; i<commands.length; i++) {
       const [first, second, third] = commands[i]
       let newArray = array.slice(first-1, second)
        newArray = newArray.sort((a,b) => a-b )
       result.push(newArray[third-1])
    }
return result
```

