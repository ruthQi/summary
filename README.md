# 深度拷贝
let obj = {
   a: {
      b: 1
   },
   c: function(){
      console.log('8888888')
   },
   d: [1,2,4]
}

function deepClone(obj){
   let objClone = Array.isArray(obj) ? [] : {};
   for(key in obj){
      if(obj.hasOwnProperty(key)){
         if(obj[key] && typeof obj[key] == 'object'){
            objClone[key] = deepClone(obj[key])
         }else{
            objClone[key] = obj[key]
         }
      }
   }
   return objClone;
}
console.log(deepClone(obj))
