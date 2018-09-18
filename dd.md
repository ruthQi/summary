1.	实现二分查找，时间复杂度(二分查找操作的数据集是一个有序的数据集。)
function binarySearch(target, arr){
   let start = 0;
   let end = arr.length -1;
   
   while(start <= end){
      let mid = parseInt(start+(end-start)/2);
      if(target == arr[mid]){
         return mid;
      }else if(target < arr[mid]){
         end = mid-1;
      }else if(target > arr[mid]){
         start = mid + 1;
      }
   }
   return -1;
}

binarySearch(6, [2,4,5,6,8,10])
时间复杂度：O(log n)
2.	js实现深度拷贝
let obj = {
   a: {
      b: 1
   },
   c: function(){
      console.log('8888888')
   }
}

console.log(JSON.parse(JSON.stringify(obj)))// {a: {…}}，过滤函数

//递归遍历
function deepClone(obj){
    let objClone = Array.isArray(obj)?[]:{};
    if(obj && typeof obj==="object"){
        for(key in obj){
            if(obj.hasOwnProperty(key)){
                //判断ojb子元素是否为对象，如果是，递归复制
                if(obj[key]&&typeof obj[key] ==="object"){
                    objClone[key] = deepClone(obj[key]);
                }else{
                    //如果不是，简单复制
                    objClone[key] = obj[key];
                }
            }
        }
    }
    return objClone;
}

console.log(deepClone(obj))
3.	页面滚动无限加载图片，给图片绑定click事件
事件委托：利用事件冒泡，把监听事件添加到父元素上，父元素监督元素的点击事件
4.	使用flex, float, position实现以下布局

方式1：flex
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge">
   <title>Document</title>
   <style type="text/css">
      .container{
         display: flex;
         width: 800px;
         height: 400px;
         justify-content: space-between;
      }
      .div{
         width: 200px;
         height: 100px;
         background-color: skyblue;
      }
      .div:nth-child(2){
         align-self: center;
      }
      .div:nth-child(3) {
         align-self: flex-end;
      }
   </style>
</head>
<body>
   <div class="container">
      <div class="div div1"></div>
      <div class="div div2"></div>
      <div class="div div3"></div>
   </div>
</body>
</html>
方式2：position
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge">
   <title>Document</title>
   <style type="text/css">
      .container{
         position: relative;
         width: 800px;
         height: 400px;
      }
      .div{
         width: 200px;
         height: 100px;
         background-color: skyblue;
      }
      .div:nth-child(1){
         position: absolute;
         top: 0px;
         left: 0px;
      }
      .div:nth-child(2){
         position: absolute;
         left: 50%;
         top: 50%;
         transform: translate(-50%, -50%);
      }
      .div:nth-child(3){
         position: absolute;
         right: 0px;
         bottom: 0px;
      }
   </style>
</head>
<body>
   <div class="container">
      <div class="div div1"></div>
      <div class="div div2"></div>
      <div class="div div3"></div>
   </div>
</body>
</html>

方式3：float+margin
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge">
   <title>Document</title>
   <style type="text/css">
      .container{
         overflow: hidden;
         width: 800px;
         height: 400px;
      }
      .div{
         width: 200px;
         height: 100px;
         background-color: skyblue;
      }
      .div:nth-child(1){
         float: left;
      }
      .div:nth-child(2){
         margin: 130px auto 0px;
      }
      .div:nth-child(3){
         float: right;
         margin-top: 70px;
      }
   </style>
</head>
<body>
   <div class="container">
      <div class="div div1"></div>
      <div class="div div2"></div>
      <div class="div div3"></div>
   </div>
</body>
</html>


<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge">
   <title>Document</title>
   <style type="text/css">
      .p1{
         display: flex;
         justify-content: flex-start;
      }
      .p2{
         display: flex;
         justify-content: center;
      }
      .p3{
         display: flex;
         justify-content: flex-end;
      }
      .div{
         width: 200px;
         height: 100px;
         background-color: skyblue;
      }
      
   </style>
</head>
<body>
   <div class="container">
      <div class="p1">
         <div class="div div1"></div>
      </div>
      <div class="p2">
         <div class="div div2"></div>
      </div>
      <div class="p3">
         <div class="div div3"></div>
      </div>
   </div>
</body>
</html>



<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge">
   <title>Document</title>
   <style type="text/css">
      .p1{
         position: absolute;
         top: 0px;
         left: 0px;
      }
      .p2{
         position: absolute;
         top: 50%;
         left: 50%;
         transform: translate(-50%, -50%);
      }
      .p3{
         position: absolute;
         right: 0px;
         bottom: 0px;
      }
      .div{
         width: 200px;
         height: 100px;
         background-color: skyblue;
      }
      
   </style>
</head>
<body>
   <div class="container">
      <div class="p1">
         <div class="div div1"></div>
      </div>
      <div class="p2">
         <div class="div div2"></div>
      </div>
      <div class="p3">
         <div class="div div3"></div>
      </div>
   </div>
</body>
</html>


float浮动实现
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge">
   <title>Document</title>
   <style type="text/css">
      /* .container{
         overflow: hidden;
         width: 800px;
         height: 400px;
      } */
      .div{
         width: 200px;
         height: 100px;
         background-color: skyblue;
      }
      .div:nth-child(1){
         float: left;
      }
      .div:nth-child(2){
         clear: both;
         margin: 0 auto;
      }
      .div:nth-child(3){
         float: right;
      }
   </style>
</head>
<body>
   <div class="container">
      <div class="div div1"></div>
      <div class="div div2"></div>
      <div class="div div3"></div>
   </div>
</body>
</html>



5.	输出以下结果
var a = 200;
function create(){
   var a = 100;
   return function(){
      alert(a)
   }
}
let fn = create();
fn();//100
var a = 200;
function create(fn){
   var a = 100;  
   fn();
}

function test(){
   alert(a)
}
create(test)//200

6.	写出知道的http 码
200， 301， 302， 304， 400， 403， 404， 500， 502

7.	git命令
git add(添加到暂存区) git pull, git push, git commit
熟悉git的暂存区，工作区这些吗？
https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013745374151782eb658c5a5ca454eaa451661275886c6000

8. 	let i;
let arr = [1,2,3,4,5];
for(i = 0; i < arr.length-1; i++){
   setTimeout(()=>{
      console.log(arr[i])//5,5,5,5
   }, 1000)
}

let arr = [1,2,3,4,5];
for(let i = 0; i < arr.length-1; i++){
   setTimeout(()=>{
      console.log(arr[i]);//1,2,3,4
   }, 1000)
}


9.//200, 300, 100
setTimeout(()=>{
   console.log(100)
});
console.log(200);
Promise.resolve().then(()=>{
   console.log(300)
})

10. 样式优先级
行内样式，#id，class，标签
11. instanceof
A instanceof B: 检测B.prototype是否存在于参数A的原型链上
console.log(123 instanceof Number)//false
console.log(new Number(123) instanceof Number)//true
console.log(Number(123) instanceof Number)//false

实现：
function _instanceof(A, B){
   let O = B.prototype;
   A = A.__proto__;
   console.log(A)
   while(true){
      if(A === null){
         return false;
      }else if(A === O){
         return true;
      }
      A = A.__proto__
   }
}
