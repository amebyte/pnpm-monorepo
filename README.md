# 从 Vue3 源码入门理解 pnpm 的 monorepo 到以 pnpm 构建 monorepo 方式搭建组件库工程化实战


monorepo 是把多个项目的所有代码放到一个 git 仓库中进行管理，多个项目中会有共享的代码则可以分包引用。整个项目就是有 root 管理的 dependencies 加上多个 packages，每个 package 也可以在自己的作用域引入自己的 dependencies。

为什么要使用 monorepo

使用 monorepo 可以把原本一个项目的多个模块拆分成多个 packages，在 packages 之间相互引用，也可以单独发布成包，极大地解决了项目之间代码无法重用的痛点。在项目打包或者编译操作时也可重用一套配置，通吃所有 packages。

初始化项目生成一个 package.json

```
pnpm init
```

管理多个项目

pnpm 提供的一个功能，可以管理多个项目，那么怎么管理多个项目呢？你需要创建一个配置文件

pnpm-workspace.yaml

在这个配置文件中要告诉 pnpm 项目写在哪个项目下

```json
packages:
  - 'packages/*'
```


```
pnpm install vue -w
```



符号链接



npm 的特点：幽灵依赖



```
pnpm install esbuild typescript minimist -D -w
```



初始化一个 TypeScript 的配置文件

```
pnpm tsc -init
```


```json
{
    "compilerOptions": {
        "outDir": "dist", // 输出的目录
        "sourceMap": true, // 采用sourcemap
        "target": "es2016", // 目标语法
        "module": "esnext", // 模块格式
        "moduleResolution": "node", // 模块解析方式
        "strict": false, // 严格模式
        "resolveJsonModule": true, // 解析json模块
        "esModuleInterop": true, // 允许通过 es6 语法引入common.js模块
        "jsx": "preserve", // jsx 不转义
        "lib": ["esnext", "dom"], // 支持的类库 esnext 及 dom
        "baseUrl": ".",
        "paths": {
            "@vue/*":["packages/*/src"]
        }
    }
}
```




