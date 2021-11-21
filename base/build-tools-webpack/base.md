### webpack
1、核心知识: entry、output、loader、plugin、devserver、hmr、--watch
- 安装webpack、webpack-cli、webpack-dev-server
- 新建文件 npm init -y
- webpack.config.js ：工作项目中需要区分正式和测试环境
- 命令行
  - 启动webpack ： --watch
  - 开发环境热更新：webpack serve / webpack --watch(手动刷新) / webpack-middleware-plugin
- 核心功能
  - 解析js：babel-loader、@babel/core、
    - 解析js新语法：@babel/polyfill+core-js3，配置useBuiltIns entry/false/usage (存在全局污染)/ @babel/plugin-transform-runtime + @babel/runtime-corejs3 (解析的新语法展示:_babel_runtime_corejs3_core_js_stable_instance_map__WEBPACK_IMPORTED_MODULE_0___default())
  - 解析css: less-loader(less转为css)、 css-loader（将css变为commonjs）、 style-loader(将css加入脚本)、postcss-loader包含autoprefix（处理css）
  - 解析图片：type:asstes/resource [webpack5]、url-loader[webpack4]
  - 解析html: html-webpack-plugin 模版
  - 自动更新：devServer (将输入的模版，监听后bundle在内存中更新)
  - 热更新：1、devserver 2、hot3、webpack.HotModuleReplacementPlugin 4、js加hot.module更新的模块
  - 
2、高级
- 开发环境：devServer、sourceMap、proxy
- 生产环境：treeShaking、压缩、提取公共代码
- webpack-merge
- tree shaking:es6 module + mode:production;loadsh-es (支持es6语法)
- sourceMap: cheap-module-source-map  \ eval-cheap-module-source-map 
- js优化；全局引入 webpack.ProvidePlugin
  - entry：
  - webpackChunkName：动态加载，按需加载
  - splitChunks: 提取公共代码
- css优化:
  - 分开打包：mini-css-extract-plugin 将css打包到另一个文件
  - 压缩：css-minimizer-webpack-plugin ，但js压缩规则会被破坏，引入terser-webpack-plugin
- 包体积分析：webpack-bundle-analyzer
- 获取参数：yargs
### 问题
- npm ERR! code EACCES && sudo chown -R 501:20 "/Users/lipeijuan/.npm" 
  - root用户和普通用户，文件的归属 ？