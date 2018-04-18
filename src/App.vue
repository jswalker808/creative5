<template>
  <div id="app">
    <app-header/>
    <router-view/>
  </div>
</template>

<script>
 import AppHeader from './components/AppHeader';
 export default {
   name: 'App',
   components: { AppHeader }
 }
</script>

<style>
 /* https://color.adobe.com/CS04-color-theme-1994456/?showPublished=true */
 body {
     font-size: 18px;
     padding: 20px 100px 0px 100px;
     font-family: 'Avenir', Helvetica, Arial, sans-serif;
     -webkit-font-smoothing: antialiased;
     -moz-osx-font-smoothing: grayscale;
 }
 button {
     color: #fff;
     min-width: 100px;
     line-height: 1em;
     border: none;
     border-radius: 5px;
     color: white;
     padding: 5px;
     text-align: center;
     text-decoration: none;
     display: inline-block;
     font-size: 1rem;
     margin: 4px 2px;
     height: 15%;
 }
 button.primary {
     background-color: #4ABDAC;
 }
 button.alternate {
     background-color: #4ABDAC;
     margin-top: 20px;
 }
 button:focus {
     outline: none;
 }
 button:hover {

 }
 button:active {
     transform: translateY(4px);
 }
 input {
     height: 20px;
     padding: 10px;
     border-radius: 5px;
 }
 a {
     color: #77C4D3;
 }
 .flexWrapper {
     display:flex;
 }
 .flexRight {
     margin-left: auto;
 }
 .error {
     color: #F35537;
 }
 .column {
     width: 100%;
 }
 .feed {
     width: 100px;
 }
 .feed img {
     width: 100%;
 }
</style>
