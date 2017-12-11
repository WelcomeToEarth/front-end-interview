# 水平居中
1. 使用inline-block 和 text-align实现
```
.parent{text-align: center;} 
.child{display: inline-block;}

```
2. 使用margin:0 auto来实现
```
.child{width:200px;margin:0 auto;}
```
3. 使用绝对定位
```
.parent{position:relative;}
/*或者实用margin-left的负值为盒子宽度的一半也可以实现，不过这样就必须知道盒子的宽度，但兼容性好*/
.child{position:absolute;left:50%;transform:translate(-50%);}
```
4. 使用flex布局
```
/*第一种方法*/
.parent{display:flex;justify-content:center;} 
/*第二种方法*/
.parent{display:flex;} 
.child{margin:0 auto;}
```
# 垂直居中
1. 使用vertical-align
```
/*第一种方法*/
.parent{display:table-cell;vertical-align:middle;height:20px;} 
/*第二种方法*/
.parent{display:inline-block;vertical-align:middle;line-height:20px;}
```
2. 使用绝对定位
```
.parent{position:relative;} 
.child{positon:absolute;top:50%;transform:translate(0,-50%);}
```
3. 使用flex
```
.parent{display:flex;align-items:center;}
```
# 水平垂直居中
1. 利用vertical-align,text-align,inline-block实现
```
.parent{display:table-cell;vertical-align:middle;text-align:center;}
.child{display:inline-block;}

```
2. 使用绝对定位
```
/*宽高已知*/
.div1{
            width:500px;
            height:500px;
            border:1px solid black;
            position: relative;     /*很重要,不能忘*/
        }
        .div2{
            background: yellow;
            width:300px;
            height:200px;
            margin-left:-150px;
            margin-top:-100px;
            top:50%;
            left:50%;
            position: absolute;
            }
 ```
 ```
  .div1{
            width:500px;
            height:500px;
            border:1px solid black;
            position: relative;     /*很重要,不能忘*/
        }
        .div2{
            background: yellow;
            width:300px;
            height:200px;
            margin:auto;
            bottom: 0;
            top:0;
            left:0;
            right:0;
            position: absolute;
  ```
  ```
 /*宽高未知*/
 .div1{
            width:500px;
            height:500px;
            border:1px solid black;
            position: relative;
        }
        .div2{
            background: yellow;
            position: absolute;
            left: 30%;
            right: 30%;
            top:40%;
            bottom: 40%;
        }
 ```
 ```
 .div1{
            width:500px;
            height:500px;
            border:1px solid black;
            position: relative;
        }
        .div2{
            background: yellow;
            position: absolute;
            /*width:200px;*/
            top:50%;
            left:50%;
            transform:translate(-50%,-50%);
        }
 ```
 ```
 .div1{
            width:500px;
            height:500px;
            border:1px solid black;
            position: relative;
        }
        .div2{
            background: yellow;
            position: absolute;
            left: 30%;
            right: 30%;
            top:40%;
            bottom: 40%;
        }
 
```
3. 使用flex布局
```
.parent{display:flex;justify-content:center;align-items:center;}

```
# 多列布局
## 左列定宽 右列自适应
1. 利用float+margin实现
```
.left{float:left;width:100px;} 
.right{margin-left;margin-left:100px;}

```
2. 利用float+margin(fix)实现
```
<div class="parent"> 
  <div class="left"></div>
  <div class="right-fix"> 
    <div class="right"></div>
  </div>
</div>
```
```
.left{width:100px;float:left;}
.right-fix{width:100%;margin-left:-100px;float:right;}
.right{margin-left:100px;}

```
3. 使用float+overflow实现
```
.left{width:100px;float:left;} 
.right{overflow:hidden;}

```
## 右列定宽，左列自适应
1. 实用float+margin实现
```
.parent{background:red;height:100px;margin:0 auto;}
.left{background:green;margin-right:-100px;width:100%;float:left;}
.right{float:right;width:100px;background:blue;}
```
2. 使用table实现
```
.parent{display:table;table-layout:fixed;width:100%;}
.left{display:table-cell;}
.right{width:100px;display:table-cell;}
```
3. 实用flex实现
```
.parent{display:flex;}
.left{flex:1;}
.right{width:100px;}
```
## 两列定宽，一列自适应
1. 利用float+margin实现
```
.left,.center{float:left:width:200px;}
.right{margin-left:400px;}
```
2. 利用float+overflow实现
```
.left,.center{float:left:width:200px;}
.right{overflow:hidden;}
```
3. 利用table实现
```
.parent{display:table;table-layout:fixed;width:100%;}
.left,.center,.right{display:table-cell;}
.left,.center{width:200px;}
```
4. 利用flex实现
```
.parent{display:flex;}
.left,.center{width:100px;}
.right{flex:1}
```
## 两侧定宽，中栏自适应
1. 利用float+margin实现
```
.left{width：100px;float:left;}
.center{float:left;width:100%;margin-right:-200px;}
.right{width:100px;float:right;}
```


