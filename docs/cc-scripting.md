# BootManager Scripting Documentation

## Variables
Variables are used to store values.
To set a new variable, you have to specify the type :
```SET "STRING" "MY_VARIABLE" "Mod your life"```

**Possible types are:**
STRING : string

U8/S8 : Signed/Unsigned 8-bits number
U16/S16 : Signed/Unsigned 16-bits number
U32/S32 : Signed/Unsigned 32-bits number


Signed numbers can be negatives, Unsigned can only be positives.


**Examples**
```SET "U8" "MY_DIGIT" "235"```
```SET "S32" "MY_OTHER_DIGIT" "-3420"```


The best place to define your variables and their types is in the file DEFCONF.PBT.
If you want your variable to be saved in the configuration file of Boot Manager, the name MUST begin with "BM.CNF".


Once the type is set, you can assign a new value to the variable :
```SET "MY_DIGIT" "34"```

**Call an existing variable**
To call an already defined variable, you have to surround it with ```$``` :

```ECHO "$MY_DIGIT$"```
will display 34 in the output console.


## Messages
Messages can be displayed either on the output console, or in the TV screen.

```ECHO "The value of MY_DIGIT is : $MY_DIGIT$"```
will return the text and the contain of the variable in the output console which will be in most case the console where you launched ps2client.


```MESSAGE "Installation Complete"```
will return the text in the TV screen.


You can escape a character with ^

```MESSAGE "The Crystal Chip is ^"astonishing^"".```
The ^ will tell the MESSAGE command not to interpret the " next to it as the end of the string character.