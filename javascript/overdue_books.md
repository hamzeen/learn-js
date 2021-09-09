## JS
```javascript
function solution(today, limit) {
  var rows = $('table tbody tr').length;
  for(var i = 0; i< rows; i++) {
    var $x = $('table tbody').find('tr').eq(i);
    
    var theArray = $x[0].innerText.trim().split(/\s+/);
    var elapsed = (theArray.length > 2) ? daysElasped(theArray[1],theArray[2]) : daysElasped(theArray[1], today) ;

    if (elapsed > limit) {
       $('table tbody').find('tr').eq(i).css('background-color', '#FF0000');
    }
  }
}

function daysElasped(start, end) {
  var diffTime = Math.abs(new Date(end) - new Date(start));
  var diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24)); 
  return diffDays;
}

$( document ).ready(function() {
  solution('2015-11-30', 7);
});

```

## CSS
```css
tr {
  padding: 20px;
  margin:20px;
}
table td {
  padding:20px;
}
```



## HTML

```html
<table><tbody>
    <tr>
        <th>burrower</th>
        <th>burrowed date</th>
        <th>return date (max 7days)</th>
    </tr>
    <tr>
        <td>Addison</td>
        <td>2014-08-14</td>
        <td>2014-10-09</td>
    </tr>
    <tr>
        <td>Valencia</td>
        <td>2014-08-14</td>
        <td>2014-10-09</td>
    </tr>
    <tr>
        <td>Patrick</td>
        <td>2015-11-23</td>
        <td></td>
    </tr>
</tbody></table>
```
