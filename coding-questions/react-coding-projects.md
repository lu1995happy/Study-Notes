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

