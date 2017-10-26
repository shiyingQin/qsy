## weUI 文档
https://github.com/Tencent/weui/wiki


## weUI  DatePicker只选择年月
 

weui同样提供了datapicker的实例，但是某些情况下，只需要年月选择，现提供demo如下：

$('#inputStartWorkingDate').on('click', function() {

var $this = $(this);

var defaults = {

start : 1980,

end : new Date().getFullYear()

};

var date = [];

for (var i = defaults.start; i <= defaults.end; i++) {

var months = [];

for (var j = 0; j < 12; j++) {

months.push({

label : j + 1 + '月',

value : j + 1,

});

}

var year = {

label : i + '年',

value : i,

children : months

};

date.push(year);

}

weui.picker(date, {

defaultValue : [ (new Date().getFullYear()) - 3, 1 ],

onChange : function(result) {

},

onConfirm : function(result) {

$this.val(result[0] + "年" + result[1] + "月");

}

});

});

实现Citypicker
本质上也是一个二级/三级级联选择，主要是数据的准备，结构如下：

[

{

“label”: “青海”,

“value”: “青海”,

“children”: [

{

“label”: “海西州”,

“value”: “235f42bbdbdc40d08fdaf48d9bca6f81”

},

{

“label”: “玉树州”,

“value”: “2f6e4d4ede00415191fc89e68b8054fd”

},

{

“label”: “西宁”,

“value”: “337b6959e4374fcca84adb8034e10c8d”

},

{

“label”: “海北州”,

“value”: “615c6a5aad444933b95730a4675d321c”

},

{

“label”: “果洛州”,

“value”: “9f3028386d9d4f64b17c07ea2215fe91”

},

{

“label”: “海东”,

“value”: “b1b97e9c9a8d4574851edf2192eecc95”

},

{

“label”: “黄南州”,

“value”: “e9f29123030c46a1ae65dc00950957d5”

}

]

},

{

“label”: “北京”,

“value”: “北京”,

“children”: [

{

“label”: “北京”,

“value”: “c99970058adb4526837c802889c73824”

}

]

}

]

由于不是最新的行政区划，就不提供数据了

weui.picker(cityPickerData, {

defaultValue : [ ‘重庆’,

‘e2acff548dd8471193ae777d23c27f49’ ],

onChange : function(result) {

console.log(result);

},

onConfirm : function(result) {

labelObj.val(Calc.findChildrenLabel(result,

cityPickerData));

valueObj.val(result[1]);

}

});
