# 1. 'en' => {value: 'en', label: 'English'}

```
const LANGS = [
    { value: 'en', label: 'English' },
    { value: 'ko', label: '한국어' },
];

const lang = 'en';

return R.compose(
    R.defaultTo({}),
    R.find(R.__, LANGS),
    R.propEq('value')
)(lang);
```

### 풀이
위의 코드를 알기쉽게 풀면

<b>R.find(R.propEq('value', lang), LANGS) || {}</b>

LANGS 중에 'value'라는 prop이 lang과 같은 값을 반환하고, 없다면 {}를 반환한다.
