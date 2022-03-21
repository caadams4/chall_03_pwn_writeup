# chall_03_pwn_writeup
executable stack and shellcode


Ok, so in this one, when we execute the program, we get a suspect address leak. It looks something like 0xff7xxxxxxx.

 Its probably a **stack address**. So run checksec and we see a beautiful red 'NX disabled' -- meaning the stack is executable, and no canary, so we can stack smash and hijack the inst ptr. 
 
 We open the binary in radare 2 and see there's a 'gets' that reads in 0x140 bytes. Perfect.... our shellcode will only take 48. 
 
 SO, our payload this time will start with the shellcode, then junk, then ret. 
 
 below is the pwn in execution: 
 
 
 ![image](https://user-images.githubusercontent.com/79220528/159326751-6e591200-a27e-41a2-b9ca-f0cc5a7d55f4.png)
