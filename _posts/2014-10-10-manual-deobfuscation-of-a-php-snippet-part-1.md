---
layout: post
title: "Manual deobfuscation of a PHP snippet - Part 1"
date: 2014-10-10 20:50:00 +0200
comments: true
categories: 
---

In late July the following question was posted on a IRC-channel i frequent: 

{% blockquote %}
Anyone care to devise what an obfuscated PHP payload does?
{% endblockquote %}

Sure, why not, sounds like a challenge. This is part 1 of a series of blogposts explaining the headache-inducing three hours that followed.

<!-- more -->

The following snippet had been added to the top of _every_ PHP file in a Wordpress installation. Scroll right to see it all. _Far_ _right_.

{% include_code lang:php deobfuscate_php/obfuscated_1.php.txt %}

After adding some newlines and replacing some strings with placeholders we can read the code without pondering our political stance.

{% include_code lang:php deobfuscate_php/obfuscated_2.php.txt %}

Let's see if we can make the code a bit more readable:

The ```$fognhntadd``` on line 1 is not code to be executed, but is there to be used by the rest of the code. We can't really make it more readable at this point. 

 ```$sjeykdhzzn``` on line four appears to split its second argument on ```chr((238-194))```. [chr](http://php.net/manual/en/function.chr.php) returns a one-character string containing the character specified by the decimal argument. ```chr(238-194) = chr(44)```, and a quick look in ```man ascii``` tells us that the ASCII character with a decimal value of 44 is , (comma). This means ```$sjeykdhzzn``` will evaluate to an array consisting of 456 (0-455) numbers, every other large (1000+) and small(<50). 

 ```$jekjvzbupt``` on line 9 is a [substring](http://php.net/manual/en/function.substr.php) of the horribly long ```$fognhntadd``` - but how to know what without counting to 10106? (67419-57313=10106).

The code does not appear to to anything dangerious, so let's try to parse it using a PHP engine! *google "run php code online"*. The second result, [sandbox.onlinephpfunctions.com](http://sandbox.onlinephpfunctions.com/) looks promising.

Pasting in ```$fognhntadd```, ```$jekjvzbupt``` and a [var_dump](http://php.net/manual/en/function.var-dump.php), tells us that ```$jekjvzbupt``` evaluates to the string ```/(.*)/e```. While i didn't know at the time, if this string is used in [preg_replace](http://php.net/manual/en/function.preg-replace.php) on a system using PHP prior to 5.5.x, it is basically the same as [eval](http://php.net/manual/en/function.eval.php).

We will skip the function ```otmxvqaaam``` for now.

The escaped string ```$wrewusbqxp``` get the same treatment, and returns the following code:

```
 /* gzmcixrfif */ eval(str_replace(chr((183-146)), chr((361-269)), otmxvqaaam($sjeykdhzzn,$fognhntadd))); /* iakxdbcknr */ 
```

 ```$flwwfkzecg``` evaluates to ```preg_replace```, why am i not surprised?

Line 26 uses ```$flwwfkzecg``` as a function name, and can thus be written like this:

```php
preg_replace('/(.*)/e', 'eval(str_replace(chr((183-146)), chr((361-269)), otmxvqaaam($sjeykdhzzn,$fognhntadd)));', NULL);
```

This can also be written like this, reusing the techniques used above:

```php
$foo = otmxvqaaam($sjeykdhzzn, $fognhntadd);
$bar = str_replace('%', '\\', $foo); # '\\' => \
eval($bar);
```

Suddenly understanding the function ```otmxvqaaam``` defined on line 12 becomes interesting. After renaming some of the variables, the function becomes somewhat easier to read. 

```php
function otmxvqaaam($start_and_length_array, $string) {
	$return_value = NULL; 
	for ($i=0; $i < (sizeof($start_and_length)/2); $i++) {
		$start = $start_and_length_array[($i*2)]
		$length = $start_and_length_array[($i*2)+1]
		$return_value .= substr($string, $start, $length); 
	} 
	return $return_value; 
};
```

This function uses ```$start_and_length_array``` together with ```substr``` as a [grille](http://en.wikipedia.org/wiki/Cardan_grille). The even number positions(0,2,4...) of the array are the positions in the ciphertext, while the odd (1,3,5...) positions are the lengths.

I concluded that the last three lines did nothing that was worth analyzing. We now have enough data to make the code easier to read.

{% include_code lang:php deobfuscate_php/obfuscated_3.php.txt %}

Since the code up to this point does nothing active (exec, system, fwrite, ...), we can replace ```eval``` with echo in our code, and get the following result:

{% include_code lang:php deobfuscate_php/obfuscated_4.php.txt %}

Oh joy! Another layer of obfuscation. I can't wait for part 2!
