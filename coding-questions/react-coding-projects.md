# React Coding Projects



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

## 

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

## 

![](https://lh4.googleusercontent.com/zTQjlH2xgU9gmlSiw4WqwcAHSQWKlzzi7hOy-MOM_AU_9L2lUIw04LQdjSMfWnu3TU5hPDk2ncG699DwDx-QXxlrmuJQRuyKFPNTPo0t5XY31j2BjbMJFqtzk5mExsGuVNd2NLXH9NN-4llxbQ)

```markup
<div class="container">
  <header> Header </header>
  <aside> Aside </aside>
  <section> 
    <div class="content1"> 1 </div>
    <div class="content2"> 2 </div>
  </section>
  <article> Article </article>  
</div>
```

```css
* {
  box-sizing: border-box;
}

.container {
  width: 50vw;
  height: 80vw;
  border: solid;
  position: relative;
}

header {
  text-align: center;
  border-bottom: dotted;
  height: 3vw;
  line-height: 3vw;
}

aside {
  width: 10vw;
  height: 77vw;
  border-right: dotted;
  line-height: 77vw;
  text-align: center;
  float: left;
}

section {
  position: absolute;
  width: 40vw;
  height: 38.5vw;
  border-bottom: dotted;
  right: 0;
}

div.content1, div.content2 {
  height: 38.5vw;
  width: 20vw;
  float:left;
  line-height: 38.5vw;
  text-align: center;
}

div.content1 {
  border-right: dotted;
}

article {
  height: 38.5vw;
  width: 40vw;
  position: absolute;
  bottom: 0;
  right: 0;
  line-height:38.5vw;
  text-align: center;
}

```

