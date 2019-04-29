---
title: 根据不同的环境打包（npm run build -- xx)
---
1> build.js 文件添加
```
process.env.NODE_ENV = process.argv.splice(2)[0] == 'dev'? 'develop':'production'
```

2> prod.env.js & dev.env.jd 文件添加在生产或开发环境需要添加的变量
```
DROP_DEBUGGER: true,
DROP_CONSOLE: true
```

3> webpack.prod.conf.js 中添加判断 & 配置参数
(1)

     let env = require('../config/prod.env')
      if (process.env.NODE_ENV == 'develop') {

         env = require('../config/dev.env')

      }
      console.log("----");
      console.log(env.DROP_CONSOLE);


      //让打包的时候输出可配置的文件
      var GenerateAssetPlugin = require('generate-asset-webpack-plugin'); 
      var createServerConfig=function(compilation){
          //  console.log("info from GenerateAssetPlugin:");
          //  console.log(compilation);
          let cfgJson={ApiUrl:"http://10.0.0.200:18080"};
          return JSON.stringify(cfgJson);
      }

      new UglifyJsPlugin({

         uglifyOptions: {

           compress: {

             warnings: false,

             drop_debugger: env.DROP_DEBUGGER,

             drop_console: env.DROP_CONSOLE

           }

        },

        sourceMap: config.build.productionSourceMap,

        parallel: true

     }),










