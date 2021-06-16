# ant-design

## 1. 使用Breadcrumb时@ant-design/icons全量引入的问题

| antd版本  | 4.16.3                                                |
| --------- | ----------------------------------------------------- |
| issue地址 | https://github.com/ant-design/ant-design/issues/31008 |

产生的原因：Menu组件内部引入@ant-design/icons时使用了全量引入，而Breadcrumb组件内部有引用Menu

Breadcrumb.tsx

```tsx
import * as React from 'react';
import classNames from 'classnames';
import toArray from 'rc-util/lib/Children/toArray';
import BreadcrumbItem from './BreadcrumbItem';
import BreadcrumbSeparator from './BreadcrumbSeparator';
import Menu from '../menu'; // 引用Menu
import { ConfigContext } from '../config-provider';
import devWarning from '../_util/devWarning';
import { Omit } from '../_util/type';
import { cloneElement } from '../_util/reactNode';
```

menu/index.tsx

```tsx
import * as React from 'react';
import RcMenu, { Divider, ItemGroup, MenuProps as RcMenuProps } from 'rc-menu';
import classNames from 'classnames';
import omit from 'rc-util/lib/omit'
import { EllipsisOutlined } from '@ant-design/icons'; // 全量引入
// 修改成 import EllipsisOutlined from '@ant-design/icons/EllipsisOutlined'
import SubMenu, { SubMenuProps } from './SubMenu';
import Item, { MenuItemProps } from './MenuItem';
import { ConfigConsumer, ConfigConsumerProps } from '../config-provider';
import devWarning from '../_util/devWarning';
import { SiderContext, SiderContextProps } from '../layout/Sider';
import collapseMotion from '../_util/motion';
import { cloneElement } from '../_util/reactNode';
import MenuContext, { MenuTheme } from './MenuContext';

```

