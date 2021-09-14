---
title: "あなたの韓国の名前"
excerpt: "オススメ韓国の名前"

categories:
  - Casual entertainment
tags:
  - Casual entertainment
  - 韓国
  - 名前
---

## あなたの名前を書いてください
#### オススメ韓国の名前が見えます。
<button onclick="window.location.href='https://www.naver.com';">Click</button>

<input type="text" id="name" name="name"/> 

<script type="text/javascript">
    var apiUrl = 'https://jsonplaceholder.typicode.com/users/1/';
    fetch(apiUrl).then(response => {
      return response.json();
    }).then(data => {
      // Work with JSON data here
      document.getElementById('test_api').innerHTML = data
      console.log(data);
    }).catch(err => {
      // Do something for an error here
    });



</script>

<div id='test_api'> </div>