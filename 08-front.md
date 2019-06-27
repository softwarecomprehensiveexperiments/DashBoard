文章目录</h3><ul><li><a href="#_2" rel="nofollow" target="_self">前端开发规范文档</a></li><ul><li><a href="#WXML__4" rel="nofollow" target="_self">一、WXML 规范</a></li><ul><li><a href="#1__6" rel="nofollow" target="_self">1. 属性顺序(不必要的情况下)</a></li><li><a href="#2_id__class__16" rel="nofollow" target="_self">2. `id` / `class` 命名规则</a></li><li><a href="#3_WXML__24" rel="nofollow" target="_self">3. WXML 注释规范</a></li></ul><li><a href="#CSS__39" rel="nofollow" target="_self">二、`CSS` 规范</a></li><ul><li><a href="#_41" rel="nofollow" target="_self">属性顺序</a></li><li><a href="#_84" rel="nofollow" target="_self">选择器</a></li><li><a href="#_88" rel="nofollow" target="_self">属性使用缩写</a></li><li><a href="#_0_93" rel="nofollow" target="_self">去掉小数点前面的 0</a></li></ul><li><a href="#_JS__97" rel="nofollow" target="_self">三、 `JS` 规范</a></li><ul><li><a href="#1__99" rel="nofollow" target="_self">1. 语言规范</a></li><li><a href="#2__113" rel="nofollow" target="_self">2. 使用分号</a></li><li><a href="#3__117" rel="nofollow" target="_self">3. 块内函数声明</a></li><li><a href="#4__135" rel="nofollow" target="_self">4. 关于循环</a></li><ul><li><a href="#41_forEach_137" rel="nofollow" target="_self">4.1 `forEach`</a></li><li><a href="#42_map_195" rel="nofollow" target="_self">4.2 `map`</a></li><li><a href="#43_forin_215" rel="nofollow" target="_self">4.3 `for-in`</a></li><li><a href="#44_forof_253" rel="nofollow" target="_self">4.4 `for-of`</a></li></ul><li><a href="#5__359" rel="nofollow" target="_self">5. 命名规范</a></li><li><a href="#6__378" rel="nofollow" target="_self">6. 声明</a></li><li><a href="#7__383" rel="nofollow" target="_self">7. 回调函数规范</a></li><li><a href="#8__421" rel="nofollow" target="_self">8. 数据绑定变量定义规范</a></li><li><a href="#9__426" rel="nofollow" target="_self">9. 函数默认值</a></li></ul><li><a href="#_436" rel="nofollow" target="_self">三、组件规范</a></li><ul><li><a href="#1__438" rel="nofollow" target="_self">1. 组件名命名规范</a></li><li><a href="#2__443" rel="nofollow" target="_self">2. 触发事件规范</a></li><li><a href="#3_externalClasses__451" rel="nofollow" target="_self">3. externalClasses 命名规范</a></li><li><a href="#4__455" rel="nofollow" target="_self">4. 组件样式规范</a></li></ul><li><a href="#_459" rel="nofollow" target="_self">四、标点规范</a></li><li><a href="#_464" rel="nofollow" target="_self">五、注释规范</a></li></ul></ul></div><p></p>
<h1><a name="t1"></a><a id="_2" target="_blank"></a>前端开发规范文档</h1>
<h2><a name="t2"></a><a id="WXML__4" target="_blank"></a>一、WXML 规范</h2>
<h3><a name="t3"></a><a id="1__6" target="_blank"></a>1. 属性顺序(不必要的情况下)</h3>
<ul>
<li><code>class</code> ( <code>class</code> 是为高可复用组件设计的,所以应处在第一位)</li>
<li><code>id</code> <code>name</code> (<code>id</code> 更加具体且应该尽量少使用,所以将它放在第二位)</li>
<li><code>data-\*</code></li>
<li><code>src</code> <code>for</code> <code>type</code> <code>href</code> <code>value</code></li>
<li><code>placeholder</code> <code>title</code> <code>alt</code></li>
<li><code>aria-\*</code> <code>role</code></li>
<li><code>required</code> <code>readonly</code> <code>disabled</code></li>
</ul>
<h3><a name="t4"></a><a id="2_id__class__16" target="_blank"></a>2. <code>id</code> / <code>class</code> 命名规则</h3>
<ul>
<li>首先根据内容命名,如 <code>header</code> <code>footer</code></li>
<li>若根据内容无法找到合适的命名,再结合行为表现进行辅助, e.g. <code>col-main</code> <code>blue-box</code></li>
<li>名字一律小写,多个单词用 - 连接,不能使用下划线和 <code>camel</code><sup class="footnote-ref"><a href="#fn1" rel="nofollow" id="fnref1" target="_self">1</a></sup> 命名法, e.g. <code>main-title</code> 可基于最近的父元素名称作为前缀</li>
<li>在不影响语义的情况下,可适当使用缩写,但是缩写只用来表示结构, e.g. <code>col</code> <code>nav</code> <code>btn</code> etc. , 别给我自编.</li>
<li>避免广告拦截词汇 e.g. <code>ad</code> <code>ads</code> <code>adv</code> <code>banner</code> <code>sponsor</code> <code>gg</code> <code>guangg</code> <code>guanggao</code> etc.</li>
</ul>
<h3><a name="t5"></a><a id="3_WXML__24" target="_blank"></a>3. WXML 注释规范</h3>
<pre class="prettyprint"><code class="prism language-html has-numbering" onclick="mdcp.copyCode(event)"><span class="token comment">&lt;!-- 头部 --&gt;</span>
<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>view</span> <span class="token attr-name">class</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>header<span class="token punctuation">"</span></span><span class="token punctuation">&gt;</span></span>
  <span class="token comment">&lt;!-- LOGO --&gt;</span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>image</span> <span class="token attr-name">class</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>logo<span class="token punctuation">"</span></span><span class="token punctuation">&gt;</span></span><span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>image</span><span class="token punctuation">&gt;</span></span>
  <span class="token comment">&lt;!-- /LOGO --&gt;</span>
  <span class="token comment">&lt;!-- 详情 --&gt;</span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>view</span> <span class="token attr-name">class</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>detail<span class="token punctuation">"</span></span><span class="token punctuation">&gt;</span></span> <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>view</span><span class="token punctuation">&gt;</span></span>
  <span class="token comment">&lt;!-- /详情 --&gt;</span>
