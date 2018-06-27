---
layout: post
title:  "Angular学习(三)" 
---

<br />

新项目开始入坑Anaular6，从看文档开始，挖坑等填...


记录一下学习进度吧，不然感觉每天不知看了点什么，笔记记录的个人认识中可能会有错误，以后不这么菜了再来勘误。、


2018/06/27 组件的双向绑定相关


 > 组件的双向绑定

 * 双向绑定：在组件的html中，在输入控件上使用```<input [(ngModel)]="hero.name" placeholder="name">```来实现双向绑定
 * 想正常使用双向绑定，需要在```app.module.ts```（根模块）文件中，引入```FormsModule```，并在```@NgModule```中声明
 * ```appModule.ts```中，在```@NgModule```中声明用到的模块和组件，使用```declarations```声明用到的模块，使用```imports```声明用到的组件
 * 声明的模块和组件必须要提前```import```进来，类似```import { AppComponent } from './app.component';```和```import { FormsModule } from '@angular/forms';```

 > 集合相关

 * 集合的定义：使用ts文件定义并```export```出一个集合
 * 集合的遍历：前台HTML文件中，使用```<li *ngFor="let hero of heroes">```来完成对集合heroes的遍历，这时，这个```<li>```标签变成宿主元素，```<li></li>```标签包栝着的内容可以调出被遍历的hero对象的属性

 > 事件绑定

 * ```<li *ngFor="let hero of heroes" (click)="onSelect(hero)">```中的```(click)="onSelect(hero)"```就是事件绑定，左边括号内是事件，右边是函数
 * 函数的写法：```onSelect(hero: Hero): void { this.selectedHero = hero; }```

 > IF条件和CSS绑定

 * 使用```<div *ngIf="selectedHero"></div>```包括的内容，当```selectedHero```为空时，该元素将被隐藏，里面可跟表达式
 * ```[class.some-css-class]="some-condition"```：当选择项目满足条件时，应用等号左边的class，不满足条件时，自动移除该class
 * 
