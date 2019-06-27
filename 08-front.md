## 前端代码规范
一、WXML 规范
1. 属性顺序(不必要的情况下)

        class ( class 是为高可复用组件设计的,所以应处在第一位)
        id name (id 更加具体且应该尽量少使用,所以将它放在第二位)
        data-\*
        src for type href value
        placeholder title alt
        aria-\* role
        required readonly disabled

2. id / class 命名规则

        首先根据内容命名,如 header footer
        若根据内容无法找到合适的命名,再结合行为表现进行辅助, e.g. col-main blue-box
        名字一律小写,多个单词用 - 连接,不能使用下划线和 camel1 命名法, e.g. main-title 可基于最近的父元素名称作为前缀
        在不影响语义的情况下,可适当使用缩写,但是缩写只用来表示结构, e.g. col nav btn etc. , 别给我自编.
        避免广告拦截词汇 e.g. ad ads adv banner sponsor gg guangg guanggao etc.

3. WXML 注释规范

        <!-- 头部 -->
        <view class="header">
          <!-- LOGO -->
          <image class="logo"></image>
          <!-- /LOGO -->
          <!-- 详情 -->
          <view class="detail"> </view>
          <!-- /详情 -->
        </view>
        <!-- /头部 -->



二、CSS 规范
属性顺序

    位置属性 ( position top right z-index display float etc.)
    大小 ( width height padding margin etc.)
    文字系列 ( font line-height letter-spacing color text-align ect.)
    背景 ( background border etc.)
    其他 ( animation transition etc.)
    以及注释的写法

    /* Button */
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



选择器

    尽量不用选择器。

属性使用缩写

    尽量使用简写 e.g. padding margin font background border border-radius etc.
    颜色代码尽量也简写 e.g. 白色 #fff

去掉小数点前面的 0

    0.8 => .8

三、 JS 规范
1. 语言规范

    声明变量必须加上 let 关键字.不要再使用 var
    优先使用箭头函数
    使用模板字符串取代连接字符串

        // worst
        let url = "pages/index/index?id=" + id + "&title=321GO"

        //best
        let url = `pages/index/index?id=${id}&title=321GO`


2. 使用分号

    如果仅依靠语句间的隐式分隔,有时会很麻烦,使用分号更能清楚哪里是语句的起止,而且有些情况下,漏掉分号会出 BUG

3. 块内函数声明

    不要在块内声明一个函数,e.g.

        if (x) {
            function zxm() {}
        }



    如果确实需要,使用函数表达式来初始化变量

        if (x) {
            let foo = function() {}
        }