<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>view</span><span class="token punctuation">&gt;</span></span>
<span class="token comment">&lt;!-- /头部 --&gt;</span>

<h2><a name="t6"></a><a id="CSS__39" target="_blank"></a>二、<code>CSS</code> 规范</h2>
<h3><a name="t7"></a><a id="_41" target="_blank"></a>属性顺序</h3>
<ul>
<li>位置属性 ( <code>position</code> <code>top</code> <code>right</code> <code>z-index</code> <code>display</code> <code>float</code> etc.)</li>
<li>大小 ( <code>width</code> <code>height</code> <code>padding</code> <code>margin</code> etc.)</li>
<li>文字系列 ( <code>font</code> <code>line-height</code> <code>letter-spacing</code> <code>color</code> <code>text-align</code> ect.)</li>
<li>背景 ( <code>background</code> <code>border</code> etc.)</li>
<li>其他 ( <code>animation</code> <code>transition</code> etc.)</li>
<li>以及注释的写法</li>
</ul>
<pre class="prettyprint"><code class="prism language-CSS has-numbering" onclick="mdcp.copyCode(event)">    /* Button */
    button {
    /* Positioning */
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100;
    /* Box-model */
    display: block;
    float: right;
    width: 100px;
    height: 100px;
    /* Typography */
    font: normal 13px "Helvetica Neue", sans-serif;
    line-height: 1.5;
    color: #333;
    text-align: center;
    /* Visual */
    background-color: #f5f5f5;
    border: 1px solid #e5e5e5;
    border-radius: 3px;
    /* Misc */
    opacity: 1;
    }
    /* End Button */

