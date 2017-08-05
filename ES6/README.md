# ES6 语法

## 在本地运行 ES6 脚本
### 打包管理
- webpack
- gulp

### 安装
- npm init -y
  - 建立 package.json 文件
- babel-cli
  - 对 js 文件 进行转换

### 本地安装
- npm install --save-dev
- babel-preset-es2015
- babel-cli

### 新建 .babelrc 文件

## 解构赋值
- 解构的默认值

## 对象扩展符 ...
- rest 运算符

## 字符串模板
- `string ${object} <html tags>`
- 字符串查找
  - includes
  - startsWith
  - endsWith

## 数组
- for let item of array
- for [index, val] of array.entries()
- forEach
- filter
- some
- map

## Pormise
```
function = (resolve,reject) => {
    if(condition){
        resolve();
    }else{
        reject();
    }
}

new Promise(function).then(function(val){
    console.log(val);
    return new Promise(function);
}).then(function(val){
     console.log(val);
});
```
