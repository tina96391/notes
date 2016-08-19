# Level 1(the idiot test)
很簡單，只要右鍵→檢查元件就可以看到一行被註解掉的程式碼</br>
the first few levels are extremely easy: password is _______</br>
輸入就行了
# Level 2
直接按下submit就通過
# Level 3
右鍵→檢查元件可以發現一個</br>
input type="hidden" name="file" value="____"</br>
在網址列後面加上找到的value就可以找到真的密碼了</br>
# Level 4
右鍵→檢查元件找到按鈕的那一行，修改上面的mail就可以收到密碼了
# Level 5
使用JS injection，在網址上打上</br>
javascript:alert(document.forms[0].to.value="___@___")</br>
填入自己的mail後就會送出密碼囉
# Level 6
嘗試在第一個空格內填入數字後按下按鈕可以發現加密後的值，是原本的數字加上第幾位-1</br>
123→加密後12(+1)3(+2)→135</br>
只要按照這個規律回推就好了
# Level 7
內文說到裡面UNIX cal command，先輸入隨意數字後發現他是叫出該年分的月曆</br>
所以試試輸入;ls</br>
分號是把後面的程式跳過</br>
加上ls可以叫出所有檔案</br>
看到所有檔案後有一個像是亂碼的.php</br>
把網址列上的檔案換掉就有flag了</br>