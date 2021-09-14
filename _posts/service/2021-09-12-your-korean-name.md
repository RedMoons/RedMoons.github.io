---
title: "Stock tracker tweet site"
excerpt: "Site introduction"

categories:
  - Site introduction
tags:
  - stock
  - tracking
  - tweet
  - stockmarket
---

## testing button

<button onclick="window.location.href='https://www.naver.com';">Click</button>

<input type="text" id="name" name="name"/> 

<script type="text/javascript">
    var apiUrl = 'https://stock-tweet-tracker.com/api/v1/stocks';
    fetch(apiUrl).then(response => {
      return response.json();
    }).then(data => {
      // Work with JSON data here
      console.log(data);
    }).catch(err => {
      // Do something for an error here
    });
</script>