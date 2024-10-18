This [[css]] property is used to specify the [[keyframe]] identifier name and how to apply those transition.

#### syntex:
 `animation: keyframe_identifier duration timing-function delay iteration-count direction fill-mode play-state`
```css
.a {
animation: myanimation 3s infinite ease-in;
}

@keyframes myanimation{ 
from{width: 50px} 
to{width: 100px}
}
```