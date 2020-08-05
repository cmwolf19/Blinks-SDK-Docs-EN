# Blinks API Reference
# Display
## **setColor()**
 **Description**\
  
Displays a color on the entire Blink.

**Syntax**\
setColor(COLOR);

**Parameters**\
COLOR: a color, either from [Defined Colors](https://docs.google.com/document/d/18tZSNT9PbkFpMRHs1ZLBGBZQ7pKVXfYQyx4ZgM8f9O0/edit#heading=h.2kkwxuxsrz85) or one you define with a Color function.

**Returns**\
Displays a color on the entire Blink.

**Example Code**\
```
void setup() {

// sets the color of the Blink to blue

setColor(BLUE);

}
```
**Notes & Warnings**\

Please note that setColor() commands do not actually update the color on the LEDs until loop() returns.

## setColorOnFace()
**Description**\
Displays a color on a single face of a Blink.

**Syntax**\
setColorOnFace(COLOR, face number);

**Parameters**\
COLOR: a color, either from [Defined Colors](https://docs.google.com/document/d/18tZSNT9PbkFpMRHs1ZLBGBZQ7pKVXfYQyx4ZgM8f9O0/edit#heading=h.2kkwxuxsrz85) or one you define with a Color function.

Face Number: a pixel on a Blink. Can be from (1-6) faces.

**Returns**\
Displays a color on a certain face(s) on the Blink.

**Example Code**\
```
void setup() {

// sets the color to be white on face 0

setColorOnFace(WHITE, 0);

}
```
**Notes & Warnings**\
Please note that setColor() commands do not actually update the color on the LEDs until loop() returns.

----------

# **Colors**

## **makeColorRGB()**
**Description**\
Summon a color using its RGB value to assign to your blink’s face(s) or store for later

**Syntax**\
makeColorRGB(red, green, blue);

**Parameters**\
Red: amount of red, 0-255
Green: amount of green, 0-255
Blue: amount of blue, 0-255

**Returns**\
A color value that can then be used to set the color of the blinks

**Example Code**
```
//if you want to name a color to reference at the top of 
//your code to store for use throughout your code

#define BLUE makeColorRGB(0, 0, 255)
#define VICTORYGREEN makeColorRGB(5, 240, 29)

void setup(){
setColor(VICTORYGREEN);
//or to summon a color one time on the spot
setColor(makeColorRGB(44, 23, 160));

}

//furthermore, if you wanted to be able to change the color on the 
//fly you could have each parameter be a variable

Byte flexRed = 30;
Byte flexGreen = 200;
Byte flexBlue = 150;

#define RAINBOW makeColorRGB(flexRed, flexGreen, flexBlue)

//and then you could write code that changes the 
//values of flexRed, flexGreen, and flexBlue to make the RAINBOW color change over time
```
**Notes/Warnings**\
If you’d like to have control over the Hue, Saturation, or Brightness of your blinks, it may better serve you to use the makeColorHSB() function.
There are 9 preset Blinks colors that you do not need to define.
There are lots of existing RGB color pickers online to help you find just the right color, for example:
[rapidtables.com/web/color/RGB_Color.html](http://rapidtables.com/web/color/RGB_Color.html)

## makeColorHSB()
**Description**\
Summon a color using its HSB value to assign to your blink’s face(s) or store for later

**Syntax**\
makeColorHSB(hue, saturation, brightness);

**Parameters**\
Hue: The numerical hue of your color, 0-255 (where 0 is red-adjacent orange and 255 is red-adjacent purple)
Saturation: How saturated your color will be, 0-255 (where 0 is white and 255 is full color)
Brightness: How bright your color will be, 0-255 (where 0 is entirely dark and 255 is full power)

**Returns**\
A color value that can then be used to set the color of the blinks

**Example Code**
```
//if you want to name a color to reference at the top of your
// code to store for use throughout your code

#define BLUE makeColorHSB(170, 255, 255)
#define VICTORYGREEN makeColorHSB(90, 255, 230)

void setup(){
setColor(VICTORYGREEN);
//or to summon a color one time on the spot
setColor(makeColorHSB(230, 180, 245));
}

//furthermore, if you wanted to be able to change the color on the
// fly you could have each parameter be a variable

Byte flexHue = 140;
Byte flexSaturation = 200;
Byte flexBrightness = 150;

#define RAINBOW makeColorHSB(flexHue, flexSaturation, flexBrightness)

//and then you could write code that changes the values of flexHue, 
//flexSaturation, and flexBrightness to make the RAINBOW color change over time
```
**Notes/Warnings**\
Most HSB color pickers set the Hue parameter on a scale of 0-360, however blinks read them from 0-255. If you use an online HSB color picker you will likely have to adjust your Hue value.
There are 9 preset Blinks colors that you do not need to define.

## **dim()**
**Description**\
returns the color passed in a dimmer state

**Syntax**\
dim(color, value);

**Parameters**\
Color: Any defined color name, either one of the predefined color values or one you define yourself
Value: Brightness (from makeColorHSB) 0-255 bucketed into 32 levels of brightness (0 means light is off, 255 means light is all the way on)

**Returns**\
A color shade set to a determined brightness (or dimness)

**Example Code**
```
dim(HAPPY_PURPLE, 150);
dim(GREEN, 10);
```
----------

## **Defined Colors**
**Description**\
The blinks have 9 pre-assigned colors that you can call without needing to define them.

**Syntax**\
RED\
ORANGE\
YELLOW\
GREEN\
CYAN\
BLUE\
MAGENTA\
WHITE\
OFF

(This is how these colors would be defined if written with makeColorRGB or makeColorHSB)
|RBG|HSB|
|--|--|
|#define RED makeColorRGB(255, 0, 0)|#define RED makeColorHSB( 0, 255, 255)|
|#define ORANGE makeColorRGB(255, 127, 0)|#define ORANGE makeColorHSB( 21, 255, 255)
|#define YELLOW makeColorRGB(255, 255, 0)|#define YELLOW makeColorHSB( 43, 255, 255)
|#define GREEN makeColorRGB( 0, 255, 0)|#define GREEN makeColorHSB( 85, 255, 255)
|#define CYAN makeColorRGB( 0, 255, 255)|#define CYAN makeColorHSB(128, 255, 255)
|#define BLUE makeColorRGB( 0, 0, 255)|#define BLUE makeColorHSB(170, 255, 255)
|#define MAGENTA makeColorRGB(255, 0, 255)|#define MAGENTA makeColorHSB(213, 255, 255)
|#define WHITE makeColorRGB(255, 255, 255)|#define WHITE makeColorHSB( 0, 0, 255)
|#define OFF makeColorRGB( 0, 0, 0)|#define OFF makeColorHSB( 0, 0, 0)

**Parameters**\
None

**Returns**\
The color stated

**Example Code**
```
setColor(BLUE);
setColorOnFace(MAGENTA, 2);
```
**Notes/Warnings**\
Do not name anything these pre-assigned names! You’ll delete the color RED if you define a new RED!

----------

# **Button**

All button handling is done with flags, so when you call a function, it returns the value of the flag (i.e. whether or not that action has occurred) and only when you have called the function will it reset the flag to false.

## **buttonPressed()**
**Description**\
Called when a button is pressed. A flag is set to true on the change from button up to button down. buttonPressed() returns that flag, and then sets it back to false.

**Syntax**\
buttonPressed();

**Parameters**\
None

**Returns**\
Returns the buttonPressed function flag as true, and then sets it back to false.

**Example Code**
```
if(buttonPressed())
{
	// Perform an action
}
```

## **buttonReleased()**
**Description**\
Called when a button goes from button down to button up.

**Syntax**\
buttonReleased();

**Parameters**\
None

**Returns**\
Returns true on the change from button down to button up, and then sets it back to false.

**Example Code**\
```
if(buttonReleased())
{
	// Perform an action.
}
```

## **buttonSingleClicked()**
**Description**\
Checks if a Blink has been clicked once.

**Syntax**\
buttonSingleClicked();

**Parameters**\
None

**Returns**\
Returns true if the Blink has been single clicked since the last time this value was checked.

**Example Code**
```
//This function sets a blink to be red if single clicked.
if (buttonSingleClicked())
{
	setColor(RED);
}
```
**Notes/Warnings**\
This function will remain true until it is called. For example, if a Blink is single clicked, and then, later in the programming, this function is called, it will return true. This can be fixed by calling this function at the bottom of your loop.

## **buttonDoubleClicked()**
**Description**\
Checks if a Blink has been clicked twice in a short amount of time.

**Syntax**\
buttonDoubleClicked();

**Parameters**\
None

**Returns**\
Returns true if the Blink has been double clicked since the last time this value was checked.

**Example Code**
```
//This function sets a blink to be red if double clicked.
if (buttonDoubleClicked())
{
	setColor(RED);
}
```
**Notes/Warnings**\
This function will remain true until it is called. For example, if a Blink is double clicked, and then, later in the programming, this function is called, it will return true. This can be fixed by calling this function at the bottom of your loop.

## **buttonMultiClicked()**
**Description**\
Checks to see if a Blink has been clicked more than once in a short period of time.

**Syntax**\
buttonMultiClicked();

**Parameters**\
None

**Returns**\
Returns true if a Blink has been clicked more than once since this value was checked..

**Example Code**
```
//This function sets a blink to be red if multi-clicked.
if (buttonMultiClicked())
{
	setColor(RED);
}
```
**Notes/Warnings**\
This function will remain true until it is called. For example, if a Blink is multi-clicked, and then, later in the programming, this function is called, it will return true. This can be fixed by calling this function at the bottom of your loop.

## **buttonClickCount()**
**Description**\
Returns the number of clicks recorded during button multi clicking.

**Syntax**\
buttonClickCount();

**Parameters**\
None

**Returns**\
Returns the number of clicks input as part of a multi-click.

**Example Code**
```
byte clicks = 1;
if (buttonMultiClicked())
{
	clicks = buttonClickCount();
}
```
**Examples of Usage**\
**[https://forum.move38.com/t/button-inputs-tutorial/288](https://forum.move38.com/t/button-inputs-tutorial/288)**

## **buttonLongPressed()**
**Description**\
When a button is held down continuously for 1.5 seconds.

**Syntax**\
buttonLongPressed();

**Parameters**\
None.

**Returns**\
Returns the buttonLongPressed function to be true and an action is then displayed on the Blink.

**Example Code**
```
bool longPressing = false;
if (buttonLongPressed())
{
	longPressing = true;
}
```
**Notes & Warnings**\
If you hold the button for too long, the Blink will go into programming mode, or even to sleep.

**Examples of Usage**\
Check out how this method is used in [Astro](https://youtu.be/omJUh8d9GPA)!

## **buttonDown()**
**Description**\
Checks if the button is down.

**Syntax**\
buttonDown();

**Parameters**\
None

**Returns**\
Returns true if the button is down, and false if it is not down.

**Example Code**
```
void loop() {
	if (buttonDown()) 
	{
		setColor(RED);
	} 
	else 
	{
		setColor(WHITE);
	}
}
```
**Example of Usage**\
[https://forum.move38.com/t/button-inputs-tutorial/288](https://forum.move38.com/t/button-inputs-tutorial/288)

----------

# **Communication**

## **setValueSentOnAllFaces()**
**Description**\
Sets the value sent on all faces to a given value between 0 and 63.

**Syntax**\
setValueSentOnAllFaces(byte value);

**Parameters**\
Value: A value between 0 and 63.

**Returns**\
None.

**Example Code**
```
//Sets the value sent on all faces to 10 if isBomb is true.
if (isBomb == true)
{
	setValueOnAllFaces(10);
}
```
**Notes/Warnings**\
This function can be used in conjunction with bitwise operators to send more complex data. See the tutorial on safely sending signals, located [here](https://forum.move38.com/t/safely-sending-signals-part-2/262).

## **setValueSentOnFace()**
**Description**\
Sets the value that should be sent on a specific face on a Blink.

**Syntax**\
setValueOnFace(value, face);

**Parameters**\
Value: A value between 0 and 63 that will be sent.
Face: One of the six faces on the Blink, 0-5.

**Returns**\
None.

**Example Code**
```
//Sets the value sent on face 0 to 10 if isBomb is true.
if (isBomb == true)
{
	setValueSentOnFace(10, 0);
}
```
**Notes/Warnings**\
This function can be used in conjunction with bitwise operators to send more complex data. See the tutorial on safely sending signals, located [here](https://forum.move38.com/t/safely-sending-signals-part-2/262).

## **getLastValueReceivedOnFace()**
**Description**\
Gets the last value received on a specific face.

**Syntax**\
getLastValueReceivedOnFace(face);

**Parameters**\
Face: One of the faces on the Blinks 0-5.

**Returns**\
A byte between 0 and 63 that was received from the face.

**Example Code**
```
//Gets the value on face 0 and checks if it is 
//greater than or equal to 5. Sets to red if true.
if (getLastValueReceivedOnFace(0) >= 5)
{
	setColor(RED);
}
```
**Notes/Warnings**\
This function does not check if the signal has expired.

## **isValueReceivedOnFaceExpired()**
**Description**\
isValueReceivedOnFaceExpired is a function that checks if a given face has failed to receive a new signal from a neighbor.

**Syntax**\
isValueReceivedOnFaceExpired(byte faceIndex);

**Parameters**\
faceIndex: Index of the face to check [0-5]

**Returns**\
True if the value received on face f has not changed or refreshed in the last 200 ms.

**Example Code**
```
//If the value received from face 5 is expired, set its color to red.
if (isValueReceivedOnFaceExpired(5)
{
	setColorOnFace(RED, 5);
}
```
**Notes/Warnings**\
isValueReceivedOnFaceExpired() will return false for the first frame a Blink is turned on before setting to false.

## **didValueOnFaceChange()**
**Description**\
didValueOnFaceChange() is a function that allows a Blink to determine if a value that it is receiving is different than the last value that was received on that same face.

**Syntax**\
didValueOnFaceChange(byte faceIndex);

**Parameters**\
faceIndex: Index of the face to check [0-5]

**Returns**\
True if the value received on face f has changed compared to the last received value stored on the face.

**Example Code**
```
**//**When a Blink sends a new signal to face 0, the Blink will turn red.
bool bottomFaceUpdate= didValueOnFaceChange(0);
if(bottomFaceUpdate)
{
	setColor(RED);
}
```
**Notes/Warnings**\
didValueOnFaceChange() will check against the last value received on the face, meaning even if a Blink is disconnected after sending a signal, that value will remain.

## **isAlone()**
**Description**\
isAlone() is a function that checks if all the faces on a Blink have expired values.

**Syntax**\
bool isAlone();

**Parameters**\
None

**Returns**\
True if all faces on the Blink have not received a valid signal within the last 200 ms. 

**Example Code**
```
//This function will turn a Blink red if connected to 
//another for more than 1 second.

Timer isolated;

if (isAlone())
{
	isolated.set(1000);
}

if (isloated.isExpired())
{
	setColor(RED);
}
```
----------

# **Time**

## **timer.set()**
**Description**\
Set the duration of your timer

**Syntax**\
void.set(duration);

**Parameters**\
Duration: amount of milliseconds your timer will run for

**Returns**\
None.

**Example Code**
```
Timer myTimer; //declaring a timer called myTimer
myTimer.set(3000)
```

## **Timer.isExpired()**
**Description**\
A bool that declares whether or not your timer has run out

**Syntax**\
timer.isExpired();

**Parameters**\
Timer: name of already declared timer

**Returns**\
True if a timer has existed longer than its set duration.

**Example Code**
```
Timer.myTimer
if(myTimer.isExpired())
{
	//some action because the timer is expired
} else if (!myTimer.isExpired()){
	//some action because the timer is NOT expired
}
```

## **Timer.getRemaining()**
**Description**\
Tells you how many milliseconds you have remaining on a timer

**Syntax**\
Timer.getRemaining();

**Parameters**\
Timer: A timer you have already declared

**Returns**\
The time remaining in milliseconds as a long.
If the timer has expired it will return 0

**Example Code**
```
//for example, you can map the remaining time 
//on a timer to change the saturation of your blink

byte saturation = 0;
if(!myTimer.isExpired()){
	byte timerProgress = myTimer.getRemaining();
	saturation = map(timerProgress, 0, TIMERLENGTH, 0, 255);
	setColor(makeColorHSB(0, saturation, 255));
}
```
----------

# **Types**

## **Color**
**Description**\
Holds information to allow you to set a certain color using RGB, HSB, or System Rainbow and to display brightness / dimness of a color.

**Syntax**\
var(val);

**Parameters**\
var: makeColorRGB, makeColorHSB, dim
val:
 - RGB values (0-255)
  
  - HSB values (0-255)
   
 - COLOR, value (0-255)

**Returns**\
Returns a color on the Blink.

**Example Code**
```
Color makeColorRGB(red, green, blue);

// R, G, and B values [0-255]
Color makeColorHSB(hue, saturation, brightness);

// H, S, and V values [0-255]
Color dim(color, value);

// returns the color passed in a dimmer state
//(0-255 bucketed into 32 levels of brightness)
```
**Notes & Warnings**\
Check [Colors()](https://docs.google.com/document/d/18tZSNT9PbkFpMRHs1ZLBGBZQ7pKVXfYQyx4ZgM8f9O0/edit#heading=h.gxn26xf5arw9) Reference for more information about how to set colors on Blinks.

## **Timer**
**Description**\
Helps declare a timer in your code. Timers allow you to set a certain amount of time for a function to be active.

**Syntax**\
Timer timerName;

**Parameters**\
timerName: any name you can give your timer.

**Example Code**
```
#define TIMER_LENGTH 6000
Timer redTimer;

void setup() {
	redTimer.set(TIMER_LENGTH);
}

void loop() {
	byte saturation = 0;

	if (!redTimer.isExpired()) {
		int timerProgress = redTimer.getRemaining();
		saturation = map(timerProgress, 0, TIMER_LENGTH, 0, 255);
	}
}
```
**Examples of Usage**\
Check the [Basic Time Function Tutorial](https://forum.move38.com/t/basic-time-functions/303) and Time Reference Library for more information about how to incorporate Timers in your code!

----------

# **Convenience**

## **FOREACH_FACE(f)**

**Description**\
A for loop that runs through all six faces in ascending order (0, 1, 2, 3, 4, 5)

**Syntax**\
FOREACH_FACE(f) { }

**Parameters**\
F: the variable name for the faces, usually kept as f

**Returns**\
None

**Example Code**\
```
FOREACH_FACE(f){
	if (getLastValueReceivedOnFace(f) == WINNER){
		setColor(GREEN);
	}

}
```
**Notes/Warnings**\
Because it’s a loop running through all six faces in ascending order, it’s best to not call functions in the loop, rather set booleans and bytes in the loop that can then be referenced outside of it.

## **COUNT_OF(array)**
**Description**\
COUNT_OF() returns the number of items in a given array as a byte.

**Syntax**\
COUNT_OF(array);

**Parameters**\
array: Any fixed size array.

**Returns**\
A byte which is the size of the array.

**Example Code**
```
//Adds up the values in array valueArray and 
//sets the total to be sent on all faces.

byte returnInt = 0;

for (byte counter = 0; counter < COUNT_OF(valueArray); counter++)
{
	returnInt = valueArray[counter];
}
setValueSentOnAllFaces(returnInt);
```

## **FACE_COUNT**
**Description**\
FACE_COUNT is defined on every Blinks system as the number of faces.

**Returns**\
A byte representing the number of faces on the Blink. (6)

**Example Code**
```
//This code will take a face (someFace) and 
//set that face to Red, and the opposite face to Blue.

byte someFace;
if (!isValueOnFaceExpired(someFace))
{
	setColorOnFace(RED, someFace);
	setColorOnFace(BLUE, (someFace+3) % FACE_COUNT);
}
```
----------


# Uniqueness

## **uint16_t random (uint16t_limit)**
**Description**\
A randomize function that returns an unsigned integer value that is up to 16 bits (1-65535).

**Syntax**\
random(uint16t_limit);

**Parameters**\
uint16t_limit: Upper limit (exclusive) of the range to use for randomization.

**Returns**\
An unsigned int from 0 - uint16t_limit.

**Example Code**
```
//This function finds a value between 0 and 5096.
short myShort = 5096;
short newShort = random(myShort);
```
**Notes/Warnings**\
Without calling randomize(), this function will return the same set of values each time it is used.

## **random()**
**Description**\
The random function generates a random number based on the values it is given.

**Syntax**\
random(max);
random(min, max);

**Parameters**\
min: lower amount of the random value(optional).
max: upper amount of the random value.

**Example Code**
```
byte randFace;
void loop() {
	if(buttonPressed())
	{
		//if button is pressed, magenta will appear randomly on a face
		randFace = random(6);
		setColorOnFace(MAGENTA,randFace);
	}
}
```
**Notes & Warnings**\
Not truly random each time you install the game.

**Examples of Usage**\
Check out [Widgets](https://youtu.be/rowD9Byubxk) to see how randomization works for Blinks.

## **randomize()**
**Description**\
Set up the random number generator.

**Syntax**\
randomize();

**Parameters**\
None.

**Example Code**
```
byte randFace;

void setup(){
randomize();
}

void loop() {
	if(buttonPressed()){
		//if button is pressed, magenta will appear randomly on a face
		randFace = random(6);
		setColorOnFace(MAGENTA,randFace);
	}
}
```
**Notes & Warnings**\
If you don't call this at the beginning of your program, your random calls will be the same each time you reinstall the game

**Examples of Usage**\
Check out [Widgets](https://youtu.be/rowD9Byubxk) to see how randomization works for Blinks.

## **getSerialNumberByte(byte n)**
**Description**\
Gets and returns one of the digits of the serial number for a specific Blink tile.

**Syntax**\
getSerialNumberByte(byte n);

**Parameters**\
n: A value from 0-8 which corresponds to the Blink’s serial number place.

**Returns**\
A byte of the serial number at digit n.

**Example Code**
```
//This function checks the first serial number
//and compares its byte value to 128.
byte myIdentity = getSerialNumberByte(0);
if (myIdentity <= 128) setColor(GREEN);
else setColor(RED);
```
**Notes/Warnings**\
This function is reliant on the specific Blink it is being run on, meaning values will be different from Blink to Blink, but constant if repeatedly called on a single Blink.