<h3><a name="t8"></a><a id="_84" target="_blank"></a>选择器</h3>
<ul>
<li>尽量不用选择器。</li>
</ul>
<h3><a name="t9"></a><a id="_88" target="_blank"></a>属性使用缩写</h3>
<ul>
<li>尽量使用简写 e.g. <code>padding</code> <code>margin</code> <code>font</code> <code>background</code> <code>border</code> <code>border-radius</code> etc.</li>
<li>颜色代码尽量也简写 e.g. 白色 <code>#fff</code></li>
</ul>
<h3><a name="t10"></a><a id="_0_93" target="_blank"></a>去掉小数点前面的 0</h3>
<ul>
<li>0.8 =&gt; .8</li>
</ul>
<h2><a name="t11"></a><a id="_JS__97" target="_blank"></a>三、 <code>JS</code> 规范</h2>
<h3><a name="t12"></a><a id="1__99" target="_blank"></a>1. 语言规范</h3>
<ul>
<li>声明变量必须加上 <code>let</code> 关键字.不要再使用 <code>var</code></li>
<li>优先使用箭头函数</li>
<li>使用模板字符串取代连接字符串</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    // worst
    let url = "pages/index/index?id=" + id + "&amp;title=321GO"
    //best
    let url = `pages/index/index?id=${id}&amp;title=321GO`

<h3><a name="t13"></a><a id="2__113" target="_blank"></a>2. 使用分号</h3>
<ul>
<li>如果仅依靠语句间的隐式分隔,有时会很麻烦,使用分号更能清楚哪里是语句的起止,而且有些情况下,漏掉分号会出 <strong>BUG</strong></li>
</ul>
<h3><a name="t14"></a><a id="3__117" target="_blank"></a>3. 块内函数声明</h3>
<ul>
<li>不要在块内声明一个函数,e.g.</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    if (x) {
        function zxm() {}
    }

<ul>
<li>如果确实需要,使用函数表达式来初始化变量</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    if (x) {
        let foo = function() {}
    }

<h3><a name="t15"></a><a id="4__135" target="_blank"></a>4. 关于循环</h3>
<h4><a id="41_forEach_137" target="_blank"></a>4.1 <code>forEach</code></h4>
<ul>
<li><code>forEach</code> 是用来循环数组的</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    let zxmArray = [3,2,1,"GO"];
    Array.prototype.sex = "男";
    Array.prototype.address = function () {
        let tempArr = this;
        tempArr.push("Xtep")
        return tempArr
    };
    //correct
    zxmArray.forEach(function (value, index) {
        console.log(value);//3 2 1 GO
    });
    //correct
    for (var i = 0; i &lt; zxmArray.length; i++) {
        console.log(zxmArray[i]);//3 2 1 GO
    }
    //correct
    let zxmMap = new Map();
    zxmMap.set("a", 3);
    zxmMap.set("b", 2);
    zxmMap.set("c", 1);
    zxmMap.set({
        d: "address"
    }, "GO");
    zxmMap.forEach(function (value, key, mapObj) {
        console.log(value);
        console.log(key)
        console.log(mapObj)
    });
    //Not recommended
    for (var i in zxmArray) {
        console.log(zxmArray[i]);//3 2 1 GO 男 f(){}
    }


<ul>
<li><code>forEach</code> 不支持 <code>break</code> <code>continue</code></li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    let zxmArray = [3,2,1,"GO"];
    zxmArray.forEach(function(value) {
        console.log(value);
            // 不能使用break
            break;
            //不能使用continue
            continue;
    });

