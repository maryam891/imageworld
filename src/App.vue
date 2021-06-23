<template>
  <div id="app">
    <div class="header">
      <b-row
        ><b-col> <h1 class="header-text">ImageWorld</h1></b-col>
      </b-row>
      <div id="links">
        <router-link to="/" style="color:grey">Home</router-link> |

        <router-link to="/photographers" style="color:grey"
          >Photographers</router-link
        >
        |

        <router-view />
      </div>
      <img src="./assets/homeimage.jpg" />
    </div>
  </div>
</template>

<style>
#links {
  font-size: 20px;
}
.header {
  background-image: linear-gradient(
    to right,
    rgba(175, 216, 221, 0.7),
    rgba(204, 171, 171, 0.7),
    rgba(255, 192, 203, 0.747)
  );
  padding: 30px;
  margin: 0px;
}
.header-text {
  text-align: center;
  color: rgb(242, 246, 247);
  margin: 0px;
}
</style>
