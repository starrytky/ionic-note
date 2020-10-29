# ionic笔记

## 组件
>组件的使用

### ionic 提供的颜色
```
light default secondary dark danger
```

### 按钮 ion-button
```html
<button ion-button>按钮</button>
```
在`ion-button`内放图标
>使用ion-button同级属性 `icon-left` `icon-right` `icon-only` `clear`

ion-icon 组件使用
```html
<button ion-button icon-left >
    <ion-icon name="home" color="light"></ion-icon>
    button(icon-left)>ion-icon
</button>
```
color使用上面提到的的颜色如:dark light secondary danger default

### 列表 ion-list
```html
<!-- 第一类 -->
<ion-list>
    <ion-item *ngFor="let item of items;let key=index" [ngClass]="{'red':key==0}">
    {{item}}
    </ion-item>
</ion-list>
<!-- 第二类：分组 icon-item-divider -->
<ion-list>
    <ion-item-divider color="light">A</ion-item-divider>
    <ion-item *ngFor="let item of itemsA;let key=index">
        {{item}}
    </ion-item>
    <ion-item-divider>B</ion-item-divider>
    <ion-item *ngFor="let item of itemsB;let key=index">
    {{item}}
    </icon-item>
</ion-list>
<!-- 第三组：带图标 ion-icon -->
<ion-list>
    <ion-item>
        <ion-icon name="home" item-start><ion-icon>
        <ion-icon>
        ion-item>ion-icon(item-start/item-end)
        <ion-icon name="rose" item-end><ion-icon>
    </ion-item>
</ion-list>
<!-- 第四组：带图片 ion-thumbnail -->
<ion-list>
    <ion-item>
        <ion-thumbnail item-start>
            <img src="img/01.png"/>
        </ion-thumbnail>
        <h1 >title</h1>
        <button ion-button clear item-end>View</button>
    </ion-item>
</ion-list>
<!-- 第五组：ion-badge 类似聊天泡泡 -->
<ion-list>
    <ion-item>
        <ion-icon name="logo-twitter" item-start></ion-icon>
            Followers
        <ion-badge>220k</ion-badge>
    </ion-item>
</ion-list>
<!-- 第六组 -->
<ion-list>
    <ion-item>第六组</ion-item>
    <ion-item-options side="left">
        <button ion-button>
            <ion-icon name="home"></ion-icon>
        </button>
    </ion-item-options>
</ion-list>
```

### 表格 ion-input
> fixed (input)placeholder floating (none)inline (list->inset)inset  stacked 
```html
<!-- 第一组 -->
<ion-list>
    <ion-item>
        <ion-label fixed>Username</ion-label>
        <ion-input type="text" value=""></ion-input>
    </ion-item>

    <ion-item>
        <ion-label>password</ion-label>
        <ion-input type="password"></ion-input>
    </ion-item>
</ion-list>
<!-- 第二组 -->
<ion-list>
    <ion-item>
        <ion-input type="text" placeholder="Username">
        </ion-input>
    </ion-item>
    <ion-item>
        <ion-input type="password"
        placeholder="Password">
        </ion-input>
    </ion-item>
</ion-list>
<!-- 第三组 -->
<ion-list>
  <ion-item>
    <ion-label floating>Username</ion-label>
    <ion-input type="text" value=""></ion-input>
  </ion-item>
  <ion-item>
    <ion-label floating>Password</ion-label>
    <ion-input type="password" value=""></ion-input>
  </ion-item>
</ion-list>
<!-- 第四组 -->
<ion-list>
  <ion-item>
    <ion-label >Username</ion-label>
    <ion-input type="text" value=""></ion-input>
  </ion-item>
  <ion-item>
    <ion-label >Password</ion-label>
    <ion-input type="password" value=""></ion-input>
  </ion-item>
</ion-list>
<!-- 第五组 -->
<ion-list inset>
  <ion-item>
    <ion-label >Username</ion-label>
    <ion-input type="text" value=""></ion-input>
  </ion-item>
  <ion-item>
    <ion-label >Password</ion-label>
    <ion-input type="password" value=""></ion-input>
  </ion-item>
</ion-list>
<!-- 第六组 -->
<ion-list>
  <ion-item>
    <ion-label stacked>Username</ion-label>
    <ion-input type="text" value=""></ion-input>
  </ion-item>
  <ion-item>
    <ion-label stacked>Password</ion-label>
    <ion-input type="password" value=""></ion-input>
  </ion-item>
</ion-list>
```

### 栅格系统 ion-grid
```html
<ion-grid>
    <ion-row>
        <ion-col col-12>this is a 12
        </ion-col>
        <ion-col col-6>
            <ion-icon name="heard"></ion-icon>
        </ion-col>
    </ion-row>
<ion-grid>
```

### 内容  ion-content
> page与component中自动生成,样式最小高度为屏幕高度，多个page会堆叠删掉
```html
<ion-content></ion-content>
```



