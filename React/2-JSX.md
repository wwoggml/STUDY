# JSX


<br>

```
๐ก JSX๋ ์๋ฐ์คํฌ๋ฆฝํธ์ ๋ฌธ๋ฒ์ ํ์ฅํ ๊ฒ์ผ๋ก JavaScript์ XML/HTML์ ํฉ์น ๊ฒ์ด๋ค.
```

<br>

## JSX ์ฝ๋ ์์ 

```
const element = <h1>Hello World!</h1>;
```

๋์ ์ฐ์ฐ์ =์ ์ผ์ชฝ์ ```์๋ฐ์คํฌ๋ฆฝํธ``` ๋ฌธ๋ฒ, ๋์ ์ฐ์ฐ์ =์ ์ค๋ฅธ์ชฝ์ ```HTML``` ๋ฌธ๋ฒ์ด๋ค.

```const element``` ๊น์ง๋ ์๋ฐ์คํฌ๋ฆฝํธ ๋ฌธ๋ฒ, ```<h1>Hello World!</h1>``` ๋ HTML ๋ฌธ๋ฒ์ด๋ค.

โ ```<h1>```ํ๊ทธ๋ก ๋๋ฌ์ธ์ธ ๋ฌธ์์ด์ element๋ผ๋ ๋ณ์์ ์ ์ธ

JSX๋ ๋ด๋ถ์ ์ผ๋ก XML/HTML ์ฝ๋๋ฅผ ์๋ฐ์คํฌ๋ฆฝํธ๋ก ๋ณํํ๋ ๊ณผ์ ์ ๊ฑฐ์น๋ค. ๋ฐ๋ผ์ ์ค์ ๋ก JSX ์ฝ๋๋ฅผ ์์ฑํด๋ ์ต์ข์ ์ผ๋ก๋ ์๋ฐ์คํฌ๋ฆฝํธ ์ฝ๋๊ฐ ๋์ค๊ฒ๋๋ค.

<br>

JSX ์ฝ๋๋ฅผ ์๋ฐ์คํฌ๋ฆฝํธ ์ฝ๋๋ก ๋ณํํ๋ ์ญํ ์ ํ๋ ๊ฒ์ด ๋ฆฌ์กํธ์ ```createElement()``` ํจ์์ด๋ค.

```jsx
class Hello extends React.Component {
	render() {
		return <div> Hello {this.props.toWhat} </div>;
	}
}

ReactDOM.render (
	<Hello toWhat="World" />,
	document.getElementById('root')
);
```

Hello๋ผ๋ ๋ฆฌ์กํธ ์ปดํฌ๋ํธ์ด๋ค.

์ด ์ปดํฌ๋ํธ ๋ด๋ถ์์๋ ์๋ฐ์คํฌ๋ฆฝํธ ์ฝ๋์ HTML ์ฝ๋๊ฐ ๊ฒฐํฉ๋ JSX๋ฅผ ์ฌ์ฉํ๊ณ  ์๋ ๊ฒ์ ๋ณผ ์ ์๋ค.

๊ทธ๋ฆฌ๊ณ  ์ด ์ปดํฌ๋ํธ๋ฅผ ReactDOM์ ```render()``` ํจ์๋ฅผ ์ฌ์ฉํ์ฌ ์ค์  ํ๋ฉด์ ๋ ๋๋งํ๊ณ  ์๋ค.


<br>


```jsx
class Hello extends React.Component {
	render() {
		return React.createElement('div', null, `Hello ${this.props.toWhat}`);
	}
}

ReactDOM.render (
	React.createElement(Hello, { toWhat: 'World' }, null),
	document.getElementById('root')
);
```

์ด ์ฝ๋๋ JSX๋ฅผ ์ฌ์ฉํ์ง ์๊ณ  ์๋ฐ์คํฌ๋ฆฝํธ ์ฝ๋๋ง ์ฌ์ฉํ ์ฝ๋๋ก ์ ์ฝ๋์ ๋์ผํ ๊ธฐ๋ฅ์ด๋ค.

์์์ JSX๋ฅผ ์ฌ์ฉํ๋ ๋ถ๋ถ์ด ์ด ์ฝ๋์์๋ ```React.createElement()``` ํจ์๋ก ๋์ฒด๋์๋ค.


<br>


```createElement()``` ํจ์์ ํ๋ผ๋ฏธํฐ๋

```jsx
React.createElement(
	type,
	[props],
	[...children]
)
```