<ul>
<li><code>forEach</code> 过程中 <code>arr.push()</code> <code>arr.pop()</code> <code>arr.shift()</code> <code>arr.unshift()</code> <code>arr.reverse()</code> <code>arr.sort()</code> <code>arr.concat()</code> 都可以使用,但是<code>arr.push()</code> 不会改变输出顺序.</li>
</ul>
<h4><a id="42_map_195" target="_blank"></a>4.2 <code>map</code></h4>
<ul>
<li><code>map()</code> 方法返回一个由原数组中的每个元素调用一个指定方法后的返回值组成的新数组</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    let zxmArray = [3,2,1,"GO"];
    let tempArr = zxmArray.map((value,index)=&gt;{
        console.log(value, index);
        return "zxm" + value
    })
    console.log(tempArr)​​​​​// [ 'zxm3', 'zxm2', 'zxm1', 'zxmGO' ]​​​​​
    function add(num) {
        return num + 10
    }
    let zxmAdd = [3,2,1];
    let tempAdd = zxmAdd.map(add);
    console.log(tempAdd)//​​​​ ​[ 13, 12, 11 ]​​​​​

<h4><a id="43_forin_215" target="_blank"></a>4.3 <code>for-in</code></h4>
<ul>
<li><code>for-in</code> 循环实际是为循环 <code>enumerable</code><sup class="footnote-ref"><a href="#fn2" rel="nofollow" id="fnref2" target="_self">2</a></sup> 对象而设计的</li>
<li><code>configurable</code><sup class="footnote-ref"><a href="#fn3" rel="nofollow" id="fnref3" target="_self">3</a></sup> <code>writable</code><sup class="footnote-ref"><a href="#fn4" rel="nofollow" id="fnref4" target="_self">4</a></sup> <code>enumerable</code><sup class="footnote-ref"><a href="#fn5" rel="nofollow" id="fnref5" target="_self">5</a></sup> <code>value</code><sup class="footnote-ref"><a href="#fn6" rel="nofollow" id="fnref6" target="_self">6</a></sup></li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    let zxmObj = {
        a: 3,
        b: 2,
        c: 1,
        d: "GO"
    };
    Object.defineProperty(zxmObj, 'address', {
        configurable: false,
        writable: true,
        enumerable: true,
        value: 'Xtep'
    })
    Object.defineProperties(zxmObj, {
        sex: {
            value: '男',
            enumerable: false
        },
        age: {
            value: 23,
            enumerable: false
        }
    })
    for (var prop in zxmObj) {
        console.log("zxmObj." + prop + " = " + zxmObj[prop]);//​​​​​zxmObj.a = 3 ​​​​​zxmObj.b = 2​​​​​ zxmObj.c = 1​​​​​ ​​​​​zxmObj.d = GO zxmObj.address = Xtep
    }

<ul>
<li><code>for–in</code> 是用来循环带有字符串 key 的对象的方法</li>
</ul>
<h4><a id="44_forof_253" target="_blank"></a>4.4 <code>for-of</code></h4>
<blockquote>
<p>墙裂推荐使用 <code>for-of</code> 既比传统的 for 循环简洁,同时弥补了 <code>forEach</code> 和 <code>for-in</code> 循环的缺点</p>
</blockquote>
<ul>
<li><code>for-of</code> 循环数组</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    let zxmArray = [3,2,1,"GO"];
    for (var value of zxmArray) {
        console.log(value);// 3 2 1 GO
    }

<ul>
<li><code>for-of</code> 循环字符串</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    let zxmString = "321GO";
    for (let value of zxmString) {
        console.log(value);// 3 2 1 G O
    }

<ul>
<li><code>for-of</code> 循环类型化的数组</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    let zxmArray = new Uint8Array([0x00, 0xff]);
    for (let value of zxmArray) {
    console.log(value);// 0 255
    }

<ul>
<li><code>for-of</code> 循环 <code>Map</code></li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    let zxmMap = new Map();
    zxmMap.set("a", 3);
    zxmMap.set("b", 2);
    zxmMap.set("c", 1);
    zxmMap.set({
        d: "address"
    }, "GO");
    for (let [key, value] of zxmMap) {
        console.log(value);// 1 2 3 GO
    }
    for (let entry of zxmMap) {
        console.log(entry);// ["a", 1] ["b", 2] ["c", 1] [{d:"address"}, "GO"]
    }

