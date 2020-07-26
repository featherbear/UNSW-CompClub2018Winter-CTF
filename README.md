# Winter CompClub 2018 CTF 

## if else
Flag: `FLAG{MAGIC_STICK}`  
Follow the logic of the code

## Welcome
Flag: `FLAG{F0UND_Y0U!}`  
There is a code hidden on the door frame of the computer labs

## NOTICE: READ ME
Flag: `FLAG{THIS}`  
Flag in the description

## Bad Magic
Flag: `FLAG{St4y_Saf3}`  
There is JavaScript in the challenge page that makes the page go back, or turns white. Disable JavaScript to continue (or just look at the source code)

## Plain Sight
Flag: `FLAG{CAN_U_SEE_ME}`  
The flag is hidden in white font. Select the text to find it (or just look at the source code)

## Parse the Parcel
Flag: `FLAG{ITS_WRITE_HERE}`  
The flag is encoded in the given [Base64](https://en.wikipedia.org/wiki/Base64) string (without padding). Use a Base64 decoder
JavaScript has the function `atob(string)`

## The Official Flag
Flag: `FLAG{WIZARD}`  
Inspect the hex codes of each colour and combine them together. 

Colour One: `#464C41`  
Colour Two: `#477B57`  
Colour Three: `#495A41`  
Colour Four: `#52447D`  

Combine the hex codes into the string `464C41477B57495A4152447D`

Convert this series of hex numbers into ASCII to get the flag

## watch?v=rEdl2Uetpvo
Flag: `FLAG{1T_always_B3gins_w1th_Rec0n}`  
There is a flag in the browser cookies of the workshop's [main site](https://winter.compclub.com.au/)

## Needle in the Stack
Flag: `FLAG{U5e_A_MaGneT_to_finD_N3eDles}`  
Remove every second letter in the block of text and search for the flag

Doing a regex for `/F.L.A.G.{.+?}/` we get `F1L2A3G4{5U657e8_9A0_1M2a3G4n5e6T7_8t9o0_1f2i3n4D5_6N332e1D2l3e4s5}`

```js
var flag_obfs = "F1L2A3G4{5U657e8_9A0_1M2a3G4n5e6T7_8t9o0_1f2i3n4D5_6N332e1D2l3e4s5}";
var flag = "";
for (var i = 0; i < flag_obfs.length; i++) {
	flag += i % 2 == 0 ? flag_obfs[i] : "";
}
console.log(flag);
```

## Trick32
Flag: `FLAG{TransP0sit1on_mainT4n5_Fr3quenC1es}`  
Switch every two letters

```js
var flag_obfs = "LFGAT {arsn 0Pis1 tnom_ iaTnn 4_5rF q3euC ne1}s";
var flag = flag_obfs.replace(/ /g, "").split("");
for (var i = 1; i < flag.length; i += 2) {
	var temp = flag[i-1];
	flag[i-1] = flag[i];
	flag[i] = temp;
}
console.log(flag.join(""))
```

## #tag javascrypt
Flag: `FLAG{sp3llb0und}`  
Enter the string _qah0oyy3cf_ into the URL hash / anchor.

This string is a Rot13 cipher that has been reversed

```js
const flag = "FLAG{sp3llb0und}"
var flag_rot = flag.replace(/[a-zA-Z]/g,function(a){return String.fromCharCode(("Z">=a?90:122)>=(a=a.charCodeAt(0)+13)?a:a-26)})
// "SYNT{fc3yyo0haq}"

// Reverse the contents of the flag
// "qah0oyy3cf"

!location.hash[1]&&alert("Tag, you're it!\n(hint hint)");
(window.onhashchange=()=>(__ = (_ = location.hash).substr(1)) && alert(__ != '\x71\x61\x68\x30\x6f\x79\x79\x33\x63\x66' ? "Nope, try again." : ("Flag: " + ("SYNT{" + __.split("").reverse().join("") + "}").replace(/[a-zA-Z]/gi, s => String.fromCharCode(s.charCodeAt(0) + (s.toLowerCase() < 'n' ? 13 : -13))))))()
```
> [#jscrew.it](http://jscrew.it/)

## Pandora's Box
Flag: `FLAG{magical}`  
The flag is the second last word of the question description

## Lost in Numbers
Flag: `FLAG{36}`  

1 + 2 + 3 + 4 + **5** = 15  
1 + 5 = 6  
6^2 = 36

## Jittery Negotiations
Flag: `FLAG{caffeinated(Kim,Kim)+1}`  
Given the two objects that we have, we won't be able to make the return value of `caffeinated(..., ...)` true... so we'll cheat and add one!
In Python, any non-zero number is considered true

## No Greek in ASCII
Flag: `FLAG{bry@gmail.cοm}`  
Note - the ο is the Greek lowercase omicron, not the English letter o

## The First One
Flag: `FLAG{4nd_wh3re_2_f1nd_th4m}`  
On the Encryption slides

## Steganography Steganography
Flag: `FLAG{Hipsters}`  
Hidden flag on the Encryption slides.  
Every first letter: feel loss and grief {Hiding in plain sight troubles every reasonable scientist} 

## Sneaky SQu1rr3L 1
Flag: `FLAG{join_the_dark_artz}`  
SQL Injection! Thankfully there is debug information which allows us to more easily understand what injections we are performing

Inject this into the username field: `' OR 1--`

## Borderline Impossible
Flag: `FLAG{MII-MES}`  

It's actually quite possible! Hints are in the question. The numbers we see point to the character in the code. The number right after the character points to the next one... Rinse and repeat!

```
# # Embed our flag and hints
# 5 x x x x F 2 x L 6 x x x x x A 6 x x x x x G 1 { 3 x x M 3 x x I 5 x x x x I 9 x x x x x x x x - 2 x M 4 x x x E 1 S 3 x x }
## Pad the string to make it 64 pairs
# 5 x x x x F 2 x L 6 x x x x x A 6 x x x x x G 1 { 3 x x M 3 x x I 5 x x x x I 9 x x x x x x x x - 2 x M 4 x x x E 1 S 3 x x } 00
## Encode the hint numbers to hex
# 35 x x x x F 32 x L 36 x x x x x A 36 x x x x x G 31 { 33 x x M 33 x x I 35 x x x x I 39 x x x x x x x x - 32 x M 34 x x x E 31 S 33 x x } 00
## Encode the flag into hex
# 35 x x x x 46 32 x 4C 36 x x x x x 41 36 x x x x x 47 31 7B 33 x x 4D 33 x x 49 35 x x x x 49 39 x x x x x x x x 2D 32 x 4D 34 x x x 45 31 53 33 x x 7D 00

## Fuzzing, from a list of 2x 0-9, 2x -, 1x A-Z
fudge = ['30', '31', '32', '33', '34', '35', '36', '37', '38', '39', '2D', '30', '31', '32', '33', '34', '35', '36', '37', '38', '39', '2D', '41', '42', '43', '44', '45', '46', '47', '48', '49', '4A', '4B', '4C', '4D', '4E', '4F', '50', '51', '52', '53', '54', '55', '56', '57', '58', '59', '5A']
string = "35 x x x x 46 32 x 4C 36 x x x x x 41 36 x x x x x 47 31 7B 33 x x 4D 33 x x 49 35 x x x x 49 39 x x x x x x x x 2D 32 x 4D 34 x x x 45 31 53 33 x x 7D 00".split(" ")

import random
for i in range(len(string)):
  if string[i] == "x":
    string[i] = random.choice(fudge)

print(" ".join(string))
```

35 42 38 38 4A 46 32 44 4C 36 42 34 59 32 32 41 36 55 54 44 36 4A 47 31 7B 33 49 32 4D 33 39 4F 49 35 56 50 59 5A 49 39 54 37 5A 58 36 33 35 38 2D 32 56 4D 34 45 2D 38 45 31 53 33 45 48 7D 00

