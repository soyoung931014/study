> https://velog.io/@longroadhome/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-LV.4-3-x-n-%ED%83%80%EC%9D%BC%EB%A7%81-JS
- 어떻게 접근해야하는지 이해가 잘 안갔었는데 위의 게시글을 읽고 이해할 수 있었다. 
```jsx

function solution (n) {
  const dp = [0, 3, 11]; // 41
  const idx = n >> 1;
  
  if(n % 2) return 0; // 홀수는 날림 (나름의 효율성을 위해)
  if(idx < 3) return dp[idx]; 

  const MOD = 1000000007 
  for(let i = 3; i <= idx; i++) {
    dp[i] = dp[i-1] * 3 + 2;
    
    for(let j = 1; j < i-1; j++) {
      dp[i] += dp[j] * 2;
    }
    
    dp[i] %= MOD;
  }
  
  return dp[idx];
}
```