4. 关于循环
4.1 forEach

    forEach 是用来循环数组的

    let zxmArray = [3,2,1,"GO"];
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
    for (var i = 0; i < zxmArray.length; i++) {
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



    forEach 不支持 break continue

    let zxmArray = [3,2,1,"GO"];
    zxmArray.forEach(function(value) {
        console.log(value);
            // 不能使用break
            break;
            //不能使用continue
            continue;
    });



forEach 过程中 arr.push() arr.pop() arr.shift() arr.unshift() arr.reverse() arr.sort() arr.concat() 都可以使用,但是arr.push() 不会改变输出顺序.

4.2 map

    map() 方法返回一个由原数组中的每个元素调用一个指定方法后的返回值组成的新数组

    let zxmArray = [3,2,1,"GO"];
    let tempArr = zxmArray.map((value,index)=>{
        console.log(value, index);
        return "zxm" + value
    })
    console.log(tempArr)// [ 'zxm3', 'zxm2', 'zxm1', 'zxmGO' ]

    function add(num) {
        return num + 10
    }
    let zxmAdd = [3,2,1];
    let tempAdd = zxmAdd.map(add);
    console.log(tempAdd)//[ 13, 12, 11 ]



4.3 for-in

    for-in 循环实际是为循环 enumerable2 对象而设计的
    configurable3 writable4 enumerable5 value6

    let zxmObj = {
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
        console.log("zxmObj." + prop + " = " + zxmObj[prop]);
        //zxmObj.a = 3 zxmObj.b = 2 zxmObj.c = 1
        zxmObj.d = GO zxmObj.address = Xtep
    }


    for–in 是用来循环带有字符串 key 的对象的方法

4.4 for-of

    墙裂推荐使用 for-of 既比传统的 for 循环简洁,同时弥补了 forEach 和 for-in 循环的缺点

    for-of 循环数组

    let zxmArray = [3,2,1,"GO"];
    for (var value of zxmArray) {
        console.log(value);// 3 2 1 GO
    }

    for-of 循环字符串

    let zxmString = "321GO";

    for (let value of zxmString) {
        console.log(value);// 3 2 1 G O
    }

    for-of 循环类型化的数组

    let zxmArray = new Uint8Array([0x00, 0xff]);

    for (let value of zxmArray) {
    console.log(value);// 0 255
    }
    for-of 循环 Map
    let zxmMap = new Map();
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


    for-of 循环 set

    let zxmSet = new Set([1, 1, 2, 2, 3, 3]);

    for (let value of zxmSet) {
        console.log(value);
    }



    for-of 循环拥有 enumerable 属性的对象,但是并不能直接使用在普通的对象上,如果我们按对象所拥有的属性进行循环,可使用内置的 Object.keys()7 方法

    let zxmObj = {
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

    for-of 循环生成器 ( generators ) 然鹅微信小程序并不支持 async await 也不支持
    function* fibonacci() { // a generator function
    let [prev, curr] = [0, 1];
    while (true) {
        [prev, curr] = [curr, prev + curr];
        yield curr;
    }
    }

    for (let n of fibonacci()) {
    console.log(n);
    // truncate the sequence at 1000
    if (n >= 1000) {
        break;
    }
    }


5. 命名规范

    变量名: 必须使用 camel 命名法
    参数名: 必须使用 camel 命名法
    函数名: 必须使用 camel 命名法
    方法/属性: 必须使用 camel 命名法
    私有 ( 保护 ) 成员: 必须以下划线开头
    常量名: 必须使用全部大写的下划线命名法,e.g. XTEP_HOST_API
    类名: 必须使用 pascal8 命名法
    枚举名: 必须使用 pascal 命名法
    枚举的属性: 必须使用全部大写的下划线命名法,e.g. XTEP_HOST_API
    命名空间: 必须使用 camel 命名法
    语义: 命名同时还需要关注语义

            变量名应当使用名词
            boolean 类型的应当使用 is has 等起头,表示其类型
            函数名应当用动宾短语 e.g. DrawBox()
            点击事件命名方式为 tap + 事件名 e.g. onClick()
            类名应当用名词

6. 声明

    在函数的开始应先用 var let 关键字声明函数中要使用的局部变量
    注释变量的功能及代表的含义,且应以字母顺序排序.每个变量单独占一行以便添加注释

7. 回调函数规范

    回调函数统一使用 Promise 函数,回调成功的参数统一为 res,错误参数为 err

        let callback = new Promise((resolve, reject) => {
            if (/* 异步操作成功 */){
                resolve(value);
            } else {
                reject(err);
            }
        });

        callback.then((res) => {
            console.log('成功回调！', res);
        }).catch((err) => {
            console.log('失败回调！', err);
        });



    私有函数以及回调函数统一放置在生命周期函数后,每个函数之间用一个空行分离结构,删除 js 文件中未用到的生命周期函数,保持代码的整洁,精简

          Pages({
                data:{

            },

            onLoad:function(event){

            },

            _self:function(){

            }
        })



8. 数据绑定变量定义规范

    所有涉及到数据绑定的变量均需在 data 中初始化.禁止在不定义的情况下直接 setData,或者出现 undefined
    涉及到数据绑定的变量写 data 中,页面内传递的写在 page 中

9. 函数默认值

    所有的函数参数的默认值要写在参数后面

        function zxm(name = 'zxm'){
            console.log(name)
        }



三、组件规范
1. 组件名命名规范

    组件在使用时命名以 " x- " 为开头的组件名,若组件名称为多个单词名拼接而成,采用 " - " 连接.
    组件标签在 page 页面使用时推荐使用单闭合标签,包含 slot的组件除外

2. 触发事件规范

    组件点击触发事件建议用冒号分隔开

    <x-component-tag-name bind:myevent="onMyEvent" />

    1

3. externalClasses 命名规范

    命名格式采用如下形式: x-class-{name}

4. 组件样式规范

    命名必须以 x- 开头

四、标点规范

    JS 中一致使用反引号 ` 或单引号 ‘’ , 不使用双引号
    WXML CSS JSON 中均应使用双引号。

五、注释规范

TODO: + 说明：

如果代码中有该标识，说明在标识处有功能代码待编写，待实现的功能在说明中会简略说明。

FIXME: + 说明：

如果代码中有该标识，说明标识处代码需要修正，甚至代码是错误的，不能工作，需要修复，如何修正会在说明中简略说明。

XXX: + 说明：

如果代码中有该标识，说明标识处代码虽然实现了功能，但是实现的方法有待商榷，希望将来能改进，要改进的地方会在说明中简略说明。

HACK:+ 说明:

如果代码中有该标识，说明标识处代码我们需要根据自己的需求去调整程序代码。

UNDONE: + 说明:

如果代码中有该标识，说明在标识处有功能代码未写完，未写完的功能在说明中会简略说明。

NOTE: + 说明:

如果代码中有该标识，用来解释说明这个功能的作用。

BUG: + 说明:

如果代码中有该标识，用来标识此处代码有一个问题,问题会简略说明。

骆驼式命名法( Camel-Case )又称驼峰式命名法,是电脑程式编写时的一套命名规则(惯例).正如它的名称 CamelCase 所表示的那样,是指混合使用大小写字母来构成变量和函数的名字. ↩︎

可枚举性 enumerable 用来控制所描述的属性,是否将被包括在 for…in 循环之中.如果一个属性的 enumerable 为 false , for-in Object.keys JSON.stringify 将不会取到该属性. ↩︎

表示能否通过 delete 删除此属性,能否修改属性的特性,或能否修改把属性修改为访问器属性,如果直接使用字面量定义对象,默认值为 true ↩︎

表示该属性是否可枚举,即是否通过 for-in 循环或 Object.keys() 返回属性,如果直接使用字面量定义对象,默认值为 true ↩︎

能否修改属性的值,如果直接使用字面量定义对象,默认值为 true ↩︎

该属性对应的值,默认为 undefined ↩︎

返回一个所有元素为字符串的数组,其元素来自于从给定的 object 上面可直接枚举的属性.这些属性的顺序与手动遍历该对象属性时的一致 ↩︎

单字之间不以空格断开或连接号或下划线连结,第一个单字首字母采用大写字母,后续单字的首字母亦用大写字母.例如: FirstName LastName ↩︎
