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

## オススメ韓国の名前が見えます。
#### あなたの名前を書いてください。

<input type="text" id="input_text" name="input_text"/> 
<input type="submit" value="クリック" onClick="myFunction();"/> 

<script type="text/javascript">


function myFunction() {
    var apiUrl = 'https://jsonplaceholder.typicode.com/users/1/';
    fetch(apiUrl).then(response => {
      return response.json();
    }).then(data => {
      // Work with JSON data here
      document.getElementById("demo").innerHTML = data.name
      
      console.log(data);
    }).catch(err => {
      // Do something for an error here
    });

    
}
</script>
<span id="demo"></span>
