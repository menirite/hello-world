# hello-world
9.Palindrome Number
-----
Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

eg:<br>
121 True<br>
-121 False<br>

方法1：直接反转。
```Python
if str(x)[::-1] == str[x]
  return True
else:
  return False
```
方法2：分而治之。反转数字1221的后半段，则21变为12，与前半段相等，为回文数。<br>
  首先处理临界情况，小于0为false。<br>
  反转过程，1221%10，得到最后一位1，要得到倒数第二位数字，先1221/10=122，122%10=2为结果。1*10+2=12。<br>
  何时反转到原来的一半？上述原始数据÷10<反转数字×10。<br>
  最后一位与第一位对比。
```Python
def palindrome(x):
  """
  type x:int
  rtype:bool
  """
  if x<0:
    return False
  ls = 0
  tmp = x
  while tmp!=0:
    ls += 1
    tmp = tmp//10
  tmp = x
  for i in range(ls/2):#i确定对比几次
    right = tmp%10
    left =tmp/(10**(ls-2*i-1))#与第1，3位对比
    left = left%10
    if left != right:
      return False
    tmp = tmp //10
  return True
```
