## 문제
---
https://school.programmers.co.kr/learn/courses/30/lessons/12953

## 풀이
----
```jsx
function solution(arr) {
  let answer = 1;
    const gcd = (a,b) => {
        if(b === 0){
            return a;
        }else if(a%b === 0){
            return b;
        }else{
            return gcd(b, a%b);
        };
    };

    const lcm = (a,b) => {
        return (a*b) / gcd(a,b);
    };

  for (let i = 0; i < arr.length; i++) {
    answer = lcm(answer, arr[i]);
  };
      return answer;
  };
```
- 최소 공배수를 구하는 법: 두수의 곱/최대공약수
- 최대공약수 : 유클리드호제법 사용

유클리드호제법을 사용 안하고 풀어보고싶었는데 잘 안됨.. 다음에 다시 도오전
