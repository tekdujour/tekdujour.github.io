---
layout: post
title: Dismiss the keyboard from a UITextField when the return key is pressed
---

1. Control drag from the text field to the view controller. ![Screen1](/images/ios/uitextfield1.png) 
Select the **delegate** option from the menu
![Screen2](/images/ios/uitextfield2.png)

2. In the implementation file (.m) add ```<UITextFieldDelegate>``` after the class name on the interface line.
![Screen3](/images/ios/uitextfield3.png)


3. Add the ```(BOOL)textFieldShouldReturn:(UITextField *)textField``` method.
![Screen4](/images/ios/uitextfield4.png)


Done!  Now when you the press the return key the keyboard will disappear.