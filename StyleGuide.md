Style Guide for React-Native
===
***
## Naming Conventions
```javascript
/* Folder Name */
//no
Images
//yes
images

/* File Name */
//no
mainview, Mainview, main_view
//yes
MainView
```
- 폴더명은 소문자로, 파일명은 파스칼 형식으로(단어의 첫문자가 대문자)
- 폴더명과 동일한 이름의 파일명은 사용하지 않도록한다.
  + ex) user/form/Form.js -> user/form/UserForm.js

```javascript
/* Class Import */
import {View, ListView, Alert } from 'react-native';
```
- 같은 모듈로부터의 import는 한줄에 작성한다.
- 공백은 import뒤, 모든 모듈 뒤, from의 양옆으로 한다.
- Class의 이름은 폴더명과 동일한 형식을 띈다.
```javascript
/* Variable and Object */
var textExample = "Hello World";
```
- 세미콜론을 붙이는 것을 규칙으로 한다.
- Variable과 Object는 Camel 형식으로 한다.(첫문자 소문자, 단어의 첫문자는 대문자)
***
## Layout Conventions
```javascript
const {loading } = this.state;
const {label, scroll, dropdown, disabledLabel } = styles;
const datasources = this.buildDataSource();

//And

if (!this.state.isSelctionChange){
  this.props.selectedIndex.punchIndex = 0;
  this.props.selectedIndex.jobIndex = 0;
}
```

- state를 이용해야 하는 경우 class로 그 외에는 functional을 이용한다.
- React Component의 Render() 내부에선 setState()를 호출하지 않는다.
- 줄 바꿈이 필요한 라인(Continuation Lines)의 경우 indent(2 space)를 넣어준다.
- Method와 Property 선언 뒤에는 꼭 한 줄의 빈 라인을 넣어준다.
- 비슷한 모양의 선언이나 동일선상의 작업중에는 빈 라인을 넣지 않는다.

```javascript
//Before
class Button extends Component {
  constructor(props) {
    super(props);
    this.state = { clicked: false };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({ clicked: true });
  }
  render() {
    return <button onClick={this.handleClick}>Click Me!</button>;
  }
}

//After
class Button extends Component {
  state = { clicked: false };
  handleClick = () => this.setState({ clicked: true }); render() {
    return <button onClick={this.handleClick}>Click Me!</button>;
  }
}
```
- Arrow function을 클래스 인스턴스로 정의하고, 고유의 스코프(변수 범위)가 없도록 한다.
- Constructor의 내부에서 바인드를 하지 않아도 되도록 할 수 있다.
- 이로서 Constructor의 사용을 최대한 자제한다.

```javascript
//Before
function todoApp(state = initialState, action) {
  switch (action.type) {
    case SET_VISIBILITY_FILTER: return Object.assign({}, state, {
      visibilityFilter: action.filter
    });
    default: return state;
  }
}

//After
function todoApp(state = initialState, action) {
  switch (action.type) {
    case SET_VISIBILITY_FILTER:
      return { …state, visibilityFilter: action.filter };
    default: return state;
  }
}
```
- Object 사용에 있어서 Array Spread Operator를 사용한다.

```java
//Before
<Welcome ref=”myRef” />

//After
<Welcome ref={(ref) => { this.myRef = ref; }} />
```
```javascript
shouldComponentUpdate(nextProps, nextState) {
  if (this.props.color !== nextProps.color) { //By using immutable library we can avoid deep comparison of objects as well
    return true;
  }
  if (this.state.count !== nextState.count) {
    return true;
  }
  return false;
}
```
- Render 시에 퍼포먼스를 향상시킬 수 있는 함수이다.
- 이외에는 기본적으로 ES6의 feature들을 따른다.
- [Airbnb ES6 Style Guide](https://github.com/airbnb/javascript#types--primitives)
***
## Commenting Conventions
```javascript
/* Comments */

//no
if(a == b)
{
  a = a+b; // add b to a
}

//yes
if(a == b)
{
  a = a+b;
  // Add a to b.
}
```
- 코드 위 새로운 줄에 주석을 단다.
- 클래스, 함수 설명을 위한 주석만 여러줄 주석을 이용하여 작성한다.
- 주석의 첫문자는 대문자로하고, 문장으로 끝내도록한다.
***
## Language Conventions
```javascript
// avoid
let message = "Hello!";
message = 123;
```
- 같은 변수에 여러가지 데이터 타입을 사용하는 것은 최대한 피한다.
```javascript
// Default
let message = "Hello,";
let messageWithVariable = `${message} World!`
```
- 쌍따옴표를 사용하는 것을 기본으로 한다.
- 문장 내에 쌍따옴표가 필요한 경우 backtricks를 사용한다.
```javascript
/* Array */

//no
let arr = new Array();
//yes
let arr = [];
```
