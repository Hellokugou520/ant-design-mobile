# Migrating from v2

v5 is a completely rewritten version, so there are lots of differences between v2 and v5. Actually, this shouldn't be called as "migration". It's about replacing one component library with another one.

In order to reduce the cost of migration, you can try to use some methods mentioned below to make v2 and v5 live alongside in your project at the same time.

### Method 1: Use antd-mobile-v2

We have published a shadow npm package for v2 which is name as `antd-mobile-v2`. You can replace the v2 antd-mobile package in your project with this one.

First, install `antd-mobile-v2`:

```bash
$ npm install --save antd-mobile-v2
# or
$ yarn add antd-mobile-v2
```

And then, replace everything that uses `antd-mobile` with `antd-mobile-v2`. For example:

```jsx
import {Button} from 'antd-mobile'
// ⬇️
import {Button} from 'antd-mobile-v2'
```

Next, remove the old `antd-mobile` dependency. And try to run/test/build your project. Check if everything is working fine.

Finally, reinstall the `antd-mobile` package as v5:

```bash
$ npm install --save antd-mobile@next
# or
$ yarn add antd-mobile@next
```

Now, the `antd-mobile` in project is v5, and `antd-mobile-v2` is v2.

### Method 2: Install v5 via alias

We recommend you to use the method 1. Although it requires a little bit migration work, it can make the whole migration process less costly and more steady.

Of course, in case your project doesn't seem to be suitable to use method 1, we provided a backup plan for you.

You can use npm alias to install v5:

```bash
$ npm install --save antd-mobile-v5@npm:antd-mobile@next
# or
$ yarn add antd-mobile-v5@npm:antd-mobile@next
```

And after that, the corresponding `package.json` is:

```json
{
  "antd-mobile": "^2.3.2",
  "antd-mobile-v5": "npm:antd-mobile@next"
}
```

Now, `antd-mobile` is v2 and `antd-mobile-v5` is v5.

```js
import { Button } from 'antd-mobile' // v2
import { Button } from 'antd-mobile-v5' // v5
```

Need to be noted, not every package manager has a well support for npm alias.
