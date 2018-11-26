# 组件使用说明


## 表格

-------------------

### SimpleTable
 

**简要描述：** 

简单表格,不带分页

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|header |是  |Array |表头   |
|data |是  |Array | 数据    |


**表头header数据类型：** 

|属性|必选|类型|说明|
|:----    |:---|:----- |-----   |
|key |是  |string |后台返回的数据名称   |
|value |是  |string | 显示的表头中文    |
|format |否  |function | 传入 row,allData，函数应返回dom或字符串   |


**事件：** 

无


**示例：**
```text
header:[
        {
          key:'num',
          value:'数量'
        },
        {
          key:'money',
          value:'单价'
        },
        {
          key:'sum',
          value:'价钱（单位）',
          format(row,allData){
            return row.num*row.money+"元"
          }
        }
      ],
      value:[
        {
          money:1,
          num:2
        }
      ]

``` 

--------------------------------

### DataTable

**简要描述：**
 
数据表格，带增删查改

**参数：** 
|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |

--------------------------------

### SearchBar

**简要描述：**
 
搜索栏


**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|v-model |是  |Object | 搜索值,双向绑定数据   |
|title |是  |string | 标题    |
|tableHeader |是  |Array | 表头    |


**表头tableHeader数据类型：** 

搜索条的表头与DataTable的表头一样

|属性|必选|类型|说明|
|:----    |:---|:----- |-----   |
|key |是  |string |后台返回的数据名称   |
|title |是  |string | 显示的表头中文    |
|searchable |是  |boolean | 是否可搜索 设置成true即可    |
|searchType |否  |string | 支持'date','select'   |
|selectList |否  |Array<{text:string,value:string}> | select的时候有效 |



--------------------------------


## 卡片

### DataPanel

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|number |是  |number | 值   |
|title |是  |Array | 标题    |
|percent |是  |string | 百分比    |
|type |是  |string:up/down | 类型上升或下降    |