<ul>
<li><code>for-of</code> 循环 <code>set</code></li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    let zxmSet = new Set([1, 1, 2, 2, 3, 3]);
    for (let value of zxmSet) {
        console.log(value);
    }

<ul>
<li><code>for-of</code> 循环拥有 <code>enumerable</code> 属性的对象,但是并不能直接使用在普通的对象上,如果我们按对象所拥有的属性进行循环,可使用内置的 <code>Object.keys()</code><sup class="footnote-ref"><a href="#fn7" rel="nofollow" id="fnref7" target="_self">7</a></sup> 方法</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    let zxmObj = {
        a: 3,
        b: 2,
        c: 1,
        d: "GO"
    };
    Object.defineProperty(zxmObj, 'address', {
        configurable: false,
        writable: true,
        enumerable: true,
        value: 'Xtep'
    })
    for (var prop of Object.keys(zxmObj)) {
        console.log("zxmObj." + prop + " = " + zxmObj[prop]);//​​​​​zxmObj.a = 3 ​​​​​zxmObj.b = 2​​​​​ zxmObj.c = 1​​​​​ ​​​​​zxmObj.d = GO zxmObj.address = Xtep
    }


<ul>
<li><code>for-of</code> 循环生成器 ( generators ) 然鹅微信小程序并不支持 <code>async</code> <code>await</code> 也不支持</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    function* fibonacci() { // a generator function
    let [prev, curr] = [0, 1];
    while (true) {
        [prev, curr] = [curr, prev + curr];
        yield curr;
    }
    }
    for (let n of fibonacci()) {
    console.log(n);
    // truncate the sequence at 1000
    if (n &gt;= 1000) {
        break;
    }
    }

<h3><a name="t16"></a><a id="5__359" target="_blank"></a>5. 命名规范</h3>
<ul>
<li>变量名: 必须使用 <code>camel</code> 命名法</li>
<li>参数名: 必须使用 <code>camel</code> 命名法</li>
<li>函数名: 必须使用 <code>camel</code> 命名法</li>
<li>方法/属性: 必须使用 <code>camel</code> 命名法</li>
<li>私有 ( 保护 ) 成员: 必须以下划线开头</li>
<li>常量名: 必须使用全部大写的下划线命名法,e.g. XTEP_HOST_API</li>
<li>类名: 必须使用 <code>pascal</code><sup class="footnote-ref"><a href="#fn8" rel="nofollow" id="fnref8" target="_self">8</a></sup> 命名法</li>
<li>枚举名: 必须使用 <code>pascal</code> 命名法</li>
<li>枚举的属性: 必须使用全部大写的下划线命名法,e.g. XTEP_HOST_API</li>
<li>命名空间: 必须使用 <code>camel</code> 命名法</li>
<li>语义: 命名同时还需要关注语义
<blockquote>
<ul>
<li>变量名应当使用名词</li>
<li>boolean 类型的应当使用 <code>is</code> <code>has</code> 等起头,表示其类型</li>
<li>函数名应当用动宾短语 e.g. DrawBox()</li>
<li>点击事件命名方式为 <code>tap</code> + 事件名 e.g. onClick()</li>
<li>类名应当用名词</li>
</ul>
</blockquote>
</li>
</ul>
<h3><a name="t17"></a><a id="6__378" target="_blank"></a>6. 声明</h3>
<ul>
<li>在函数的开始应先用 <code>var</code> <code>let</code> 关键字声明函数中要使用的局部变量</li>
<li>注释变量的功能及代表的含义,且应以字母顺序排序.每个变量单独占一行以便添加注释</li>
</ul>
<h3><a name="t18"></a><a id="7__383" target="_blank"></a>7. 回调函数规范</h3>
<ul>
<li>回调函数统一使用 <code>Promise</code> 函数,回调成功的参数统一为 res,错误参数为 err</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    let callback = new Promise((resolve, reject) =&gt; {
        if (/* 异步操作成功 */){
            resolve(value);
        } else {
            reject(err);
        }
    });
    callback.then((res) =&gt; {
        console.log('成功回调！', res);
    }).catch((err) =&gt; {
        console.log('失败回调！', err);
    });

