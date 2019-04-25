# React Coding Projects

## Like/Dislike Component

![](https://lh4.googleusercontent.com/gcRnGn8UoEXIsIlif94tvW7EcHcDgFZm1HIkQUogztQ_qJa8cdLLtcJTbln4u8QgE2k4zjlyq0RgLhJcVlNwBLTKhOmoaJCYsD_dR2pYQMWIC9-aegXUoqZiZPljiwyUj2-E31sL7emNu07e5g)

![](https://lh6.googleusercontent.com/vxGQFzPIY4UcMeJkgOskpRB5c_Nx5No-Ruurd7Xi80V2Snieq-LgTH9-aPtCzb89WHgS_ijZkLJ94IbEfOMqNmy9yyaK2KEIZSUSc27sKfYbHYWvG7iMP9cmGzENB2zuLUn3zVMBo5uroidauA)

```jsx
import cx from 'classnames';
import React, { Component } from 'react';

export default class LikeDislike extends Component {

	constructor(props){
    super(props);
    this.state = {
      likes:100,
      dislikes:25,
      isLike: false,
      isDislike: false
    }
  }
  
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

![](../.gitbook/assets/image%20%284%29.png)

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

## Like Button Component 

![](../.gitbook/assets/image%20%285%29.png)

![](../.gitbook/assets/image%20%287%29.png)

```jsx
import React, { Component } from 'react';

export default class LikeButton extends Component {
  state = {
    number: 100,
    liked: false
  }

  addLike = () => {
    this.setState({ liked: true, number: this.state.number + 1});
  }

  removeLike = () => {
    this.setState({ liked: false, number: this.state.number - 1});
  }

  render() {
    return (
      <>
        <div>
          {
            !this.state.liked ?
            <button className="like-button" onClick={this.addLike}>
            Like | <span className="likes-counter">{this.state.number}</span>
            </button> :
            <button className="like-button liked" onClick={this.removeLike}>
            Like | <span className="likes-counter">{this.state.number}></span>
            </button>
          }
        </div>
        <style>
          {`
            .like-button {
              font-size: 1rem;
              padding: 5px 10px;
              color: white;
            }
            .liked {
              font-weight: bold;
              color: red;
            }
          `}
        </style>
      </>
    );
  }
}
```

