---
title: Fetching API in react - in the simplest form
date: "2020-05-20T22:40:32.169Z"
description: Fetching a dummy data in the simplest steps
---

State 초기화 → API 불러오기 → API response 를 setState 하기 → response 를 render 하기

### 1 State 초기화

```jsx
constructor(props) {
	super(props);
	this.state = {
		items: [ ],
		isLoaded: false
	}
}
```

### 2 API 불러오고 setState 하기

```jsx
componentDidMount() {
	fetch('https://jsonplaceholder.typicode.com/users')
		.then(res => res.json())
		.then(res => {
			this.setState({
					isLoaded: true,
					items: res,
			})
		})
}
```

### 3. data render 하기

```jsx
<ul>
  {this.state.items.map(item => (
    <li key={item.id}>
      Name: {item.name} | Email: {item.email}
    </li>
  ))}
</ul>
```
