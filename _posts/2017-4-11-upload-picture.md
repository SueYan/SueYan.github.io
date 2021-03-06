---
title: "Ionic2 图片上传"
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

# ionic 图片上传(适用于浏览器)

1.在命令行输入以下代码进行安装:

```
npm install ng2-imageupload --save
```

2.在==app.module.ts==文件夹头部输入:


```
import { BrowserModule } from '@angular/platform-browser';
import { ImageUploadModule } from 'ng2-imageupload';

```

3.在所需文件夹内(图片上传页面)按需输入:


```
import { ImageResult, ResizeOptions } from 'ng2-imageupload';

```

```
@Component({
    selector: 'my-app',
    template: `
      <img [src]="src" [hidden]="!src"><br>
      <input type="file" imageUpload
        (imageSelected)="selected($event)"
        [resizeOptions]="resizeOptions">`
})


export class AppComponent {
    src: string = "";
    resizeOptions: ResizeOptions = {
        resizeMaxHeight: 128,
        resizeMaxWidth: 128
    };



    selected(imageResult: ImageResult) {
        this.src = imageResult.resized
            && imageResult.resized.dataURL
            || imageResult.dataURL;
    }
}
```

> 注意:@Component内的template内容按需编写,可在HTML页面引入.如:

```
<div>
	<img [src]="src">
	<input type="file" imageUpload (imageSelected)="selected($event)" [resizeOptions]="resizeOptions">
</div>
```

> 所需文件夹内(图片上传页面).ts的src路径则为图片路径,例如:

```
src: string = "assets/img/personal.png";
```

