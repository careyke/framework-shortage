# ESlint配置问题

## 1. eslint-config-prettier包版本问题

`eslint-config-prettier`包当升级到 ^8 之后的版本时，会导致eslint失效。降低到 `^7` 版本之后正常工作

eslint相关的配置：

```json
"@typescript-eslint/eslint-plugin": "^4.14.1",
"@typescript-eslint/parser": "^4.14.1",
"eslint": "^7.19.0",
"eslint-config-prettier": "^7.2.0",
"eslint-plugin-prettier": "^3.3.1",
"eslint-plugin-react": "^7.22.0",
"eslint-plugin-react-hooks": "^4.2.0",
"lerna": "^4.0.0",
"prettier": "^2.2.1",
"typescript": "4.1"
```

