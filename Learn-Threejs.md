
# Learn Three.js

## 第一章 threejs中的各种光源


### AmbientLight(环境光)
#### 一、特点
	1. 没有特定的来源
	2. 它的颜色会影响整个场景
	3. 不会影响阴影
	4. 必须配合其他光源使用，目的在于弱化阴影和加上一些颜色
#### 二、tips
		1. 用色不能过于明亮
****

### PointLight(点光源)
#### 一、特点
	1.单点发光，照射所有方向
	2.不会产生阴影
	3.distance属性指的是光照射的距离
***

### Spotlight(聚光灯光源)
#### 一、重要属性
	1.castShadow(是否有阴影)
	2.angle(光照角度)
	3.exponent(光强衰减指数)
	4.onlyShadow(是否只有阴影)
	5.target(照向哪)
***

### DirectinalLight(方向光|模拟太阳光)
***
### 特殊光源
#### 一、THREE.HemisphereLight(半球光光源)
##### 三个参数：
	1.接受自天空的颜色
	2.接受自地面的颜色
	3.光强		  
***
#### 二、AreaLight(平面光光源)
##### 特点
	1.创建平面光对象的同事创建平面
	
	
	
***
## 第二章 three.js中的材质
***
### 一、基本性质
    1. opacit(0-1)
    2. transport(true/false)
    3. overdraw(true/false)[过度描绘]
    4. visible(true/false)
    5. side(FrontSide/BackSide/THREE.DoubleSide)
    6. noodsUpdate(ture/false)[当材质改变，是否告诉three.js刷新新的材质]

***

### 二、几种不同的材质
#### 1.MeshBasicMaterial(简单材质)
-  简单，不受光照影

    ```
       var meshMaterial = new THREE.MeshBasicMaterial({color: 0x7777ff});
    ```


*** 

#### 2.MeshDepthMaterial（基于深度着色）
- 外观不受光照和材质决定，仅由距离照相机远近决定
    
    ```
        var scene = new THREE.Scene();
    scene.overrideMaterial = new THREE.MeshDepthMaterial();
    ```


#### 3.联合材质

```
var cubeMaterial = new THREE.MeshDepthMaterial();
var colorMaterial = new THREE.MeshBasicMaterial({
    color: controls.color,
    transparent: true,
    blending: THREE.MultiplyBlending
});
var cube = new THREE.SceneUtils.createMultiMaterialObject(cubeGeometry, [colorMaterial, cubeMaterial]);
cube.children[1].scale.set(0.99, 0.99, 0.99);

```
##### 要点
1. MeshBasicMaterial 中 transparent:true;
2. MeshBasicMaterial 中 blending: THREE.MultiplyBlending
