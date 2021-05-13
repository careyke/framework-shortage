# vite一些影响使用的问题

## 1. vite和qiankun的兼容

`vite`在开发模式下无法打包成`umd`格式，对于调试`qiankun`子应用不友好



## 2. vite热更新问题(*)

在React应用中，保存某个组件的文件时，即使没有更新，vite也会更新这个组件，而且本次更新会触发`ignorePreviousDependencies`模式，也就是`useEffect、useCallback和useMemo`的判断条件无效，会强制更新。

但是问题是只有当前组件是`ignorePreviousDependencies`模式，其后代组件并不会。在某些情况下，后代组件和当前组件有数据依赖，会导致页面更新错误。

> ignorePreviousDependencies是React内部的属性，用来`hot reload`组件
>
> 对应代码可以看[这里](https://github.com/facebook/react/blob/46491dce96e6a151706f51494edfd3cb7f09ed7f/packages/react-reconciler/src/ReactFiberHooks.new.js#L370)

