## SimpleTable

**简要描述：**

简单表格,仅做数据展示，不带分页，可插槽式使用

![](/assets/simple-tale.png)

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| header | 是 | Array | 表头 |
| data | 是 | Array | 数据 |

**表头header数据类型：**

| 属性 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| key | 是 | string | 后台返回的数据名称 |
| value | 是 | string | 显示的表头中文 |
| format | 否 | function | 传入 row,allData，函数应返回dom或字符串 |

**插槽式使用**
在配置好header后，无需配置format，在组件内添加 slot="需要设置格式的key",slot-scope="row"

```text    
<template>
<SimpleTable
            :header="header"
            :data="tableData">
            <!-************↓ 配置列模板 返回每行的数据值在row内返回*************** ->
            <template slot="iver" slot-scope="row">
              <a @click="goIverDetail(row.iver)">{{row.iver}}</a>
            </template>
</SimpleTable>
</template>
<script>
export default {
  data: function () {
    return {
      header: [
        {
          key: 'iver',
          name: '版本号'
        }
      ]
    }
  },
  methods:{
    goIverDetail:function(text){
        alert(text)
    }
  }
  mounted: function () {
    // 在这里添加你的数据
    this.tableData = [
      {
        iver: "demo"
      }
    ]
  }
}
</script>
```

**事件：**

无

**配置示例：**

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

