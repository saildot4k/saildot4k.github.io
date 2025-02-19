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


## Widgets
Widgets is used to display menus in the screen. There are many Widget types to feet different needs.


```ADDWIDGET "LABEL" "Main Menu"```

Types of Widgets:


LABEL : to display a title.

```ADDWIDGET "LABEL" "$TXT_LABEL$"```

will display a title line with the text contained in the variable TXT_LABEL.


CHOICE : to display a choice to set a numerical value to a variable

```ADDWIDGET "CHOICE" "Title" "Description" "MY_CHOICE"  "CHOICE 1" "CHOICE 2" "CHOICE 3"```

will display a widget with the specified title and description (the description is displayed in the scroll bar), and will set the variable MY_CHOICE to "0", "1", or "2" depending of the user choice.


INT : to set a variable with a number

```ADDWIDGET "INT" "Title" Description" "MY_NUMBER" "0" "99" 1```

will display a widget to store a value between 0 and 99 in the variable MY_NUMBER. The user will be able to increment the number by 1.


AXIS : to set axis numbers (X,Y)

```ADDWIDGET "AXIS" "Title" "Description" "VALUE_X" "VALUE_Y" "0" "1920" "1" "0" "1920" "2"```

will display the widget which let the user to select a value for VALUE_X between 0 and 1920 with an increment of 1 and for VALUE_Y between 0 and 1920 with an increment of 2.


IP : to set an IP adress

```ADDWIDGET "IP" "Title" "Description" "IP_ADDRESS_1" "IP_ADDRESS_2" "IP_ADDRESS_3" "IP_ADDRESS_4"```

to set variables IP_ADRESS_1, IP_ADDRESS_2. For example, if you wish to display this IP again, you'll have to call


```ECHO "THE IP ADDRESS YOU'VE ENTERED IS $IP_ADDRESS_1$.$IP_ADDRESS_2$.$IP_ADDRESS_3$.$IP_ADDRESS_4$"```


CALL : to call another section of the code

```ADDWIDGET "CALL" "Title" "Description" "$ARG0$" "THE_SECTION" "ARG_2" "ARG_3"...```

will call the section "THE_SECTION" of the file $ARG0$ ($ARG0$ will be the file where this widget is executed. The section THE_SECTION is inside the same file). with arguments ARG_2 and ARG_3.
The text ARG_2 and ARG_3 will be available in the section THE_SECTION by calling variables $ARG2$ and $ARG3$. (see Sections below)