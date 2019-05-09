# React Projects

## Like/Dislike Component

![](https://lh4.googleusercontent.com/gcRnGn8UoEXIsIlif94tvW7EcHcDgFZm1HIkQUogztQ_qJa8cdLLtcJTbln4u8QgE2k4zjlyq0RgLhJcVlNwBLTKhOmoaJCYsD_dR2pYQMWIC9-aegXUoqZiZPljiwyUj2-E31sL7emNu07e5g)

![](https://lh6.googleusercontent.com/vxGQFzPIY4UcMeJkgOskpRB5c_Nx5No-Ruurd7Xi80V2Snieq-LgTH9-aPtCzb89WHgS_ijZkLJ94IbEfOMqNmy9yyaK2KEIZSUSc27sKfYbHYWvG7iMP9cmGzENB2zuLUn3zVMBo5uroidauA)

```jsx
import cx from 'classnames';
import React, { Component } from 'react';

export default class LikeDislike extends Component {

  state = {
      likes:100,
      dislikes:25,
      isLike: false,
      isDislike: false
  };
  
  like = () => {
    if (this.state.isLike){
      this.setState({
        likes:this.state.likes-1,
        isLike:false
      });
    } else {
        if (this.state.isDislike){
          this.setState({
              likes:this.state.likes+1,
              dislikes:this.state.dislikes-1,
              isDislike:false,
              isLike:true
          });
        } else {
          this.setState({
              likes:this.state.likes+1,
              isLike:true
          });
        }
    }
  }
  
  dislike = () => {
    if(this.state.isLike){
      this.setState({
        likes:this.state.likes-1,
        dislikes:this.state.dislikes+1,
        isDislike:true,
        isLike:false
      });
    } else if(this.state.isDislike){
      this.setState({
        dislikes:this.state.dislikes-1,
        isDislike:false
      });
    } else {
      this.setState({
        dislikes:this.state.dislikes+1,
        isDislike:true
      });
    }
  }
  
  render() {
	let likeBtnClass = cx({
		'like-button': true,
		liked: this.state.isLike
    });

    let dislikeBtnClass = cx({
		'dislike-button': true,
		disliked: this.state.isDislike
    });

    return (
      <div>
        <div>
          <button className = {likeBtnClass}></button>
          <button className = {this.state.isLike?"like-button liked":"like-button"} onClick = {this.like}>Like | <span className = "likes-counter">{this.state.likes}</span></button>
          <button className = {this.state.isDislike?"dislike-button disliked":"dislike-button"} onClick = {this.dislike}>Dislike | <span className = "dislikes-counter">{this.state.dislikes}</span></button>
        </div>
        <style>{`
          .like-button, .dislike-button {
            font-size: 1rem;
            padding: 5px 10px;
            color:   #585858;
          }
          .liked, .disliked {
            font-weight: bold;
            color: #1565c0;
          }
        `}</style>
      </div>
    );
  }
}
```

## Counter Component

![](https://lh4.googleusercontent.com/lmUWF6xlKd06uAfcb3_njwVRD5Koq8vFlaDYHakAPT5cU-fMb4Tw7eK4UoisAgSlPA_7w4QU2dB7fFCTIjkfyEHEbaTvRw27jitp44BveUczEuVHO7DumzhWGdsd51yn2DusmPigE4cGbAgjJA)

```javascript
import cx from 'classnames';
import { Component } from 'react';

export default class Counter extends Component {
	constructor(props){
    	super(props);
    	this.state = {
        	coun:42
    	}
	}
    
	add = () => {
    	this.setState({
        	coun : this.state.coun + 1
    	})
	}
    
	render() {
    	return (
        	<div>
                <h2 className = "counter">{this.state.coun}</h2>
                <button className ="counter-button" onClick={this.add}>Click</button>
            	<style>{`
                	.counter-button {
                    	font-size: 1rem;
                    	padding: 5px 10px;
                    	color:  #585858;
                	}
            	`}</style>
        	</div>
    	);
	}
}
```

## Walmart Checkout Component

![](../.gitbook/assets/image%20%281%29.png)

> [https://codesandbox.io/s/0qqwjkryq0](https://codesandbox.io/s/0qqwjkryq0)

## Chinese Restaurant App

![](https://lh3.googleusercontent.com/Az3GaKpOVjNSG-VCe-KFMwAGu9ivcNKf-RHpVAz9V7cF0hObiwJSTztpgdmQJnNpOaTQa9PaCrwVyO_bWrek0tFPR3ks9DtE0pK1XXWTZ3xkfmYnhf5_chZZD4cggKVubtQrcbHx)

> [https://github.com/wenjun9/Menu](https://github.com/wenjun9/Menu)

## Quiz Reducer Problem 

When this form is submitted, you should render additional text at the top of the page that says "You selected: the text for the answer they selected" and below that, the other potential answers each with the number of times each was selected by other users next to it \(which is found the "responses" attribute in the Json\). 

1. Fork this fiddle: [https://jsfiddle.net/ebayfred/n431oxwz/](https://jsfiddle.net/ebayfred/n431oxwz/) 

2. Change the JavaScript, HTML, and CSS panels to solve the problem \(as described in the summary, preferably with React templates\) 

3. As part of the solution, implement the questionReducer. It’s a standard Redux reducer that takes a state and action and returns a new state. 

a. The state is the questions part of the last challenge. 

b. The action is dispatched when someone picks an answer to a question. It contains both the question ID and answer ID. The matching question/answer’s responses should be incremented.

> [https://jsfiddle.net/Sharonliao/5sebvL0w/](https://jsfiddle.net/Sharonliao/5sebvL0w/) \(color\)
>
> [https://jsfiddle.net/nvj4exgm/61/](https://jsfiddle.net/nvj4exgm/61/) \(animal\)

## Radio Button Component

```jsx
import React, { Component } from 'react';

class Test extends Component {
  state = {
    answer: ""
  };

  submitHandler = () => {
    const { answer } = this.state;
    if (answer) {
      console.log("You answer is " + answer);
    } else {
      console.log("You need to choose an answer");
    }
  }

  radioChange = e => {
    this.setState({answer: e.target.value});
  }

  render() {
    return (
      <React.Fragment>
        <h1>What is the name of this animal</h1>
        <input type="radio" value="monkey" onChange={() => this.radioChange}/>monkey<br/>
        <input type="radio" value="cat" onChange={() => this.radioChange}/>cat<br/>
        <input type="radio" value="dog" onChange={() => this.radioChange}/>dog<br/>
        <button onClick={this.submitHandler}>submit</button>
      </React.Fragment>
    )
  }
}
```

## Design a login page with header and footer

```jsx
import React, { Component } from "react";
import ReactDOM from "react-dom";
import axios from "axios";
import Footer from "./Footer";
import Header from "./Header";

import "./styles.css";

class App extends Component {
  constructor(props) {
    super(props);
    this.state = {
      username: "",
      password: ""
    };
  }
  handleChange = e => {
    const { name, value } = e.target;
    this.setState({ [name]: value });
  };

  handleSubmit = e => {
    e.preventDefault();
    axios
      .post("http://localhost:4000/api/users", this.state)
      .then(response => {
        alert("The user login successfully");
      })
      .catch(err => {
        alert(err);
      });
    this.setState({
      username: "",
      password: ""
    });
  };
  render() {
    return (
      <div>
        <Header />
        <div className="login-page">
          <h2>Login </h2>
          <form>
            <label> Username: </label>
            <input
              type="text"
              placeholder="username"
              name="username"
              value={this.state.username}
              onChange={this.handleChange}
            />
            <br />
            <label> Password: </label>
            <input
              type="password"
              placeholder="password"
              name="password"
              value={this.state.password}
              onChange={this.handleChange}
            />
            <button className="login-btn" onClick={this.handleSubmit}>
              Login
            </button>
          </form>
        </div>
        <Footer />
      </div>
    );
  }
}

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);
```

```jsx
import React from "react";
const Header = props => {
  return (
    <div className="wrapped">
      <span className="home-text">Home</span>
      <span className="list">List1</span>
      <span className="list">List2</span>
      <span className="list">List3</span>
    </div>
  );
};
export default Header;
```

```jsx
import React from "react";
const Footer = props => {
  return (
    <div className="wrapped">
      <span>Company ©author by</span>
    </div>
  );
};
export default Footer;
```

```css
.App {
  font-family: sans-serif;
  text-align: center;
}
.wrapped {
  border: 1px blue solid;
  padding: 10px;
}
.home-text {
  font-weight: bold;
  padding: 5px;
  cursor: pointer;
}
.list {
  color: tomato;
  padding: 5px;
  border: 1px gold solid;
  cursor: pointer;
}
.login-page {
  border: 1px pink solid;
  height: 400px;
}
h2 {
  color: blue;
}
input[type="text"],
input[type="password"] {
  width: 80%;
  padding: 5px 5px;
  margin: 8px;
}
.login-btn {
  width: 50%;
  background-color: green;
  color: bisque;
  cursor: pointer;
  padding: 5px;
}
```

## Toggle Component

```jsx
import React, { Component } from 'react';

class Toggle extends Component {
  state = {
    text: "Hello",
    display: false
  };

  toggleGreeting = () => {
    this.setState({display: !this.state.display});
  }

  render() {
    return (
      <div>
        <button onClick={this.toggleGreeting}>Button</button>
        <p>{this.state.display ? this.state.text : null}</p>
      </div>
    );
  }
}

export default Toggle;
```

## React Editable Table with add, delete and search filter

```markup
<body>
  <div id="container">
    <!-- This element's contents will be replaced with your component. -->
  </div>
</body>
```

```jsx
class Products extends React.Component {

  constructor(props) {
    super(props);
    // this.state.products = [];
    this.state = {};
    this.state.filterText = "";
    this.state.products = [
      {
        id: 1,
        category: 'Sporting Goods',
        price: '49.99',
        qty: 12,
        name: 'football'
      }, {
        id: 2,
        category: 'Sporting Goods',
        price: '9.99',
        qty: 15,
        name: 'baseball'
      }, {
        id: 3,
        category: 'Sporting Goods',
        price: '29.99',
        qty: 14,
        name: 'basketball'
      }, {
        id: 4,
        category: 'Electronics',
        price: '99.99',
        qty: 34,
        name: 'iPod Touch'
      }, {
        id: 5,
        category: 'Electronics',
        price: '399.99',
        qty: 12,
        name: 'iPhone 5'
      }, {
        id: 6,
        category: 'Electronics',
        price: '199.99',
        qty: 23,
        name: 'nexus 7'
      }
    ];
  }
  handleUserInput(filterText) {
    this.setState({filterText: filterText});
  };
  handleRowDel(product) {
    var index = this.state.products.indexOf(product);
    this.state.products.splice(index, 1);
    this.setState(this.state.products);
  };

  handleAddEvent(evt) {
    var id = (+ new Date() + Math.floor(Math.random() * 999999)).toString(36);
    var product = {
      id: id,
      name: "",
      price: "",
      category: "",
      qty: 0
    }
    this.state.products.push(product);
    this.setState(this.state.products);
  }

  handleProductTable(evt) {
    var item = {
      id: evt.target.id,
      name: evt.target.name,
      value: evt.target.value
    };
    
  var products = this.state.products.slice();
  var newProducts = products.map(function(product) {

    for (var key in product) {
      if (key == item.name && product.id == item.id) {
        product[key] = item.value;
      }
    }
    return product;
  });
    this.setState({products:newProducts});
    // console.log(this.state.products);
  };
  render() {
    return (
      <div>
        <SearchBar filterText={this.state.filterText} onUserInput={this.handleUserInput.bind(this)}/>
        <ProductTable onProductTableUpdate={this.handleProductTable.bind(this)} onRowAdd={this.handleAddEvent.bind(this)} onRowDel={this.handleRowDel.bind(this)} products={this.state.products} filterText={this.state.filterText}/>
      </div>
    );
  }
}
class SearchBar extends React.Component {
  handleChange() {
    this.props.onUserInput(this.refs.filterTextInput.value);
  }
  render() {
    return (
      <div>
        <input type="text" placeholder="Search..." value={this.props.filterText} ref="filterTextInput" onChange={this.handleChange.bind(this)}/>
      </div>
    );
  }
}

class ProductTable extends React.Component {

  render() {
    var onProductTableUpdate = this.props.onProductTableUpdate;
    var rowDel = this.props.onRowDel;
    var filterText = this.props.filterText;
    var product = this.props.products.map(function(product) {
      if (product.name.indexOf(filterText) === -1) {
        return;
      }
      return (<ProductRow onProductTableUpdate={onProductTableUpdate} product={product} onDelEvent={rowDel.bind(this)} key={product.id}/>)
    });
    return (
      <div>
      <button type="button" onClick={this.props.onRowAdd} className="btn btn-success pull-right">Add</button>
        <table className="table table-bordered">
          <thead>
            <tr>
              <th>Name</th>
              <th>price</th>
              <th>quantity</th>
              <th>category</th>
            </tr>
          </thead>
          <tbody>
            {product}
          </tbody>
        </table>
      </div>
    );
  }
}

class ProductRow extends React.Component {
  onDelEvent() {
    this.props.onDelEvent(this.props.product);

  }

  render() {
    return (
      <tr className="eachRow">
        <EditableCell onProductTableUpdate={this.props.onProductTableUpdate} cellData={{
          "type": "name",
          value: this.props.product.name,
          id: this.props.product.id
        }}/>
        <EditableCell onProductTableUpdate={this.props.onProductTableUpdate} cellData={{
          type: "price",
          value: this.props.product.price,
          id: this.props.product.id
        }}/>
        <EditableCell onProductTableUpdate={this.props.onProductTableUpdate} cellData={{
          type: "qty",
          value: this.props.product.qty,
          id: this.props.product.id
        }}/>
        <EditableCell onProductTableUpdate={this.props.onProductTableUpdate} cellData={{
          type: "category",
          value: this.props.product.category,
          id: this.props.product.id
        }}/>
        <td className="del-cell">
          <input type="button" onClick={this.onDelEvent.bind(this)} value="X" className="del-btn"/>
        </td>
      </tr>
    );
  }
}
class EditableCell extends React.Component {

  render() {
    return (
      <td>
        <input type='text' name={this.props.cellData.type} id={this.props.cellData.id} value={this.props.cellData.value} onChange={this.props.onProductTableUpdate}/>
      </td>
    );
  }
}
ReactDOM.render( < Products / > , document.getElementById('container'));
```

