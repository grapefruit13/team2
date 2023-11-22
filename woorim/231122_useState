# useState 참조형

# 리액트의 State

리액트는 state(상태)가 바뀔 때마다 화면을 새롭게 그려내는 방식으로 동작한다. 리액트의 state(상태)를 생성하고 바꾸기 위해 사용하는게 useState 함수이다.

# useState

useState를 사용하기 위해서는 아래 예시처럼 import 문을 작성하고, 변수를 destructuring 방법으로 선언하면 된다.

```jsx
import { use State } from 'react';

// ...

const [state, setState] = useState(0);
```

여기서 state라는 변수는 state 값을 말하고, setState는 state에 값을 넣을 때(값을 바꿀 때) 사용하는 함수이며, useState() 괄호 안에 원하는 값을 넣어서 state의 초기값을 설정할 수 있다. 

# 참조형 State

- 배열이나 객체같은 ******참조형 타입******의 state를 변경할 때는, 반드시 새로운 값을 만들어서 state를 변경해야 한다.

## 예시 코드

```jsx
const [gameHistory, setGameHistory] = useState([]);
```

- 위 코드는 gameHistory라는 state를 생성해 초기값으로 빈 배열을 넣어주고, setter함수로는 setGameHistory를 정해준다.

여기에서 gameHistory라는 변수가 배열 임에 주목하고, gameHistory에 값을 추가한다고 가정해보자.

## 잘못된 코드

```jsx
const handleRollClick = () => {
    const nextNum = random(6);
    setNum(nextNum);
		gameHistory.push(nextNum);
		setGameHistory(gameHistory);
```

- 위에서는 gameHistory가 참조하고 있는 배열에 nextNum을 마지막 인덱스로 추가해주고 있다. 그리고 그 배열을 setter 함수를 통해 state를 변경해주고 있는 것 같지만. 잘못된 코드이다.
- state는 배열값 자체를 가지고 있는 게 아니라, 배열의 주소값을 참조하고 있기 때문에, push 메소드로 배열 안의 요소를 변경했더라도 결과적으로 참조하는 배열의 주소값은 변경된 것이 아니게 된다.
- 그럼 리액트 입장에서 state가 참조하는 주소값은 여전히 똑같기 때문에 상태가 바뀌었다고 판단하지 않아, 렌더링 되지 않는다 = 화면에 변경한 배열이 반영되지 않는다.

## 올바른 코드

```jsx
	const [gameHistory, setGameHistory] = useState([]);
	const handleRollClick = () => {
    const nextNum = random(6);
    setNum(nextNum);
    setSum(sum + nextNum);
    setGameHistory([...gameHistory, nextNum]);
  };
```

- 배열의 state를 변경하기 위해서는, … 스프레드 연산자를 사용하여 gameHistory가 참조하고 있는 주소값에 존재하는 배열을 복사하고, 그 배열에 값을 추가해서 state를 변경해주어야 한다.
