---
title: 常用扩展
date: 2019-10-18 16:47:56
categories: Laravel
tags: [常用扩展]
---

## 中国省份城市区数据 

 china-area-data 

## 弹出提示框 

 sweetalert 

```js
require('sweetalert');
```

```php
<button class="btn btn-danger btn-del-address" type="button" data-id="{{ $address->id }}">删除</button>

<script>
    $(document).ready(function() {
    // 删除按钮点击事件
    $('.btn-del-address').click(function() {
        // 获取按钮上 data-id 属性的值，也就是地址 ID
        var id = $(this).data('id');
        // 调用 sweetalert
        swal({
            title: "确认要删除该地址？",
            icon: "warning",
            buttons: ['取消', '确定'],
            dangerMode: true,
        })
            .then(function(willDelete) { // 用户点击按钮后会触发这个回调函数
            // 用户点击确定 willDelete 值为 true， 否则为 false
            // 用户点了取消，啥也不做
            if (!willDelete) {
                return;
            }
            // 调用删除接口，用 id 来拼接出请求的 url
            axios.delete('/user_addresses/' + id)
                .then(function () {
                // 请求成功之后重新加载页面
                location.reload();
            })
        });
    });
});
</script>
```

