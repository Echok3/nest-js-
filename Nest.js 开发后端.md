# Nest.js 开发后端

## 安装及添加路由步骤：

1. 安装环境

   ```bash
   npm i -g @nestjs/cli
   nest new blog
   ```

2. 当前项目文件夹添加 module

   ```bash
   nest g module blog
   ```

3. 当前项目文件夹添加 controller

   ```bash
   nest g controller blog
   ```

   ![2024-04-15 20.48.52](/Users/kelvin.a/Desktop/学习/nest.js后端开发/imgs/2024-04-15 20.48.52.png)

   * 创建和更新了几个文件。

4. 编辑 blog.controller.ts，添加路由内容

   ```bash
   import { Controller,Get} from '@nestjs/common';
   
   @Controller('blog')
   export class BlogController {
   @Get('test')
   test() {
     return 'hello test';
   }
   
   @Get()
     async findAll() {
       return ['a','b','c'];
     }
   }
   ```

   * import 需要添加 Get
   * npm start, http://localhost:3000/blog 和 http://localhost:3000/blog/test  都将显示对应陆游的内容。

5. 设置全局前缀 setGlobalPrefix，可以编辑 main.ts，天际 `app.setGlobalPrefix('/api');`

   ```bash
   import { NestFactory } from '@nestjs/core';
   import { AppModule } from './app.module';
   
   async function bootstrap() {
     const app = await NestFactory.create(AppModule);
   
     app.setGlobalPrefix('/api');
   
     await app.listen(3000);
   }
   bootstrap();
   ```

   * 访问 http://localhost:3000/api/blog/ 显示同样的效果。

---