## Env 运行环境
```
pyenv version
# anaconda2-4.3.1
conda list gurobi
# gurobi                    7.0.2                    py27_0

# tested with
#  Python 2.7.13 :: Anaconda 4.3.1 (x86_64) Gurobi 7.0.2

Jupyter notebooks # 启动 notebook 环境
```

## Files & Folders 模型代码
Source: http://www.gurobi.com/resources/examples/example-models-overview
* notebook
  * `diet.ipynb` 每日食物营养摄入均衡
  * `multiobj.ipynb` 多目标优化 （TODO: 搞清楚具体优化目标。)
  * `food-manufacture-[i|ii].ipynb` 生产熬油(版本i|ii)
  * `factory-planning-[i|ii].ipynb` 工厂生产(版本i|ii)
  * `manpower-planning.ipynb` 工厂人员Staffing问题
  * `mining.ipynb` production 生产问题。 使用多周期生产规划5年挖矿计划。公司拥有不同的矿产，生产的数量不同。目标是创建最优化的生产计划，以最大化收益。
  * `refinery.ipynb` 解决生产规划问题。 公司采购两种原油(crude oil)，可以生产汽油(gasoline)，航空汽油(jet fuel)，或普通油. 目标是创建生产计划以最大化收益。
* InteractiveModelExamples
  * `InteractiveModelExamples.ipynb` 记录交互式代码整体文档
  * `interactive-open-pit-mining.py.ipynb` 通用 project selection 项目选择问题，项目之间存在依赖关系。 对挖矿问题进行求解，不同采矿点存在依赖关系。
  * `interactive-offshore-wind-farming.ipynb` 通用 fixed charge network flow 网络流问题，通信网络或运输网络的规划；解决水下电缆的安置问题；从风车收集电力
  * `interactive-traveling-salesman-problem.ipynb` 经典的TSP组合优化问题
  * `interactive-cell-tower-coverage.ipynb` 用的 covering problem 覆盖问题; 在预算受限的情况下规划蜂窝电话塔的位置以完成最大人群覆盖。
  * `interactive-facility-location.ipynb` 通用 facility location problem 生产问题，包括供应链，物流，运输问题等。 交互式例子为英国通过库房供应超级市场的选址问题。
  * `interactive-production-scheduling.ipynb` 简单的生产规划问题，采用 piecewise-linear 目标函数。TODO: piecewise-linear 函数的作用。
  * `interactive-kidney-exchange.ipynb` 器官移植问题, 在捐助者和病人之间进行配型.
* python
  * `python $xxx$.py` 执行对应的 python 代码, 可获取标准结果
* Mathjax分段函数例子： http://blog.csdn.net/u012302219/article/details/51452649

## 模型描述

Model Name|	Model Description
----------|---------------------
Food Manufacture I|	This model is an example of a blending problem. In blending optimization problems, multiple raw materials are combined in a way the meets the stated constraints for the lowest cost. 生产熬油混合问题
Food Manufacture II|	This model extends the Food Manufacture I example above to include new constraints that change the problem from a fairly easy to solve linear programming model to an mixed integer model that is harder to solve. 熬油问题变更为 MIP模型, 使用 `addGenConstrIndicator` 增加了油品种的使用约束
Factory Planning I|	This model is an example of a production planning problem. In product planning problems the goal is to create an optimal production plan to maximize profit. 工厂生产规划模型
Factory Planning II|	This model extends the Factory Planning I example above to add complexity whereby the month where each machine is down will, instead of being fixed, be determined as a part of the optimized plan. 工厂生产问题将下线机器变更为动态时间版本, 采用 `Vars.sum('*', m)` 汇总统计变量.
Farm Planning |	This model is an example of a multi-period production planning problem. In this case the application is to optimize the operation of a farm over 5 years.
Manpower Planning|	This model is an example of a staffing problem. In staffing planning problems, choices must be made regarding the recruitment, training, redundancy (retention) and scheduling of staff.
Mining  |	This model is an example of a production problem. In production planning problems, choices must be made regarding the what resources to use to produce what products.
Refinery	| This model is an example of a production problem. In production planning problems, choices must be made regarding the what resources to use to produce what products.