* type : element์ ์ ํ
  * ex) ```<div>, <span>``` ๋ฑ HTML ํ๊ทธ ๋๋ ๋ค๋ฅธ ๋ฆฌ์กํธ ์ปดํฌ๋ํธ
* props : element์ ์์ฑ
* children : ํ์ฌ element๊ฐ ํฌํจํ๊ณ  ์๋ ์์ element


<br>
<br>

## JSX ์ฅ์ 

### 1๏ธโฃย  ์ฝ๋๊ฐ ๊ฐ๊ฒฐํด์ง๋ค.

- **JSX ์ฌ์ฉํ ๊ฒฝ์ฐ**
```<div>Hello, {name} </div>```


- **JSX ์ฌ์ฉ ์ ํ ๊ฒฝ์ฐ**
```React.createElement('div', null, `Hello, ${name}`);```


<br>


### 2๏ธโฃย  ๊ฐ๋์ฑ์ด ํฅ์๋๋ค.

JSX๋ฅผ ์ฌ์ฉํ ๊ฒฝ์ฐ๊ฐ ์ํ ๊ฒฝ์ฐ๋ณด๋ค ์ฝ๋์ ์๋ฏธ๊ฐ ๋ ๋น ๋ฅด๊ฒ ์๋ฟ๋๋ค.


<br>



### 3๏ธโฃย  Injection Attact ์ด๋ผ๋ ํดํน์ ๋ฐฉ์ดํ์ฌ ๋ณด์์ฑ์ด ์ฌ๋ผ๊ฐ๋ค.

Injection Attack : ์๋ ฅ์ฐฝ์ ๋ฌธ์๋ ์ซ์ ๊ฐ์ ์ผ๋ฐ์ ์ธ ๊ฐ์ด ์๋ ์์ค์ฝ๋๋ฅผ ์๋ ฅํ์ฌ ํด๋น ์ฝ๋๊ฐ ์คํ๋๋๋ก ๋ง๋๋ ํดํน ๋ฐฉ๋ฒ



<br>
<br>


## JSX ์ฌ์ฉ๋ฒ

```jsx
const name = "js";
const element = <h1>์๋, {name}</h1>;

ReactDOM.render (
	element,
	document.getElementById('root')
);
```

XML/HTML ์ฝ๋๋ฅผ ์ฌ์ฉํ๋ค๊ฐ ์ค๊ฐ์ ์๋ฐ์คํฌ๋ฆฝํธ ์ฝ๋๋ฅผ ์ฌ์ํ  ๊ฒฝ์ฐ ์ค๊ดํธ{}๋ฅผ ์ฌ์ฉํด์ ๋ฌถ์ด์ฃผ๋ฉด ๋๋ค.


<br>

```jsx
function formatName(user) {
	return user.firstName + ' ' + user.lastNamse;
}

const user = {
	firstName: 'Inje',
	lastName: 'Lee'
};

const element = (
	<h1>
			Hello, {formatName(user)}
	</h1>
);

ReactDOM.render (
	element,
	document.getElementById('root')
);
```

์ ์ฝ๋์์ ์ค๊ดํธ{}๋ฅผ ์ฌ์ฉํ์ฌ ์๋ฐ์คํฌ๋ฆฝํธ ํจ์๋ฅผ ํธ์ถํ์ฌ ์ฌ์ฉํ๋ค.


<br>


### HTML ํ๊ทธ์ ์์ฑ์ ๊ฐ์ ๋ฃ๊ณ  ์ถ์ ๋

- ํฐ ๋ฐ์ดํ ์ฌ์ด์ ๋ฌธ์์ด์ ๋ฃ๊ฑฐ๋

```const element = <div tabIndex=โ0โ></div>;```

- ์ค๊ดํธ ์ฌ์ด์ ์๋ฐ์คํฌ๋ฆฝํธ ์ฝ๋๋ฅผ ๋ฃ๋๋ค.

```const element = <img src={user.avatarUrl}></img>;```


<br>


### children ์ ์ํ๊ธฐ

```jsx
const element = (
	<div>
		<h1>์๋ํ์ธ์</h1>
		<h2>์ด์ฌํ ๋ฆฌ์กํธ๋ฅผ ๊ณต๋ถํด ๋ด์๋ค! </h2>
	</div>
);
```

์ ์ฝ๋์์ ```<div>``` ํ๊ทธ์ children์ ```<h1>๊ณผ <h2>``` ํ๊ทธ์ด๋ค.

๐[์ปดํฌ๋ํธ](https://github.com/kimjaehee18/STUDY/blob/main/React/3-Component.md)
