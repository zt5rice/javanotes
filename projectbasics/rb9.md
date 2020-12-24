# Project 1
- difference between header and nav tag header, how to choose?

    这个问题是这样的，我们的项目上面的红色区域整体是header，具体到左边的链接的部分是用nav标签来表示,所以在写的时候一般来讲网页的顶部是用header，nav标签嵌套在header里面
    
- HOC 作用 higher order component是干什么的？ 比如 export const WrappedCreatePostForm = Form.create()(CreatePostForm); 为什么要export这个新的，而不是直接CreatePostForm？

    Form.create() 返回一个HOC。这个HOC并不是一个Component，而是一个接受普通Form作为parameter，然后返回一个自动可校验Form的增强Form的function。相当于 const HOC = Form.create(); const WrappedCreatePostForm = HOC(CreatePostForm); WrappedCreatePostForm这个带自动校验的Form才是我们最后要在Modal里面放的Form。

- mockSearchResponse不用import之类的吗？这是JS的什么语法？

    mockSearchResponse是mock.js里面定义的一个global variable它本身是一个array of objects，因为mock.js在main.js之前引用所以main.js可以用到这个global variable.

- 请问float和flex一般怎么判断什么时候用哪个呢？

    这个看你的project的需求了，如果不需要支持老的浏览器，用flex就可以了（flex box还可以帮助处理居中等问题）

Class 属性的作用是不是为了让developer更容易理解，然后后面CSS也可以方便对这一部分进行处理？ 还有 span section div这样的tag除了读起来容易理解，是不是也会被后面CSS用到？

   class主要是方便CSS的使用，因为class是针对一类具有相似属性的html element的，所以可以用来表示它们的common的部分。所有的tag都可以被CSS使用，这个并不是我们使用span section div的原因

- 对于callback function，我始终有点无法理解。这些parameter 都是怎么传入callback function 里的呢，还有就是，callback function一定是等到所有操作都结束了才执行的么

    $.get是jquery提供的一个用来发get ajax request的function. 它的内部实现还是使用XMLHttpRequest来做的。这里我们传的第一个参数是URL，第二个参数是function，jquery的$.get给你的保证是你在第二个parameter传给它的function会在request成功之后被call并且被传入Response object里面的data。注意这里data并不是$.get的parameter而是它第二个parameter(a function)的parameter。

课上很多地方用到了AJAX，但是关于AJAX到底是什么，我非常模糊，也解释不清楚。 AJAX只是针对java script 和 xml的吗？

    先看一下科普页 Wiki https://en.wikipedia.org/wiki/Ajax_(programming) 这个知识点的核心不在于是用JS或是XML而是要理解asynchronous和synchronize HTTP request的区别。同时掌握通过XMLHttpRequest这个global object发送和接收asynchronous HTTP request的方式。具体的code可以参照我们第一个recommendation项目或者下面的Mozilla官方的页面. XMLHttpRequest https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest

感觉完全可以用constructor进行初始化为什么还要用static initializer呢？

    Static initializer 用来初始化 static member，而且执行不需要创建对象。如果你的 class 没有实例化对象的话就需要用 static initializer 来初始化 static members 或者在 class loading 的时候执行一些操作。在我们的课程里主要在 JDBC 的实现时使用 static initializer，因为我们没有创建 JDBC class 的 object，而是利用 JDBC 的 static initializer 来注册数据库的驱动。

请问下什么样的场景需要用到jQuery这个JS library？

    JQuery比较常用的场合是需要做DOM manipulation和发Ajax request的时候。

-我们从api中获取了event的所有数据为啥不直接传到前端或者存到数据库，要这个item 类到底是干嘛的

    首先前端不需要你所有的数据，如果全部都传过去前端的load很大会影响latency其次你也不能整个存数据库，一样的道理有些数据对我们来说没有用的

- external package是我们的web server向TicketMaster API提取数据。我们关心的是那个_embedded下的events JSONArray. 这个array里面是一个一个的event,每个event是一个JSONObject吗？ 我们还写了一个entity package, 这个package下的Item class是在clean我们得到的events JSONArray还是这个array里面的每一个event呢？然后就是，这两个package是怎么相互调用来完成parse and clean event array to only save data we want的？

    external只是负责往外面读API数据 你的理解是对的 entity是整个project里边描述一个event的java object 可以转存成为比如说db里边的table

- 在postman里可以选择GET或POST request， 但是一般的浏览器里，用户只输入URL，并没有额外选择request的method，所以浏览器是如何自动选择http method的？

    你的前端的代码里边是可以自由选择的 浏览器如果只输入URL默认是GET

- 面试题：如何提高Ticket+这个项目服务器处理请求的能力？哪一部分是限制服务器处理请求能力的关键，哪个地方最容易出问题？

    单纯从performance的角度来说 背后的TicketMaster API的throughput是其中的single node 其他都可以在我们的控制下比如说分配更多的资源 那么大家可以想想在这个命题下提高我们对TicketMaster API的利用效率，假设他只能处理比如说10个QPS 思路1. 有没有什么办法可以减少我们这边发送的请求， 比如说可否中间有个proxy server，把一些相似的请求缓存起来，然后同样的请求都不需要再跟API要一遍了 再比如说可否做一些data study，假设我们都已经知道他附近的另外几个点附近的events，我们不可以做个简单的地理建模把他们中间的某个点也算出来吗？ 思路2. 如果我们不需要马上实时返回，为了避免出现HTTP timeout的出现，可否建成队列然后以10QPS的上限开始发送请求 思路3. 有没有可能我们完全摆脱TicketMaster API的限制，另起炉灶？

- 我看到我们遇到exception时候，要么是在函数声明地方加trows exception, ，另一种是try， catch的方法。这两种方法有什么区别么？

    throws意味着可能抛出某种异常，但是不一定自己来处理，可能留给别的method来接；try catch就是自己来接这个异常并且进行对应处理

- 我们为什么用json作为body？所有object都可以转化为json吗？

    HTML是专门用来制作网页的语言，如果你后端程序返回的内容是直接在浏览器里显示的，那返回HTML会更好。但是多数情况下返回的内容不会直接显示到浏览器里，而是需要加工处理，或者根本不是返回给浏览器的，这些情况下JSON这种格式处理起来会比HTML容易的多。比如TicketMaster API返回的内容是有后端的Java代码接收的，不会直接显示到浏览器里，Java代码在创建和解析JSON格式的数据时就会比处理HTML格式容易。 JSON是一种key-value pair的格式，类似于HashMap，如果一个Object可以通过key-value pair的形式体现的话，那么就可以转换成JSONObject。所以在上课的例子里Item的object可以转成JSONObject，因为你可以把Item的每一个private field当成一个key，而对应的值就是value。 如果一个请求的操作类型不是通过http method来指定，而是通过参数，比如localhost:8080/Jupiter/search?method=GET, 那么你在处理请求的时候是不是还需要多判断一下url里边method这个参数的内容。
