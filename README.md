## 为 layui 扩展的 表格列自动合并[独立模块版]
当前 `layui` 版本为 **2.4.5**

在线demo： [http://yelog.org/layui-table-merge/](http://yelog.org/layui-table-merge/)    
这个在线 demo就是本项目的 `index.html`。 可将项目 `clone` 到本地查看效果。

## 效果图
![效果](http://oncj6b2vl.bkt.clouddn.com/FmMA3nI42bajhMmRF0OFzLZH1KlC.png)

## 参数说明
<table><thead><tr><th>属性名</th><th>属性值</th><th>例子</th><th>描述</th></tr></thead><tbody><tr><td rowspan="3">merge</td><td>boolean</td><td>merge: true</td><td>开启合并，并根据 当前列 相同值 自动合并</td></tr><tr><td>string</td><td>merge: 'name'</td><td>开启合并，并根据 指定列 相同值 自动合并</td></tr><tr><td>array</td><td>merge: ['name', 'type']</td><td>开启合并，并先根据 name值 分组后，再以 type值 相同的合并对应行<br>注：数组无数量限制</td></tr></tbody></table>

## 引入
引入 tableMerge 模块即可
```js
// 自定义模块
layui.config({
    base: 'module/'
}).extend({
    tableMerge: 'tableMerge'
});
```


## 使用实例
```js
table.render({
    elem: '#mergeTable'
    ,height: 550
    ,url: 'data.json'
    ,limit: 30
    ,page: true
    ,cols: [[
        {type: 'checkbox', fixed: 'left'}
        ,{field:'poetry', title:'诗词', width:188, fixed: 'left'}
        ,{field:'name', merge: true, title:'诗人', width:100, fixed: 'left'}              // 根据 当前列 相同值 的自动合并
        ,{field:'type', merge: ['name','type'], title:'类型', width:100, fixed: 'left'}   // 根据 name 分组后，再以 type值 相同的合并对应行
        ,{field:'type', merge: true, title:'类型', width:100}                             // 根据 当前列 相同值 的自动合并
        ,{field:'dynasty', title:'朝代', merge: ['name', 'type'], width:150}              // 根据 name 分组后，再以 type值 相同的自动合并
        ,{field:'dynasty', title:'朝代', merge: 'name', width:150}                        // 根据 name值 相同的自动合并
        ,{field:'dynasty', title:'朝代', merge: true, width:150}                          // 根据 当前列 相同值 的自动合并
        ,{field:'sentences', title:'名句', width:400}
        ,{field:'sentences', title:'名句', width:400}
        ,{field:'sentences', title:'名句', width:400}
        ,{fixed: 'right', title:'操作', toolbar: '#barDemo', width:150}
    ]]
    ,done: function () {
        tableMerge.render(this)
    }
});
```

> 更多内容参考实例或代码。
