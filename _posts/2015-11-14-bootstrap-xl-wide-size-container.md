---
layout: post
title:  "Bootstrap如何设置超大尺寸容器（container）"
categories: bootstrap
---

有时候我们需要一个超大XL尺寸的容器。比如说当浏览器宽度达到1600px甚至1800px都能重复利用空间的容器，Bootstrap默认的容器宽度最大只有1200px不到。我们可以自己定义一个容器。容器尺寸可以随着显示器视窗的大小变化而做相应的自动切换。  

例子：  


    .container-xl{
      @extend .container;
    }
    
    @media (min-width: 1800px) {
      .container-xl{
        width: 1780px;
      }
    }
    @media (min-width: 1550px) and (max-width: 1799px ) {
      .container-xl{
        width: 1530px;
      }
    }
    @media (min-width: 1300px) and (max-width: 1549px ) {
      .container-xl{
        width: 1280px;
      }
    }
    @media (min-width: 1050px) and (max-width: 1299px ) {
      .container-xl{
        width: 1030px;
      }
    }
 

