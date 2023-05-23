> https://velog.io/@longroadhome/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-LV.4-3-x-n-%ED%83%80%EC%9D%BC%EB%A7%81-JS
- 어떻게 접근해야하는지 이해가 잘 안갔었는데 위의 게시글을 읽고 이해할 수 있었다. 
```jsx
const MOD = 1000000007;

function solution (n) {
    if(n % 2) return 0; // 홀수는 날림  
    const dp = [0, 3, 11]; // 41
    const idx = n >> 1; // 시프트 연산자
  
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

-------
다시 풀어봄. 

이번 문제는 직사각형이고 세로의 길이가 3이기 때문에 n이 홀수인 경우에는 가로 2 세로1의 타일은 들어가지 않습니다. 따라서 홀수인 경우 🇵✅ 와 같이 처리해줍니다.
짝수인 경우만 생각해주면되는데, 기본적으로 n=2일때 3가지 스타일이 나오게 됩니다. 만약 n=4일경우로 생각해보면, n=2일때의 스타일 X n=2일때의 스타일(3가지)가 붙는것이기 떄문에 이를 점화식으로 표현하면 dp[i] = 3dp[i-2]로 처리해 줄 수 있습니다. 그러나 문제의 예시를 보면 n=4일경우는 2개의 경우의 수가 더 생기게 되는걸 볼 수 있습니다. n=6일경우도 2가지가 추가될것임을 알수 있습니다.
즉 우리가 만들어준 식에 +2dp[i-4]의 경우의 수를 추가해주면  정답이 나옵니다. 
어제 이문제를 한참을 봐도 규칙을 잘 못찾았었습니다. 
결국 https://www.youtube.com/watch?v=kYoKLm8BZtI&t=803s 이걸 보고 흐름으르 알 수 있게되었습니다. 
function solution (n) {
   let m = 1000000007
   if(n%2) return 0 🇵✅
   let dp=[]
   dp[0]=1
   dp[2]=3
  
    for(let i=4; i<=n; i+=2){
        dp[i] = 3*dp[i-2] 
        for(let j=i; j>=4; j-=2){
            dp[i] +=  2*dp[j-4]      
        }
     dp[i] = dp[i]%m
    }
    return dp[n]
}
