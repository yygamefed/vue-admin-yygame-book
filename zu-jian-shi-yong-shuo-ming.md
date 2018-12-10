# 组件使用说明

框架基于iview基础上，进一步对组件进行定制，各个定制的组件存放在@/src/common文件夹内  
插槽方式使用：即无需在js里写html代码，直接在template完成当前的操作

## 表格

---
- 普通表格-SimpleTable
- 数据表格 DataTable


---


---

### SearchBar

**简要描述：**

搜索栏

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| v-model | 是 | Object | 搜索值,双向绑定数据 |
| title | 是 | string | 标题 |
| tableHeader | 是 | Array | 表头 |

**表头tableHeader数据类型：**

搜索条的表头与DataTable的表头一样

| 属性 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| key | 是 | string | 后台返回的数据名称 |
| title | 是 | string | 显示的表头中文 |
| searchable | 是 | boolean | 是否可搜索 设置成true即可 |
| searchType | 否 | string | 支持'date','select' |
| selectList | 否 | Array&lt;{text:string,value:string}&gt; | select的时候有效 |

---

## 卡片

### DataPanel

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| number | 是 | number | 值 |
| title | 是 | Array | 标题 |
| percent | 是 | string | 百分比 |
| type | 是 | string:up/down | 类型上升或下降 |