<ul>
<li>私有函数以及回调函数统一放置在生命周期函数后,每个函数之间用一个空行分离结构,删除 js 文件中未用到的生命周期函数,保持代码的整洁,精简</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    Pages({
        data:{
        },
    onLoad:function(event){
        },
        _self:function(){
        }
    })

<h3><a name="t19"></a><a id="8__421" target="_blank"></a>8. 数据绑定变量定义规范</h3>
<ul>
<li>所有涉及到数据绑定的变量均需在 <code>data</code> 中初始化.禁止在不定义的情况下直接 <code>setData</code>,或者出现 <code>undefined</code></li>
<li>涉及到数据绑定的变量写 <code>data</code> 中,页面内传递的写在 <code>page</code> 中</li>
</ul>
<h3><a name="t20"></a><a id="9__426" target="_blank"></a>9. 函数默认值</h3>
<ul>
<li>所有的函数参数的默认值要写在参数后面</li>
</ul>
<pre class="prettyprint"><code class="prism language-JS has-numbering" onclick="mdcp.copyCode(event)">    function zxm(name = 'zxm'){
        console.log(name)
    }

<h2><a name="t21"></a><a id="_436" target="_blank"></a>三、组件规范</h2>
<h3><a name="t22"></a><a id="1__438" target="_blank"></a>1. 组件名命名规范</h3>
<ul>
<li>组件在使用时命名以 " x- " 为开头的组件名,若组件名称为多个单词名拼接而成,采用 " - " 连接.</li>
<li>组件标签在 page 页面使用时推荐使用单闭合标签,包含 <code>slot</code>的组件除外</li>
</ul>
<h3><a name="t23"></a><a id="2__443" target="_blank"></a>2. 触发事件规范</h3>
<ul>
<li>组件点击触发事件建议用冒号分隔开</li>
</ul>
<pre class="prettyprint"><code class="prism language-html has-numbering" onclick="mdcp.copyCode(event)">    <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>x-component-tag-name</span> <span class="token attr-name"><span class="token namespace">bind:</span>myevent</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>onMyEvent<span class="token punctuation">"</span></span> <span class="token punctuation">/&gt;</span></span>

