<template>
    <div class="grid-item card">
          <div class="img-container">
          <slot name="source">
            </slot>
          </div>
          <div class="content">
            <h3 class="title"><slot name="fullName"></slot></h3>
            <p class="category"><slot name="category"></slot></p>

            <div class="infoProd">
              <div class="rating">
                <p><span>Rating:  </span><slot name="rate"></slot></p>
                <p><span>Count: </span><slot name="count"></slot></p>
              </div>
              <div class="price">
                <p><span>Price: </span><slot name="price"></slot></p>
              </div>

            </div>
            <div class="DescProd">
              <p class="titleDesc">Description</p>
                <div class="dProd"><p><slot name="description"></slot></p></div>
              </div>
          </div>
      </div>
  </template>

<style >
.grid-item{
  position: relative;
  height: 270px;
overflow: hidden;
/*https://css.glass */
background: rgba(255, 255, 255, 0.676);
border-radius: 16px;
box-shadow:4px 10px 7px 1px #635e6341;
backdrop-filter: blur(10px);
-webkit-backdrop-filter: blur(10px);
}
.card{
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  width: 674px;
}

.infoProd span{
  color: rgb(118, 53, 131);
  font-size: 21px;
}
.infoProd p{
  padding: 3px 0;
  font-weight: bold;
  font-size: 1.2em;
}
.img-container{
  height: 100%;
}
.img-container img{
  width: 250px;
  height: 100%;
}
.content{
  width: 55%;
  height: 100%;
  margin: 0px 14px ;
}
.title{
display: flex;
align-items: center;
  font-size: 20px;
margin-top: 10px;
  color: hsl(289, 78%, 26%);
height: 35%;
}
.content .category{
  color: brown;
  font-size: 1.5rem;
  padding: 0;
}
.dProd{
  position: absolute;
  top: -100%;
  right: 0;
  width: 63%;
  height: 100%;
  font-size: 15px;
  padding: 10px;
  margin: 0 ;
  text-align: justify;
  line-height: 28px;
  background-color: rgba(195, 167, 192, 0.968);
  transition:translate .35s linear ease-in-out;
}
.titleDesc{
  text-align: center;
 position: absolute;
 bottom:0 ;
 right: 0%;
 width: 200px;
font-size: 1.6rem;
  color: #6e4b90b9;
  background-color: #c9b8cc78;
  border-radius: 50px  0 0;
  margin-bottom: 0;
}
.titleDesc:hover~.dProd{
  transform-origin: 0 0;
  transition: transform 0.5s;
  transform: translateY(100%);
}

  </style>





