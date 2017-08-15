## eslint 规范示例
> package.json 里的 pre-commit 命令暂时注释掉了，使用例子前记得删掉注释

为了方便对比，添加了两个 npm scripts 命令，分别为 lint 和 lint:fix

建议使用者打开 src/index.js 观察 lint 和 lint:fix 操作前后变化

使用 lint:fix 会自动修复大部分错误，每次 git commit 前进行 lint:fix 检查

## 结合 webpack 使用

添加 rules
```js
{
  test: /\.(js|jsx)$/,
  loader: 'eslint-loader',
  enforce: 'pre',
  include: [path.join(__dirname, 'src')],
  options: {
    formatter: require('eslint-friendly-formatter')
  }
}
```

这段配置的意思是在 webpack 打包前进行 eslint 检测，检测 src 目录下的 .js | .jsx 结尾的文件

[`eslint-friendly-formatter`](https://www.npmjs.com/package/eslint-friendly-formatter)插件提供 sublime 等插件点击错误跳转到文件功能
