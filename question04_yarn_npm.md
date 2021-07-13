# yarn and npm



## 1. 第三方包的peerDependencies中依赖包的版本不对称

1. yarn中对于这种情况不会报错，只会报警告

2. npm install时，会直接报错，中断整个流程。

   ```shell
   # 解决方案
   npm install --legacy-peer-deps 
   # 或
   npm install --force
   ```

这种情况一般是第三方包没有及时更细依赖版本，可以给作者提pr或issue。对于没有人维护的包，应该要考虑更换其他包