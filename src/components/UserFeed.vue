<template>
  <div class="feed">
    <div>
      <h3>Enter a movie into your watch list!</h3>
      <form v-on:submit.prevent="tweet" class="tweetForm">
	<input v-model="text" placeholder="Movie Name"/>
  <button class="primary" type="submit">Submit</button>
	<div class="buttonWrap">
	</div>
      </form>
    </div>
    <div class="itemSection">
    <div v-for="item in feed" class="item">
      <p class="tweet">{{item.tweet}}</p>
    </div>
    </div>
    <a href="https://github.com/jswalker808/creative5" id="gitLink">Link to GitHub</a>
  </div>
</template>

<script>
 import moment from 'moment';
 export default {
   name: 'UserFeed',
   data () {
     return {
       text: '',
     }
   },
   created: function() {
     this.$store.dispatch('getFeed');
   },
   filters: {
     since: function(datetime) {
       moment.locale('en', {
	 relativeTime: {
	   future: 'in %s',
	   past: '%s',
	   s:  'seconds',
	   ss: '%ss',
	   m:  '1m',
	   mm: '%dm',
	   h:  'h',
	   hh: '%dh',
	   d:  'd',
	   dd: '%dd',
	   M:  ' month',
	   MM: '%dM',
	   y:  'a year',
	   yy: '%dY'
	 }
       });
       return moment(datetime).fromNow();
     },
   },
   computed: {
     feed: function() {
       return this.$store.getters.feed;
     },
   },
   methods: {
     tweet: function() {
       this.$store.dispatch('addTweet',{
         tweet: this.text,
       }).then(tweet => {
	       this.text = "";
       });
     },
   }
 }
</script>

<style scoped>
 .feed {
     width: 600px;
 }
 .tweetForm {
     padding: 10px;
     margin-bottom: 10px;
     border-radius: 5px;
 }
 .buttonWrap {
     width: 100%;
     display: flex;
 }
 button {
     margin-top: 1%;
     margin-left: 3%;
     height: 35%;
     font-size: 0.9em;
     padding: 10px;
 }
 textarea {
     width: 100%;
     height: 5em;
     padding: 2px;
     margin-bottom: 5px;
     resize: none;
     box-sizing: border-box;
 }
 #gitLink {
 height: 30px;
 position: fixed;
 bottom: 0;
 margin: auto;
 width: 100%;
 text-decoration: none;
 }
 span button {
  min-width: 20px;
  background-color: #ff4949;
  float: right;
 }
 input {
    border-radius: 5px;
 }
 .item {
     border-bottom: 1px solid #ddd;
     padding: 10px;
 }
 .itemSection {
     border: solid 2px grey;
     border-radius: 5px;
     width: 75%;
 }
 .tweet {
     margin-top: 0px;
     font-weight: 800;
 }
 .idline {
     margin-bottom: 0px;
 }
 .user {
     font-weight: bold;
     margin-right: 10px;
 }
 .handle {
     margin-right: 10px;
     color: #666;
 }
 .time {
     float: right;
     color: #666;
 }
</style>
