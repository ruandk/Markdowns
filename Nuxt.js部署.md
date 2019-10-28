# Nuxt.js SSR服务端渲染

## 一、安装

    确保安装了npx（npx在NPM版本5.2.0默认安装）

    ```shell
    npx create-nuxt-app <project-name>
    
    cd <project-name>
    
    npm run dev
    ```

    应用现在运行在 http://localhost:3000

## 二、开发
    
    开发跟平时开发Vue SPA 项目几乎一样，注意下Nuxt.js的一些默认规则

    [目录结构](https://zh.nuxtjs.org/guide/directory-structure)
    
    [配置](https://zh.nuxtjs.org/guide/configuration)
    
    [路由](https://zh.nuxtjs.org/guide/routing)
    
    [Vuex](https://zh.nuxtjs.org/guide/vuex-store)
    
## 三、[部署](https://zh.nuxtjs.org/guide/commands)
    
    ### 1.打包

    ```shell
    npm run build
    ```
    
    ### 2.将以下文件或目录上传至服务器

    .nuxt/          (打包后的项目)
    nuxt.config.js  (nuxt配置文件)
    package.json    (包管理配置)
    server/         (启动服务)
    static/         (静态文件)

    ### 3.安装依赖并启动服务

    ```shell
    cnpm i

    nohup npm run start &   #服务端后台运行

    exit                    #运行后不可直接关闭远程连接客户端
    ```

    ### 4.注意
    
    阿里云安全组配置规则允许访问对应端口

    nuxt.config.js文件中配置，否则无法被外网访问
    server: {
        port: 8000, // default: 3000
        host: '0.0.0.0' // default: localhost
    }