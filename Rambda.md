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

# 2. R.pluck

```jsx
const dummyTeamDatas = [
    { name: 'Adriel' },
    { name: 'Adriel_US' },
    { name: 'Adriel_KR' },
    { name: 'Adriel_JP' },
];

R.pluck('name', dummyTeamDatas)

// returns
// ["Adriel", "Adriel_US", "Adriel_KR", "Adriel_JP"]
```

# 3. R.filter, R.both, R.propEq, R.compose

```jsx
R.filter(
    R.both(
        R.propEq('name', name),
        R.compose(R.not, R.propEq('id', id))
    ),
    this.dummyTeamDatas
)
```

filter(조건, 배열) ⇒ 조건에 맞는 배열

filter(propEq('키', 벨류), 오브젝트배열) ⇒ 오브젝트 중 키가 벨류인 것

both(A, B) ⇒ A&&B

# 4. R.zipObj

```jsx
const numArr = [1, 2, 3];
const alphaArr = ['a', 'b', 'c'];

R.zipObj(numArr, alphaArr)

// returns
// {1: 'a', 2: 'b', 3: 'c'}
```

# 5. R.pathOr

```jsx
const memObj = {
	member: {
		team: ['teamA', 'teamB']
	}
}

const memObj2 = {
	member: {
		name: ['hihi']
	}
}

R.pathOr([], ['member', 'team'], memObj)
R.pathOr([], ['member', 'team'], memObj2)

// returns
// ['teamA', 'teamB']
// []
```

# 6. R.map, R.assoc

```jsx
const data = [
	{ name: 'a' },
	{ name: 'b' },
	{ name: 'c' },
	{ name: 'd' },
];

R.map(R.assoc('isActive', false), data)

// returns
// [
//	{ name: 'a', isActive: false },
//	{ name: 'b', isActive: false },
//	{ name: 'c', isActive: false },
//	{ name: 'd', isActive: false },
// ];
```
