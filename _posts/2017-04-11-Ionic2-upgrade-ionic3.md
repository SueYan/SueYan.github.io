---
title: "Ionic2 升级 Ionic3"
header:
  image: /assets/images/ionic-header.jpg
  caption: "Photo credit: [**Ionic**](https://ionic.io)"
categories:
  - Ionic 2
tags:
  - Ionic 3
  - Ionic 2
  - Angular 2
  - Hybird App
---

1.首先更新==package.json==, 按照以下的代码相应替换你package.json里面的代码, 并且把你项目根目录下的==node_modules==文件夹删除掉, 然后运行npm install (如果你是用淘宝镜像可以运行 cnpm install)

```json
"dependencies": {
    "@angular/common": "4.0.0",
    "@angular/compiler": "4.0.0",
    "@angular/compiler-cli": "4.0.0",
    "@angular/core": "4.0.0",
    "@angular/forms": "4.0.0",
    "@angular/http": "4.0.0",
    "@angular/platform-browser": "4.0.0",
    "@angular/platform-browser-dynamic": "4.0.0",
    "@ionic-native/core": "3.4.2",
    "@ionic-native/splash-screen": "3.4.2",
    "@ionic-native/status-bar": "3.4.2",
    "@ionic/storage": "2.0.1",
    "ionic-angular": "3.0.1",
    "ionicons": "3.0.0",
    "rxjs": "5.1.1",
    "sw-toolbox": "3.4.0",
    "zone.js": "^0.8.4"
},
"devDependencies": {
  "@ionic/app-scripts": "1.3.0",
  "typescript": "~2.2.1"
}
```

2.第二步你需要在==app/app.module.ts==文件里面引入BrowserModule和HttpModule
首先需要在头部引入这两个module (如果你的APP不使用HTTP可以不引入HttpModule)

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { HttpModule } from '@angular/http';
```
在同一个文件里面找到imports并且加入BrowserModule和HttpModule

```typescript
imports: [
  BrowserModule,
  HttpModule,
  IonicModule.forRoot(MyApp)
],
```
3.在==app.component.ts==文件夹里面修改以及添加以下代码:

```typescript
import { StatusBar } from '@ionic-native/status-bar';
import { SplashScreen } from '@ionic-native/splash-screen';



@Component({
  templateUrl: 'app.html',
  providers: [SplashScreen, StatusBar]
})


constructor(platform: Platform, private splashScreen: SplashScreen, private statusBar: StatusBar) {
    platform.ready().then(() => {
      this.statusBar.styleDefault();
      this.splashScreen.hide();
    });
  }
```
4.然后在命令行分别执行以下4段代码(一定要分别执行):

```
ionic plugin add cordova-plugin-statusbar

npm install --save @ionic-native/status-bar

ionic plugin add cordova-plugin-splashscreen

npm install --save @ionic-native/splash-screen
```
