### 图片裁剪插件说明文档

#### 1.功能

实现将所传图片裁剪为自定义尺寸，并返回为Base64格式。

#### 2.调用方式

##### 2.1 模块化调用

a. 引入jQuery

``` html
<script src="//static.soufunimg.com/common_m/pc_public/fangjs/build/??fang2.3.2.js,jquery/jquery-3.js"></script>
```
注： 该引用已集成jQuery和前端框架fang.js 。

b. 配置基本路径信息

``` javascript
fang.config({
    base:'//static.soufunimg.com/common_m/pc_public/imgcropping/js'
});
```
注： 详细的配置信息，请参考: [http://activities.m.test.fang.com/fangfis-doc#/api?id=fangconfigoptions](http://activities.m.test.fang.com/fangfis-doc#/api?id=fangconfigoptions)。

c. 调用

``` javascript
var config = {
    // 裁剪框可见宽度
    cropWidth: 200,
    // 裁剪框可见高度
    cropHeight: 300,
    // 最终输出图片宽高与裁剪框宽高的比率，如本例中值为3，则输出图片尺寸为600*900
    // 若此值为空或不传，则比率默认为设备像素比的值（DPR）
    ratio: 3
    // 图片上传input标签的id值，切图type必须为file
    fileId: '#file',
    // 回调函数，返回值为Base64格式
    callback: function(base64) {
        $('#previewResult').attr('src', base64).show();
    }
};
fang.use('tailoring', function(Tailoring) {
    new Tailoring(config);
});
```

##### 2.2 非模块化调用

a. 引入jQuery
``` html
<script src="//static.soufunimg.com/common_m/pc_public/fangjs/build/jquery/jquery-3.js"></script>
```

b. 引入插件
``` html
<script src="//static.soufunimg.com/common_m/pc_public/imgcropping/js/tailoring.js"></script>
```

c. 调用

``` javascript
var config = {
    // 裁剪框可见宽度
    cropWidth: 200,
    // 裁剪框可见高度
    cropHeight: 300,
    // 最终输出图片宽高与裁剪框宽高的比率，如本例中值为3，则输出图片尺寸为600*900
    // 若此值为空或不传，则比率默认为设备像素比的值（DPR）
    ratio: 3
    // 图片上传input标签的id值，切图type必须为file
    fileId: '#file',
    // 回调函数，返回值为Base64格式
    callback: function(base64) {
        $('#previewResult').attr('src', base64).show();
    }
};
new Tailoring(config);
```

#### 3. 参数

3.1 参数示例
``` javascript
var config = {
    // 裁剪框可见宽度
    cropWidth: 200,
    // 裁剪框可见高度
    cropHeight: 300,
    // 最终输出图片宽高与裁剪框宽高的比率，如本例中值为3，则输出图片尺寸为600*900
    // 若此值为空或不传，则比率默认为设备像素比的值（DPR）
    ratio: 3
    // 图片上传input标签的id值，切图type必须为file
    fileId: '#file',
    // 回调函数，返回值为Base64格式
    callback: function(base64) {
        $('#previewResult').attr('src', base64).show();
    }
};
```

3.2 参数解释
- ####  cropWidth
    裁剪框在设备的可见宽度，非裁剪完成后的实际宽度，实际宽度需要结合ratio计算得出。
- ####  cropHeight
    裁剪框在设备的可见高度，非裁剪完成后的实际高度，实际高度需要结合ratio计算得出。
- #### ratio
    最终输出图片宽高与裁剪框宽高的比率，裁剪完成后的实际宽高为裁剪框可见宽高的ratio倍，如例中ratio值为3，裁剪框可见宽高分别为200和300，则输出图片尺寸为600*900；若此值为空或不传，则比率默认为设备像素比的值（DPR）。
- #### fileId
    图片上传input标签的id值，切图中必须type="file"  accept="image/*"。
- #### callback
    回调函数，返回值为Base64格式。
