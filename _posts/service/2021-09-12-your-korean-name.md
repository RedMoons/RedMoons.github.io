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

## あなたにピッタリな韓国の名前は？
#### あなたの名前を入力してください。（ひらがなで）

<input type="text" id="inputText" name="inputText"/> 
<input type="submit" value="クリック" onClick="getRecommendName();"/> 

<script type="text/javascript">


function getRecommendName() {
    var apiUrl = 'https://jsonplaceholder.typicode.com/users/1/';
    fetch(apiUrl).then(response => {
      return response.json();
    }).then(data => {
      // Work with JSON data here
      document.getElementById("recommendName").innerHTML = data.name
      console.log(data);
    }).catch(err => {
      // Do something for an error here
    });
}
</script>
<span id="recommendName"></span>