<h3><a name="t24"></a><a id="3_externalClasses__451" target="_blank"></a>3. externalClasses 命名规范</h3>
<ul>
<li>命名格式采用如下形式: <code>x-class-{name}</code></li>
</ul>
<h3><a name="t25"></a><a id="4__455" target="_blank"></a>4. 组件样式规范</h3>
<ul>
<li>命名必须以 <code>x-</code> 开头</li>
</ul>
<h2><a name="t26"></a><a id="_459" target="_blank"></a>四、标点规范</h2>
<ul>
<li><code>JS</code> 中一致使用反引号 ` 或单引号 ‘’ , 不使用双引号</li>
<li><code>WXML</code> <code>CSS</code> <code>JSON</code> 中均应使用双引号。</li>
</ul>
<h2><a name="t27"></a><a id="_464" target="_blank"></a>五、注释规范</h2>
<ul>
<li>
<p>TODO: + 说明：</p>
<blockquote>
<p>如果代码中有该标识，说明在标识处有功能代码待编写，待实现的功能在说明中会简略说明。</p>
</blockquote>
</li>
<li>
<p>FIXME: + 说明：</p>
<blockquote>
<p>如果代码中有该标识，说明标识处代码需要修正，甚至代码是错误的，不能工作，需要修复，如何修正会在说明中简略说明。</p>
</blockquote>
</li>
<li>
<p>XXX: + 说明：</p>
<blockquote>
<p>如果代码中有该标识，说明标识处代码虽然实现了功能，但是实现的方法有待商榷，希望将来能改进，要改进的地方会在说明中简略说明。</p>
</blockquote>
</li>
<li>
<p>HACK:+ 说明:</p>
<blockquote>
<p>如果代码中有该标识，说明标识处代码我们需要根据自己的需求去调整程序代码。</p>
</blockquote>
</li>
<li>
<p>UNDONE: + 说明:</p>
<blockquote>
<p>如果代码中有该标识，说明在标识处有功能代码未写完，未写完的功能在说明中会简略说明。</p>
</blockquote>
</li>
<li>
<p>NOTE: + 说明:</p>
<blockquote>
<p>如果代码中有该标识，用来解释说明这个功能的作用。</p>
</blockquote>
</li>
<li>
<p>BUG: + 说明:</p>
<blockquote>
<p>如果代码中有该标识，用来标识此处代码有一个问题,问题会简略说明。</p>
</blockquote>
</li>
</ul>
<hr class="footnotes-sep">
<section class="footnotes">
<ol class="footnotes-list">
<li id="fn1" class="footnote-item"><p>骆驼式命名法( Camel-Case )又称驼峰式命名法,是电脑程式编写时的一套命名规则(惯例).正如它的名称 <code>CamelCase</code> 所表示的那样,是指混合使用大小写字母来构成变量和函数的名字. <a href="#fnref1" rel="nofollow" class="footnote-backref" target="_self">↩︎</a></p>
</li>
<li id="fn2" class="footnote-item"><p>可枚举性 <code>enumerable</code> 用来控制所描述的属性,是否将被包括在 for…in 循环之中.如果一个属性的 <code>enumerable</code> 为 <code>false</code> , <code>for-in</code> <code>Object.keys</code> <code>JSON.stringify</code> 将不会取到该属性. <a href="#fnref2" rel="nofollow" class="footnote-backref" target="_self">↩︎</a></p>
</li>
<li id="fn3" class="footnote-item"><p>表示能否通过 <code>delete</code> 删除此属性,能否修改属性的特性,或能否修改把属性修改为访问器属性,如果直接使用字面量定义对象,默认值为 true <a href="#fnref3" rel="nofollow" class="footnote-backref" target="_self">↩︎</a></p>
</li>
<li id="fn4" class="footnote-item"><p>表示该属性是否可枚举,即是否通过 <code>for-in</code> 循环或 <code>Object.keys()</code> 返回属性,如果直接使用字面量定义对象,默认值为 true <a href="#fnref4" rel="nofollow" class="footnote-backref" target="_self">↩︎</a></p>
</li>
<li id="fn5" class="footnote-item"><p>能否修改属性的值,如果直接使用字面量定义对象,默认值为 true <a href="#fnref5" rel="nofollow" class="footnote-backref" target="_self">↩︎</a></p>
</li>
<li id="fn6" class="footnote-item"><p>该属性对应的值,默认为 <code>undefined</code> <a href="#fnref6" rel="nofollow" class="footnote-backref" target="_self">↩︎</a></p>
</li>
<li id="fn7" class="footnote-item"><p>返回一个所有元素为字符串的数组,其元素来自于从给定的 <code>object</code> 上面可直接枚举的属性.这些属性的顺序与手动遍历该对象属性时的一致 <a href="#fnref7" rel="nofollow" class="footnote-backref" target="_self">↩︎</a></p>
</li>
<li id="fn8" class="footnote-item"><p>单字之间不以空格断开或连接号或下划线连结,第一个单字首字母采用大写字母,后续单字的首字母亦用大写字母.例如: <code>FirstName</code> <code>LastName</code> <a href="#fnref8" rel="nofollow" class="footnote-backref" target="_self">↩︎</a></p>
</li>
</ol>
</section>

