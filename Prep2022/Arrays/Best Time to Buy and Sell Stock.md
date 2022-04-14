# PROBLEM

[Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

# SOLUTION

```
 // O(N)|O(1)
    public int maxProfit(int[] prices) {
        int lowest_buy_so_far = Integer.MAX_VALUE;
        int overall_profit = 0;
        int profit_if_sold_today = 0;
        
        for(int price: prices){
            if(price<lowest_buy_so_far){
                lowest_buy_so_far = price;
            }
            profit_if_sold_today = price - lowest_buy_so_far;
            if(overall_profit<profit_if_sold_today){
                overall_profit = profit_if_sold_today;
            }
        }
        return overall_profit;
    }
 ```

