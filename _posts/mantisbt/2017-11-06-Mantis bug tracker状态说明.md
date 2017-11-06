---
   layout: default
   title: Mantis Bug Tracker状态流程说明 
   tags: MantisBT
--- 

# {{ page.title }}
{{ page.date | date: "%Y-%m-%d" }}

在Mantis中的问题状态一共有以下几种
```php
10:new,             //新建
20:feedback,        //反馈
30:acknowledged,    //认可
40:confirmed,       //已确认
50:assigned,        //已分派
80:resolved,        //已解决
90:closed           //已关闭
```

问题完成度有以下几种：
```php
10:open,                    //未处理
20:fixed,                   //已修正
30:reopened,                //重新打开
40:unable to reproduce,     //无法重现
50:not fixable,             //无法修复
60:duplicate,               //重复问题
70:no change required,      //不是问题
80:suspended,               //暂停
90:won\'t fix               //不做修改

```

可以在管理里面看到默认流程下的各种状态和完成度，一些基本的应该是这样吧。  
角色有以下几种：
- 报告人
- 修改人
- 测试人
- 审核人


### 流程1
报告-审核-修改-测试-关闭

一个问题来了以后，经过审核人审核，提出修改意见，然后指派给修改人员，修改人员修改完成后指派测试人员，或者由审核人指派测试人员，测试完毕后关闭如果有问题仍然存在，问题状态为`反馈`，完成度为`重新打开`

| 过程    | 问题状态    | 完成度                            |
|-------|---------|--------------------------------|
| 新报告问题 | 新建      | 未修改                            |
| 审核后   | 已确认，已分派 | 未修改                            |
| 修改后   | 已解决     | 已修正，无法重现，重复问题，不是问题，暂停，不修改      |
| 测试后   | 已关闭，反馈  | 已修正，无法重现，重复问题，不是问题，暂停，不修改，重新打开 |


### 流程2
报告-审核-测试-关闭  

当审核认为不需要修改的时候可以直接将问题分派给测试人员，由测试人员测试，如果有问题仍然存在，问题状态为`反馈`，完成度为`重新打开`。

| 过程    | 问题状态    | 完成度                             |
|-------|---------|---------------------------------|
| 新报告问题 | 新建      | 未修改                             |
| 审核后   | 已确认，已分派 | 未修改，无法重现，重复问题，不是问题，暂停，不修改       |
| 测试后   | 已关闭，反馈  | 已修正，无法重现，重复问题，不是问题，暂停，不修改 ，重新打开 |


 ![](/assets/mantisbt/mantisstatus.png)

### 一、New(新建) 状态说明 

1. 测试人员发现bug，填写好bug report后通过“1”submit bug，此时bug的状态为new； 
2. 处于new状态的bug，team leader认为是bug且需要修复的，通过“2”将bug分派给相应的开发人员，此时bug的状态为assigned(分配状态)； 
3. 处于new状态的bug，team leader认为测试人员的bug描述不清或者有疑问，通过“3”将bug反馈给测试人员，并在note里注明原因，此时bug的状态为confirmed（回馈状态）； 
4. 处于new状态的bug，team leader认为需要延后修复、需跟客户确认、不能修复的bug，通过“4”将bug的状态更改为acknowledged（等待状态）。 

### 二、Assigned(已分派) 状态说明： 

5. 处于`assigned`状态的bug，开发人员将其修复后，通过“5”将bug的状态更改为resolved； 
6. 处于`assigned`状态的bug，开发人员认为测试人员的bug描述不清或者有疑问，通过“6”将bug反馈给测试人员，并在note里注明原因，此时bug的状态为`confirmed`；
7. 处于`assigned`状态的bug，开发人员认为需要延后修复、需跟客户确认、不能修复的bug，通过“7”将bug的状态更改为`acknowledged`。 

### 三、Resolved(已解决) 状态说明： 

8. 处于`resolved`状态的bug，测试人员进行回归测试确认bug已经被修复后，通过“8”将bug关闭，此时bug的状态为`closed`；  
9. 处于`resolved`状态的bug，测试人员进行回归测试发现bug没有修复或者由此引发了其他的bug，通过“9”将bug反馈给开发人员，并在note里注明原因，此时bug的状态为`feedback`。 

### 四、Closed(已关闭) 状态说明： 

10. 处于`closed`状态的bug，若测试人员在测试过程中还发现该问题，可以通过“10” 将bug反馈给开发人员，并在note里注明原因，此时bug的状态为`feedback`。 

### 五、Feedback(打回) 状态说明： 

11. 处于`feedback`状态的bug，开发人员将其修复后，通过“11”将bug的状态更改为`resolved`； 
12. 处于`feedback`状态的bug，开发人员认为测试人员的bug描述不清或者有疑问，通过“12”将bug反馈给测试人员，并在note里注明原因，此时bug的状态为`confirmed`； 
13. 处于`feedback状态的bug，team leader或者开发人员认为该bug需要重新分派，通过“13”将bug重新分派给相应的开发人员，此时bug的状态为`assigned`；
14. 处于`feedback`状态的bug，开发人员认为需要延后修复、需要跟客户确认、不能修复的bug，通过“14”将bug的状态更改为`acknowledged`。 

### 六、Confirmed(已确认) 状态说明： 

15. 处于`confirmed`状态的bug，测试人员对于开发人员的疑问作出回应，通过“15”将bug的状态更改为`feedback`，并在note里注明原因； 
16. 处于`confirmed`状态的bug，测试人员认为该bug有争议，需上一级领导确认的，通过“16”将bug的状态更改为`acknowledged`； 
17. 处于`confirmed`状态的bug，测试人员认为该bug不需要修复，通过“17”将bug关闭，此时bug的状态为`closed`。 

### 七、Acknowledged(认可) 状态说明： 

18. 处于`acknowledged`状态的bug，team leader或者测试人员认为该bug必须修复，通过“18”重新将bug分派给相应的开发人员，此时bug的状态为`assigned`； 
19. 处于`acknowledged`状态的bug，team leader或者开发人员发现该bug已经修复了，通过“19” 将bug的状态更改为`resolved`；
20. 处于`acknowledged`状态的bug，测试人员认为该bug不需要修复，通过“20”将bug关闭，此时bug的状态为`closed`