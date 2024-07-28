## datawhale AI 夏令营 task1笔记
本题市场的主体是各个发电机组，他们在电力现货市场中根据市场信息/其他机组信息进行报价，并**以获得最大利润为目标**。

这里我们用**边际成本定价法**作为baseline，即每个机组都以其自身每生产一度电的成本进行报价，而不考虑市场信息和其他机组信息。

> 类比来说就是只会以成本价卖出商品（事实上这就是完全竞争市场的长期均衡状态）

随后，按报价从低到高排序，依次接受报价，直到累计的功率超过了总需求，市场达到出清状态，并以最后一个满足的报价作为市场出清价格的估计。
### 函数记忆
sort_values("coal consumption (g coal/KWh)")  # 按照一度电的耗煤量（近似为边际成本）降序排序


model = LinearRegression()

X = prices[:train_length]

y = electricity_price["clearing price (CNY/MWh)"].iloc[:train_length].values.reshape(-1, 1)

model.fit(X, y)
