# vuex-router-sync

<!--
> Effortlessly keep vue-router and vuex store in sync.
-->

vue-router와 vuex store를 손쉽게 동기화 할 수 있습니다.

### Usage

``` bash
# vue-router 최신버전에서만 작동합니다 (2.0 이상)
npm install vuex-router-sync

# vue-router 2.0 이하에서 사용법
npm install vuex-router-sync@2
```

``` js
import { sync } from 'vuex-router-sync'
import store from './vuex/store' // vuex store 인스턴스
import router from './router' // vue-router 인스턴스

sync(store, router) // 완료.

// 애플리케이션 구현부...
```
<!--
You can set a custom vuex module name
-->
vuex 모듈이름을 원하는대로 설정할 수 있습니다.

```js
sync(store, router, { moduleName: 'RouteModule' } )
```

<!--
### How does it work?
-->
### 어떻게 작동하나요?

<!--
- It adds a `route` module into the store, which contains the state representing the current route:
-->

- store에 현재 경로 상태를 포함하는 `route`모듈을 추가합니다.

  ``` js
  store.state.route.path   // 현재 경로 (string)
  store.state.route.params // 현재 파라미터 (object)
  store.state.route.query  // 현재 쿼리 (object)
  ```

<!--
- When the router navigates to a new route, the store's state is updated.
-->

<!--
- **`store.state.route` is immutable, because it is derived state from the URL, which is the source of truth**. You should not attempt to trigger navigations by mutating the route object. Instead, just call `$router.push()` or `$router.go()`. Note that you can do `$router.push({ query: {...}})` to update the query string on the current path.
-->

**`store.state.route`는 URL로부터 상태를 가져왔기 때문에 변하지 않는 값 입니다**. route object를 변경하여 탐색을 시작해서는 안됩니다. 대신, `$router.push()` 또는 `$router.go()`를 호출할 수 있습니다. `$router.push({query: {...}})`를 사용하면 현재 경로의 쿼리 문자열을 업데이트 할 수 있습니다.

<!--
### License
-->
### 라이선스

[MIT](http://opensource.org/licenses/MIT)