## 生命周期
```typescript
  constructor(public navCtrl: NavController) {
    console.log("constructor构造函数执行");
  }

  ionViewDidLoad(){
    console.log('1、ionViewDidLoad 当页面加载时触发，仅在页面创建时触发，如果被缓存，下次打开不触发');
  }
  ionViewWillEnter(){
    console.log("2、ionViewWillEnter 当将要进入页面是触发");
  }
  ionViewDidEnter(){
    console.log("3、ionViewDidEnter 进入页面后触发");
  }
  ionViewWillLeave(){
    console.log("4、ionViewWillLeave 当离开页面是执行");
  }
  ionViewDidLeave(){
    console.log("5、ionViewWillUnload 当离开页面是触发");
  }
  ionViewWillUnLoad(){
    console.log("6、ionViewWillLoad 当页面销毁时页面元素移除时触发");
  }
  ionViewCanEnter(){
    console.log("ionViewCanEnter");
  }
  ionViewCanLeave(){
    console.log("ionViewCanLeave");
  }
```

## 路由

### 路由跳转
> this.navCtrl.push()、this.navCtrl.pop()
```typescript
// 1、引入
import { NavController } from 'ionic-angular';
import { NewPage } from '...'

// 2、注册
constructor(public navCtrl: NavController){};

// 3、使用
// 跳转指定组件
this.navCtrl.push(NewPage,{/* 传参 */});
// 回退
this.navCtrl.pop();
```
### 路由守卫
> ionViewCanEnter、 ionViewCanLeave

需要服务配合，判断是否登录决定能否使用某些组件。

钩子返回值为true：允许进入，或离开

钩子返回值为false: 禁止进入，或离开

## 父子组件通信

### 父组件向子组件传值
> 绑定属性的方式
```html
// 父组件html
<content-child [parentMsg]="parentMsg"></content-child>
```

```ts
// 子组件ts
import { input } from "@angular/core"

@input() parentMsg:string;
```
### 子组件向父组件传值
> 获取子组件dom以及属性方法
```html
// 父组件html
<content-child #contentChild></content-child>
```
```ts
// 父组件ts
import { ViewChild } from '@angular/core'

@ViewChild('contentChild') domContentChild: any;

ionViewDidEnter(){
    this.text = "从子组件中获得"+this.domContentChild.text;
}
```
### 子组件向父组件传值2 待完成
> 发布订阅的形式向父组件传值

## 自定义组件

1、创建组件
``` ts
ionic g component contact-child
```

2、挂载组件到 `component.module.ts` ,并在其中引入对应的模块
```ts
import { NgModule } from '@angular/core';
import { ContactChildComponent } from './contact-child/contact-child';
import { BrowserModule } from '@angular/platform-browser';
import { IonicModule } from 'ionic-angular';
@NgModule({
	declarations: [ContactChildComponent],
	imports: [BrowserModule,IonicModule],
	exports: [ContactChildComponent]
})
export class ComponentsModule {}
```

3、components模块挂载到`app.module.ts`
```ts
import { ComponentsModule } from '../components/components.module';
  imports: [
    ...,  
    ComponentsModule
  ],
```

## 管道

1、创建管道
``` ts
ionic g pipe MenuPipe
```

2、pipes模块挂载到`app.module.ts`
```ts
import { PipesModule } from '../pipes/pipes.module';
  imports: [
    ...,  
    PipesModule
  ],
```

3、在app模块下的组件内使用
```ts
{{ text | memuPipe }}
```

## page
1、创建页面
```ts
// 带module的页面
ionic g page new-page
// 子页面,不带module且到指定目录下创建
ionic g page add-new-page --pagesDir src/pages/new-page --no-module
ionic g page del-new-page --pagesDir src/pages/new-page --no-module
ionic g page edit-new-page --pagesDir src/pages/new-page --no-module
```
2、导出page到new-page.module.ts
```ts
import { NgModule } from '@angular/core';
import { IonicModule } from 'ionic-angular'; // ionic组件
import { BrowserModule } from '@angular/platform-browser'; // ng指令
import { WorkOrderPage } from './work-order'; // 自身页面及各个子页面
import { AddWorkOrderPage } from './add-work-order/add-work-order';
import { DelWorkOrderPage } from './del-work-order/del-work-order';
import { EditWorkOrderPage } from './edit-work-order/edit-work-order';

@NgModule({
  declarations: [
    WorkOrderPage,
    AddWorkOrderPage,
    DelWorkOrderPage,
    EditWorkOrderPage
  ],
  entryComponents: [
    WorkOrderPage,
    AddWorkOrderPage,
    DelWorkOrderPage,
    EditWorkOrderPage
  ],
  imports: [
    IonicModule,
    BrowserModule
  ],
})
export class WorkOrderPageModule {} //导出到app.module.ts
```
3、在app.module.ts中引入WorkOrderPageModule
```ts
import { WorkOrderPageModule } from '../pages/work-order/work-order.module';
```
