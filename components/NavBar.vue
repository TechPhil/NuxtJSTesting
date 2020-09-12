<!--suppress HtmlUnknownTarget -->
<template>
  <nav class='open-nav--wrap nav-fixed'>
    <div class='open-nav'>
      <div class='open-nav--brand'>
        <span>TechPhil Billing Portal</span>
      </div>
      <ul class='open-nav--menu'>
        <li class='open-nav--item'>
          <NuxtLink to='/'>Home</NuxtLink>
        </li>
        <li class='open-nav--item'>
          <NuxtLink to='/about'>About</NuxtLink>
        </li>
        <li class='open-nav--item'>
          <NuxtLink to=''></NuxtLink>
        </li>
      </ul>
      <ul class='open-nav--mobilemenu' id='mobileMenu'>
        <li class='open-nav--item'>
          <NuxtLink to='/'>Home</NuxtLink>
        </li>
        <li class='open-nav--item'>
          <NuxtLink to='/about'>About</NuxtLink>
        </li>
        <li class='open-nav--item'>
          <NuxtLink to=''></NuxtLink>
        </li>
      </ul>
      <div class='nav-toggler' v-on:click="toggleNav">
        <div class='nav-toggler-line'></div>
        <div class='nav-toggler-line'></div>
        <div class='nav-toggler-line'></div>
      </div>
    </div>
  <hr id='navhr' style='visibility: hidden;'>
  </nav>
</template>

<script>
export default {
  name: "NavBar",
  methods: {
    toggleNav: function() {
      let navbar = document.getElementById("mobileMenu");
      let hr = document.getElementsByTagName("hr")[0];
      navbar.classList.toggle("nav-open");
      hr.classList.toggle("nav-open");
    }
  }
}

</script>

<!--suppress SpellCheckingInspection -->
<style lang="scss">
// Text
$navcolor: #000000;
$navhovercolor: #363636;
$navbg: #ffffff;
// Body
$bodybg: #ececec;
// Sizing
$desktop-menu-width: 200px; // Setting this value higher will increase the spacing between items
$mobile-breakpoint: 800px; // Use this setting to change how soon the nav enters mobile mode
* {
  box-sizing: border-box;
  font-family: sans-serif;
}

html,body {
  margin: 0;
  padding: 0;
  width: 100%;
  min-height: 99%;
  background: $bodybg;
}
.open-nav--wrap {
  padding: 0 2rem;
  height: 55px;
  background: $navbg;
  position: relative;
  .contained {
    max-width: 1100px;
    margin: auto;
  }
  .open-nav {
    height: 100%;
    display: grid;
    grid-template-columns: auto 1fr $desktop-menu-width;
    @media (max-width: $mobile-breakpoint) {
      grid-template-columns: auto 1fr 30px;
    }
    .open-nav--brand {
      display: flex;
      align-items: center;
      font-weight: bold;
      font-size: 1.1rem;
    }
    .open-nav--menu {
      list-style: none;
      margin: 0;
      padding: 0;
      display: flex;
      grid-column: 3/4;
      flex-direction: row;
      align-items: center;
      justify-content: space-between;

      @media (max-width: $mobile-breakpoint) {
        display: none;
      }

      .open-nav--item {
        a {
          color: $navcolor;
          text-decoration: none;
          transition: ease .12s;

          &:hover {
            color: $navhovercolor;
          }
        }
      }
    }
    .open-nav--mobilemenu {
      position: absolute;
      top: 55px;
      left: 0;
      width: 100%;
      list-style: none;
      margin: 0;
      padding: 0 2rem;
      display: flex;
      flex-direction: column;
      overflow: hidden;
      pointer-events: none;
      background: $navbg;
      max-height: 0;
      transition: max-height .3s ease;

      @media (min-width: $mobile-breakpoint) {
        display: none;
        max-height:55px;
      }

      .open-nav--item {
        margin-bottom: 15px;
        a {
          color: $navcolor;
          text-decoration: none;
          transition: ease .12s;

          &:hover {
            color: $navhovercolor;
          }
        }
      }
      .open-nav--item:first-child {
        margin-top: 15px;
      }
      .open-nav--item:last-child {
        margin-bottom: 25px;
      }
    }
    @media(max-width:$mobile-breakpoint){
      .nav-open {
        max-height: 130px;
        pointer-events: all;
      }
    }
    .nav-toggler {
      grid-column: 3/4;
      display: flex;
      align-self: center;
      height: 30px;
      cursor: pointer;
      flex-direction: column;
      justify-content: space-evenly;
      .nav-toggler-line {
        width: 100%;
        height: 2px;
        background: #bdbdbd;
      }
      @media (min-width: $mobile-breakpoint) {
        display: none;
      }
    }
  }
}

.nav-fixed {
  position: fixed;
  top: 0;
  width: 100%;
  left:0;
}

hr#navhr {
  transition: height 0.3s ease;
  height:55px;
  @media (max-width: $mobile-breakpoint) {
    &.nav-open {
      height:185px;
    }
  }
}


</style>
