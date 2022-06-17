[Coin Change](https://leetcode.com/problems/coin-change/)

### Using Backtracking
Complexity - O(C^N)

C - Coins Array Length;
N - Height of the tree 

``` Java
class Solution {
    //O(coins.length^N)
    int minCoins = Integer.MAX_VALUE;
    public int coinChange(int[] coins, int amount) {
        minCoins = amount+1;
        coinChangeUtil(coins, amount, 0);
        return minCoins>amount+1?-1:minCoins;
    }
    
    public void coinChangeUtil(int[] coins, int amount, int count){
        if(amount==0){
            minCoins = Math.min(minCoins, count);
            return;
        }
        if(amount<0){
            return;
        }
        
        for(int i=0; i<coins.length; i++){
            if(coins[i]<=amount){
                coinChangeUtil(coins, amount-coins[i], count+1);
            }
        }
    }
}

```

### Using Dynamic Programming
TimeComplexity - O(AmountxCoins.length)


``` Java

//O(Amount*Coins.length)
    public int coinChange(int[] coins, int amount) {
        Arrays.sort(coins);
        int[] dp = new int[amount+1];
        Arrays.fill(dp, amount+1);
        dp[0] = 0;
        for(int i=1; i<=amount; i++){
            for(int j=0; j<coins.length; j++){
                if(coins[j]<=i){
                    dp[i] = Math.min(dp[i], 1+dp[i-coins[j]]);    
                }else{
                    break;
                }
            }
        }
        return dp[amount]> amount ? -1:dp[amount];
    }
```
