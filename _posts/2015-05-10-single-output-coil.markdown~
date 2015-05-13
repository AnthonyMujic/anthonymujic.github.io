---
layout: post
---

Every output should only be energised in one location. Don't set outputs in multiple locations. Following this simple rule makes debugging easier. Consider the following scenario: 

You have a pump P101. The run command for P101 is stored in C100. In automatic mode, provided there are no alarms  and the  process interlocks are healthy, when the run command comes on, the pump should start:


![Pump Run Rung](/assets/single output coil/pump run rung.png)


In this scenario the run command is set in step 3 of sequence 1:


![First Run Command](/assets/single output coil/first run command.png)


Further down the code however, in step 4 of sequence 2, the run command is also set:


![Second Run Command](/assets/single output coil/second run command.png)


If the run command is set in sequence 1 but cleared in sequence 2, the run output wont come on. This can be confusing when debugging the code. In sequence 2, when the run command is set the run output will come on as expected. This occurs due to the scan order of the PLC. 

In general, code is executed top to bottom, left to right. Inputs are read before the ladder scan starts and outputs are set after the code has been executed.

One simple way to overcome this problem is the only set a bit at one place in the code. To refactor from setting a bit in multiple locations to setting a bit in a single location, use the following steps:

1) Add in a new rung with the run command as the input and as the output.

![Run Command Coil](/assets/single output coil/run command coil.png)

2) Add new sequence 1 step 3 command and sequence 2 step 4 command contacts in parallel with the P101 run command.

![Multi Input Run Coil](/assets/single output coil/multi input run coil.png)

3) Replace the P101 run command output related to sequence 1 step 3  with the new sequence 1 step 3 command bit. 

![First Seq Command](/assets/single output coil/first seq command.png)

4) Replace the P101 run command output related to sequence 2 step 4  with the new sequence 2 step 4 command bit. 

![Second Seq Command](/assets/single output coil/second seq command.png)

5) Remove the P101 run command input from the new coil.

![Final Run Command](/assets/single output coil/final run command.png)

This should have removed the bug from your code and cleaned up the code. Now when debugging the code position of code and scan order do not play a part in what the result will be.

