# 1. 리스트 아이템 (List Item Memorize)

<img src="./app.gif" width="200"> <img src="./app2.gif" width="200">


```
import React, {memo} from 'react';

const ListItem = () => {
    ...
    return ...
}

const equalCheck = R.both(
    R.eqBy(R.path(['item', 'id'])), 
    R.eqProps('metricOption')
);


export default memo(ListItem, equalCheck);
```

### 풀이
우리회사 같은 경우 여러가지 채널에서 `실시간으로 응답을 받아서 보여주기` 때문에 데이터가 바뀔 때 마다 그때마다 리렌더링을 해주면 UI가 버벅댄다. 이럴 땐 새로 랜더링할 필요가 없는 경우를 알려주면 memorize된 아이템을 그대로 보여준다.

