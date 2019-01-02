Say you have an array for which the ith element is the price of a given stock on day i.(给你一个数组prices，数组index代表第index天， prices[index]代表第index天的股价)

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.（如果你只允许最多交易一次【即买卖各一次】，设计一个算法计算最大利润）

Note that you cannot sell a stock before you buy one.（卖出股票前只能买入）

#### 解题
```
class Solution(object):
    def maxProfit(self, prices):
        ## 声明两个变量，记录最大利润max_profit、最小成本min_price
        max_profit, min_price = 0, float('inf')
        for price in prices:
            ## 遍历数组，记录最小成本
            min_price = min(min_price, price)
            ## 计算某天卖出的利润
            profit = price - min_price
            ## 计算记录某天卖出的利润是否最大
            max_profit = max(max_profit, profit)
        return max_profit
```
