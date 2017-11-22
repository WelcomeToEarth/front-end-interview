* 复制数组
1. by slice 
```
var arr = [1, 2, 3], copyArr; 
copyArr = arr.slice(); 
```
2. by concat
```
var arr = [1, 2, 3], copyArr; 
copyArr = arr.concat();
```
3. by loop
```
var arr = [1, 2, 3], copyArr = []; 
for (var i=0, j=arr.length; 
```
* 数组去重
1. SET 
```
 [...new Set(array)]
```
2. 对象keys不重复
```
Array.prototype.distinct = function (){
  var arr = this,
    i,
    obj = {},
    result = [],
    len = arr.length;
  for(i = 0; i< arr.length; i++){
    if(!obj[arr[i]]){  //如果能查找到，证明数组元素重复了
      obj[arr[i]] = 1;
      result.push(arr[i]);
    }
  }
  return result;
};
```
3. for loop
```
var arr1 =[1,2,2,2,3,3,3,4,5,6], 
arr2 = []; 
for(var i = 0,len = arr1.length; i< len; i++){ 
	if(arr2.indexOf(arr1[i]) < 0){ 
		arr2.push(arr1[i]); 
	} 
} 
document.write(arr2);
```
* 求数组最大值
```
Array.prototype.max = function() {
  var max = this[0];
  var len = this.length;
  for (var i = 1; i < len; i++) {
    if (this[i] > max) {
      max = this[i];
    }
  }
  return max;
}

Math.max.apply( null, array );

Math.max(...[14, 3, 77])
```
* 伪数组转化为标准数组
```
var args = Array.prototype.slice.call(arguments);

let arr2 = Array.from(arrayLike);
```
*  判断一个单词是否是回文
```
function checkPalindrom(str) {  
    return str == str.split('').reverse().join('');
}
```
* 将两个有序数组合并为一个数组。请不要使用concat以及sort方法
```
function merge(left, right) {
  var result = [],
    il = 0,
    ir = 0;

  while (il < left.length && ir < right.length) {
    if (left[il] < right[ir]) {
      result.push(left[il++]);
    } else {
      result.push(right[ir++]);
    }
  }
 //这里注意
  result = result.concat(left[il] ? left.slice(il) : right.slice(ir));
  return result;
}
var left = [1, 4, 7, 8, 9, 10];
var right = [2, 5];
console.log(merge(left, right))
```
* 实现一个函数clone，可以对JavaScript中的5种主要的数据类型（包括Number、String、Object、Array、Boolean）
```
var newObject = JSON.parse(JSON.stringify(oldObject));

function clone(obj) { 
    var o; 
    switch (typeof obj) { 
        case "undefined": 
            break; 
        case "string": 
            o = obj + ""; 
            break; 
        case "number": 
            o = obj - 0; 
            break; 
        case "boolean": 
            o = obj; 
            break; 
        case "object": // object 分为两种情况 对象（Object）或数组（Array） 
            if (obj === null) {o = null; } 
            else {                                 
                if(Object.prototype.toString.call(obj).slice(8, -1) === "Array") { 
                o = []; 
                for (var i = 0; i < obj.length; i++){o.push(clone(obj[i]));} 
                }
                else { 
                o = {}; 
                for (var k in obj) {o[k] = clone(obj[k]);} 
                    } 
                } 
                break; 
                default: 
                o = obj; 
                break; 
        } //switch函数结束
    return o; 
}
```
* 快速排序
```
function quickSort(arr) {
 
    if(arr.length<=1) {
        return arr;
    }
 
    let leftArr = [];
    let rightArr = [];
    let q = arr[0];
    for(let i = 1,l=arr.length; i<l; i++) {
        if(arr[i]>q) {
            rightArr.push(arr[i]);
        }else{
            leftArr.push(arr[i]);
        }
    }
 
    return [].concat(quickSort(leftArr),[q],quickSort(rightArr));
}
```
* 冒泡排序
```
var examplearr=[8,94,15,88,55,76,21,39];
function sortarr(arr){
    for(i=0;i<arr.length-1;i++){
        for(j=0;j<arr.length-1-i;j++){
            if(arr[j]>arr[j+1]){
                var temp=arr[j];
                arr[j]=arr[j+1];
                arr[j+1]=temp;
            }
        }
    }
    return arr;
}
sortarr(examplearr);
console.log(examplearr);
```
* 统计字符串”aaaabbbccccddfgh”中字母个数
```
var str = "aaaabbbccccddfgh"; 
var obj = {}; 
for(var i=0;i<str.length;i++){
	var v = str.charAt(i);
	if(obj[v]&&obj[v].value==v){
		obj[v].count=++obj[v].count;
	}else{
		obj[v]={};
		obj[v].count=1;
		obj[v].value=v;
	}
}
for(key in obj){
	documemt.write(obj[key].value+'='+obj[key].count+'');//a=4 b=3 c=4 d=2 f=1 g=1 h=1
}
```
* 统计字符串最多字母数
```
function findMaxDuplicateChar(str) {  
  if(str.length == 1) {
    return str;
  }
  let charObj = {};
  for(let i=0;i<str.length;i++) {
    if(!charObj[str.charAt(i)]) {
      charObj[str.charAt(i)] = 1;
    }else{
      charObj[str.charAt(i)] += 1;
    }
  }
  let maxChar = '',
      maxValue = 1;
  for(var k in charObj) {
    if(charObj[k] >= maxValue) {
      maxChar = k;
      maxValue = charObj[k];
    }
  }
  return maxChar;
 
}
```
* 清除字符串前后空格
```
function trim(str) {
	if (str && typeof str === "string") {
		return str.replace(/(^\s)|(\s)$/g,""); //去除前后空白符
	}
}
```
* 不借助临时变量，进行两个整数的交换
```
function swap(a , b) {  
  b = b - a;
  a = a + b;
  b = a - b;
  return [a,b];
}
```
```
let x = 1;
let y = 2;

[x, y] = [y, x];
```
* 生成斐波那契数组
```
function getFibonacci(n) {  
  var fibarr = [];
  var i = 0;
  while(i<n) {
    if(i<=1) {
      fibarr.push(i);
    }else{
      fibarr.push(fibarr[i-1] + fibarr[i-2])
    }
    i++;
  }
 
  return fibarr;
}
```
* 找出下列正数组的最大差值   输入 [10,5,11,7,8,9]  输出 6
```
function getMaxProfit(arr) {
 
    var minPrice = arr[0];
    var maxProfit = 0;
 
    for (var i = 0; i < arr.length; i++) {
        var currentPrice = arr[i];
 
        minPrice = Math.min(minPrice, currentPrice);
 
        var potentialProfit = currentPrice - minPrice;
 
        maxProfit = Math.max(maxProfit, potentialProfit);
    }
 
    return maxProfit;
}
```
* 随机生成指定长度的字符串
```
function randomString(n) {  
  let str = 'abcdefghijklmnopqrstuvwxyz9876543210';
  let tmp = '',
      i = 0,
      l = str.length;
  for (i = 0; i < n; i++) {
    tmp += str.charAt(Math.floor(Math.random() * l));
  }
  return tmp;
}
```
* 邮箱的正则匹配 
```
var regMail = /^([a-zA-Z0-9_-])+@([a-zA-Z0-9_-])+((.[a-zA-Z0-9_-]{2,3}){1,2})$/
```
* 使用JS 实现二叉查找树
```
// 一般叫全部写完的概率比较少，但是重点考察你对它的理解和一些基本特点的实现。 二叉查找树，也称二叉搜索树、有序二叉树（英语：ordered binary tree）是指一棵空树或者具有下列性质的二叉树：

// 任意节点的左子树不空，则左子树上所有结点的值均小于它的根结点的值；
// 任意节点的右子树不空，则右子树上所有结点的值均大于它的根结点的值；
// 任意节点的左、右子树也分别为二叉查找树；
// 没有键值相等的节点。二叉查找树相比于其他数据结构的优势在于查找、插入的时间复杂度较低。为O(log n)。二叉查找树是基础性数据结构，用于构建更为抽象的数据结构，如集合、multiset、关联数组等。

class Node {
  constructor(data, left, right) {
    this.data = data;
    this.left = left;
    this.right = right;
  }

  show() {
    return this.data;
  }
}


class BinarySearchTree {

  constructor() {
    this.root = null;
  }

  insert(data) {
    let n = new Node(data, null, null);
    if (!this.root) {
      return this.root = n;
    }
    let currentNode = this.root;
    let parent = null;
    while (1) {
      parent = currentNode;
      if (data < currentNode.data) {
        currentNode = currentNode.left;
        if (currentNode === null) {
          parent.left = n;
          break;
        }
      } else {
        currentNode = currentNode.right;
        if (currentNode === null) {
          parent.right = n;
          break;
        }
      }
    }
  }

  remove(data) {
    this.root = this.removeNode(this.root, data)
  }

  removeNode(node, data) {
    if (node == null) {
      return null;
    }

    if (data == node.data) {
      // no children node
      if (node.left == null && node.right == null) {
        return null;
      }
      if (node.left == null) {
        return node.right;
      }
      if (node.right == null) {
        return node.left;
      }
      
      let getSmallest = function(node) {
        if(node.left === null && node.right == null) {
          return node;
        }
        if(node.left != null) {
          return node.left;
        }
        if(node.right !== null) {
          return getSmallest(node.right);
        }
        
      }
      let temNode = getSmallest(node.right);
      node.data = temNode.data;
      node.right = this.removeNode(temNode.right,temNode.data);
      return node;

    } else if (data < node.data) {
      node.left = this.removeNode(node.left,data); 
      return node;
    } else {
      node.right = this.removeNode(node.right,data);  
      return node;
    }
  }

  find(data) {
    var current = this.root;
    while (current != null) {
      if (data == current.data) {
        break;
      }
      if (data < current.data) {
        current = current.left;
      } else {
        current = current.right
      }
    }
    return current.data;
  }

  findMax() {
    var current = this.root;
    while (current.right != null) {
      current = current.right;
    }
    return current.data;
  }

  findMin() {
    var current = this.root;
    while (current.left != null) {
      current = current.left;
    }
    return current.data;
  }

  inOrder(node) {
    if (!this.inOrderArr) {
      this.inOrderArr = [];
    }
    if (node !== null) {
      this.inOrder(node.left);
      this.inOrderArr.push(node.data);
      this.inOrder(node.right);
    }
  }

  preOrder(node) {
    if (!this.preOrderArr) {
      this.preOrderArr = [];
    }
    if (node !== null) {
      this.preOrderArr.push(node.data);
      this.preOrder(node.left);
      this.preOrder(node.right);
    }
  }

  postOrder(node) {
    if (!this.postOrderArr) {
      this.postOrderArr = [];
    }
    if (node !== null) {
      this.postOrder(node.left);
      this.postOrder(node.right);
      this.postOrderArr.push(node.data);

    }
  }

}
```

