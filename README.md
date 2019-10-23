# php excerpt
Text Summary / Excerpt Function

When the number of words exceeds the specified limit, the text continues until the end of the sentence.

``` php
function excerpt($data, $limit = 18)
{
    $arr = array_filter(explode('.', strip_tags($data)));
    $total = 0;
    $return = '';
    for($i=0;$i<count($arr);$i++){
        $total += count(explode(' ', $arr[$i]));
        $return .= $arr[$i] . '. ';
        if($total >= $limit){
            break;
        }
    }
    return $return;
}
```
Use:
``` php
echo excerpt('text here', 12);
```

Example:
``` php
$text = "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin eget risus sed turpis faucibus convallis. Vestibulum sagittis vestibulum nunc, quis feugiat libero rhoncus vitae. Etiam eleifend mauris condimentum lorem aliquet, vitae ullamcorper orci bibendum. Vestibulum in libero dui. Aliquam ut neque semper lectus viverra viverra ac id mauris. Vestibulum eu nulla consequat, vulputate felis ac, cursus leo. Nunc scelerisque ex ac varius consectetur.";

echo excerpt($text);
//Output:
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin eget risus sed turpis faucibus convallis. Vestibulum sagittis vestibulum nunc, quis feugiat libero rhoncus vitae.

echo excerpt($text, 5);
//Output
Lorem ipsum dolor sit amet, consectetur adipiscing elit.

```
