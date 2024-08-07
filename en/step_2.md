## Wiring the ADC (MCP3008)

The MCP3008 is an ADC providing eight input channels. The eight connectors on one side are connected to the Pi's GPIO pins, and the other eight are available to connect analogue input devices to read their values.

Place the MCP3008 chip on a breadboard and carefully wire it up as shown in the following diagram. You should see a small notch, or dot, in one end of the chip. In the diagram, this end of the chip is alligned with column **19** on the breadboard.

![MCP3008 wiring](images/mcp3008.png)

Alternatively, you could use the [Analog Zero](http://rasp.io/analogzero/){:target="_blank"} board, which provides the MCP3008 chip on a handy add-on board to save you from the complicated wiring.

### Add a potentiometer

Now that the ADC is connected to the Pi, you can wire devices up to the input channels. A potentiometer is a good example of an analogue input device: it's simply a variable resistor, and the Pi reads the voltage (from 0V to 3.3V).

![Potentiometer](images/potentiometer.png)

A potentiometer's pins are ground, data, and 3V3. This means you connect it to ground and a supply of 3V3, and read the actual voltage from the middle pin.
--- task ---

Place a potentiometer on the breadboard and wire one side to the ground rail, the other to the 3V3 rail, and the middle pin to the first input channel as shown:

![Add a potentiometer](images/mcp3008-pot.png)

--- /task ---

### Code

Now your potentiometer is connected and its value can be read from Python!

--- task ---

Open your code editor and start a new script.

--- /task ---

--- task ---

Start by importing the `MCP3008` class from the GPIO Zero library:

    ```python
    from gpiozero import MCP3008
    ```

--- /task ---

--- task ---

Create an object representing your analogue device:

    ```python
    pot = MCP3008(0)
    ```

    Note the `0` represents the ADC's channel 0. There are 8 channels (0 to 7), and you're using the first one.

--- /task ---

--- task ---

Try to read its value:

    ```python
    print(pot.value)
    ```

--- /task ---

--- task ---

Run your code. You should see a number between 0 and 1. This represents how far the dial is turned.

--- /task ---

--- task ---

Now read the value in a loop:

    ```python
    while True:
        print(pot.value)
    ```

Try twisting the dial around to see the value change.

--- /task ---

