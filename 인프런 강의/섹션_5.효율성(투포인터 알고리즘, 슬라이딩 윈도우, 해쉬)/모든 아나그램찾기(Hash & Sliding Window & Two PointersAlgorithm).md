## ✅✅
```jsx
<html>
    <head>
        <meta charset="UTF-8">
        <title>출력결과</title>
    </head>
    <body>
        <script>
            function solution(s, t){
                let cnt=0
                let map = new Map()
                for(let el of t){
                    if(!map.has(el)){
                       map.set(el, 1)     
                    }else map.set(el,map.get(el)+1)
                }
                
                for(let i=0; i<s.length-t.length+1; i++){
                    let flag=0
                    let copy = new Map(map)
                    for(let j=i; j<i+t.length; j++){
                        if(copy.has(s[j]) && copy.get(s[j]) !==0) copy.set(s[j],copy.get(s[j])-1)
                        else {
                            flag=1
                            break
                        }
                    }
                    if(!flag) cnt++
                }

                return cnt
            }
            
            let a="bacaAacba";
            let b="abc";
            console.log(solution(a, b));
        </script>
    </body>
</html>
```
