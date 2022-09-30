## Vulnerable code:

```html
<html>
  <head>
  	<title>Address based DOM XSS</title>
  </head>0
  
  <body>
    <script>
      var payload = window.location.hash.substr(1);window.location.assign(payload);
    </script>
  </body>
</html>
```

## Here the 'window.location.hash' is used to handle the string with a hash in front of the url. So we can give an input by adding a hash into the url

url: 
```
https://public-firing-range.appspot.com/address/location.hash/assign + #test
```

## The 'substr(1)' function is used to trim the hash character from the input we give, And parse only the string not the hash.

## The input get saved in that 'payload' variable

## 'window.location.assign(payload)' function is used to replace the current page with whatever page we give to it by the payload variable.

## and we can also give a valid javascript code and it will run that code.

## Payload: https://public-firing-range.appspot.com/address/location.hash/assign#javascript:alert(1)