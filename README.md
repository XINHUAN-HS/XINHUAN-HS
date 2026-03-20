<div>
<canvas style="/* 通用选择器：重置所有元素的默认外边距和内边距 */
* {
    margin: 0;
    padding: 0;
}

/* 设置整个页面的背景颜色为黑色 */
body {
    background: black;
}

/* 设置所有canvas元素以块级元素显示，通常用于全屏或独立画布 */
canvas {
    display: block;
}

/* 为ID为color的元素（可能是一个文本信息或控制面板）设置样式 */
#color {
    /* 字体颜色 */
    color: #BBB;
    /* 字体族，设置备用字体 */
    font-family: helvetica, arial, sans-serif;
    /* 字体大小 */
    font-size: 1.2em;
    /* 定位方式为绝对定位，并固定在右下角 */
    position: absolute;
    bottom: 0;
    right: 0;
    /* 设置一个较高的堆叠顺序，确保显示在最上层 */
    z-index: 1000;
}"></canvas>
<script>
    // 配置文件根对象，存储动画的各种参数
var root = {
  wavecolor: {  // 固定颜色模式下的RGB值
    r: 125,
    g: 52,
    b: 253
  },
  rainbowSpeed: 0.5, // 彩虹颜色变化速度系数
  rainbow: true,      // 是否启用彩虹颜色效果
  matrixspeed: 50     // 动画绘制间隔（毫秒）
};

// 获取Canvas元素及其2D绘制上下文
var c = document.getElementById("c");
var ctx = c.getContext("2d");

// 彩虹效果相关变量
var hueFw = false; // 色调变化方向控制
var hue = -0.01;   // 当前色调值（初始值）

// 设置Canvas尺寸为全屏
c.height = window.innerHeight;
c.width = window.innerWidth;

// 定义雨滴中显示的字符（这里只使用了0和1）
var konkani = "01";
// 将字符串分割为字符数组
var characters = konkani.split("");

var font_size = 14; // 字体大小
var columns = c.width / font_size; // 根据画布宽度计算列数

// 创建线性渐变（虽然定义了但后续未使用）
var gradient = ctx.createLinearGradient(0, 10, 0, 200);

// 雨滴位置数组：每列对应一个雨滴，存储其Y坐标（行数）
var drops = [];

// 初始化雨滴数组：每列从第1行开始
for (var x = 0; x < columns; x++) {
  drops[x] = 1;
}

// 核心绘制函数
function draw() {
  // 1. 绘制半透明黑色背景，产生拖尾效果
  ctx.fillStyle = "rgba(0,0,0, 0.05)";
  ctx.fillRect(0, 0, c.width, c.height);

  // 2. 设置默认字体样式
  ctx.fillStyle = "#BBB"; // 灰色文本
  ctx.font = font_size + "px arial";

  // 3. 遍历所有列（雨滴）
  for (var i = 0; i < drops.length; i++) {
    // 3.1 在字符位置绘制一个深色背景矩形（形成"块"状效果）
    ctx.fillStyle = "rgba(10,10,10, 1)";
    ctx.fillRect(i * font_size, drops[i] * font_size, font_size, font_size);

    // 3.2 随机选择一个字符（0或1）
    var text = characters[Math.floor(Math.random() * characters.length)];

    // 3.3 设置字符颜色
    if (root.rainbow) {
      // 彩虹模式：动态计算RGB值
      hue += hueFw ? 0.01 : -0.01; // 更新色调值
      // 使用正弦函数生成周期性变化的RGB值
      var rr = Math.floor(127 * Math.sin(root.rainbowSpeed * hue + 0) + 128);
      var rg = Math.floor(127 * Math.sin(root.rainbowSpeed * hue + 2) + 128);
      var rb = Math.floor(127 * Math.sin(root.rainbowSpeed * hue + 4) + 128);
      ctx.fillStyle = 'rgba(' + rr + ',' + rg + ',' + rb + ')';
    } else {
      // 固定颜色模式：使用root.wavecolor中的RGB值
      ctx.fillStyle = 'rgba(' + root.wavecolor.r + ',' + root.wavecolor.g + ',' + root.wavecolor.b + ')';
    }

    // 3.4 绘制字符
    ctx.fillText(text, i * font_size, drops[i] * font_size);

    // 3.5 雨滴下落：Y坐标增加1（行数+1）
    drops[i]++;

    // 3.6 重置条件：当雨滴超出画布底部且随机概率大于0.975时，将其重置到顶部
    if (drops[i] * font_size > c.height && Math.random() > 0.975) {
      drops[i] = 0;
    }
  }
}

// 窗口大小改变时重新加载页面（重置Canvas和动画）
window.onresize = () => {
  location.reload();
};

// 设置定时器，按照指定间隔重复执行draw函数
setInterval(draw, root.matrixspeed);

// 属性监听函数：接收外部传递的属性更改（可能来自GUI控制面板）
function livelyPropertyListener(name, val) {
  switch (name) {
    case "matrixColor": // 矩阵颜色更改
      root.wavecolor = hexToRgb(val); // 将十六进制颜色转换为RGB对象
      break;
    case "rainBow": // 彩虹效果开关
      root.rainbow = val;
      break;
    case "rainbowSpeed": // 彩虹速度更改（转换0-100到小数）
      root.rainbowSpeed = val / 100;
      break;
  }
}

// 工具函数：将十六进制颜色字符串转换为RGB对象
function hexToRgb(hex) {
  // 正则表达式匹配 #RRGGBB 格式
  var result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
  return result ? { // 如果匹配成功，返回包含r,g,b属性的对象
    r: parseInt(result[1], 16), // 红色分量
    g: parseInt(result[2], 16), // 绿色分量
    b: parseInt(result[3], 16)  // 蓝色分量
  } : null; // 匹配失败返回null
}
</script>
</div>