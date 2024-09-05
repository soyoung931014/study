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

다른 풀이
```jsx
function solution(array, commands) {
let result = []
for(let command of commands) {
    console.log(command)
    const [f, s, t] = command
    result = result.concat(
        array.slice(f-1, s).sort((a,b) => a-b).slice(t-1, t)
    )

}
return result
```
### 또풀이
```jsx
function solution(array, commands) {
    let result = [];
    for(let i = 0; i < commands.length; i++){
      let command = commands[i]
      let slice = array.slice(command[0] - 1, command[1])
      result.push(slice.sort((a, b) => a - b)[command[2] - 1])
    }

    return result;
}
```

### 풀이
```jsx
function solution(array, commands) {
    let result = []
    for(let [start,cut,find] of commands){
        let tmp = array.slice(start-1,cut).sort((a,b) => a-b)[find-1]
        result.push(tmp)
    }
    return result
}
```
