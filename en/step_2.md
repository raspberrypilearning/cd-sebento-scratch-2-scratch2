## Getting information from the user

On this card you'll make the water usage calculator. To personalise the calculation for your program's user, you'll use a new block to ask them questions that they can type in answers to.

+ Open a new Scratch project and go to the Costumes tab for the cat sprite.

+ Add a new costume from the library. Choose a character that will do some talking. I'm using this monkey:

![The talking monkey costume](images/askMonkeyCostume.png)

+ Click on the Scripts tab and add the following blocks to your sprite. You will find the `ask and wait`{:class="blocksensing"} block in the **Sensing** category.

```blocks
    when green flag clicked
    set size to (80) %
    switch costume to [monkey2-a v]
    ask [What's your name?] and wait
```

+ Change the question to `How many times do you flush the toilet each week?`{:class="blocksensing"} .

You've asked the user for information — now you need to get the answer! 

+ First, create a variable called `flushes`{:class="blockdata"}. You will use it to store the user's answer.

[[[generic-scratch-add-variable]]]

+ Drag out the `set flushes to`{:class="blockdata"} block from **Data**.

+ Then, look in the **Sensing** section and find the `answer`{:class="blocksensing"} block. This is a special variable where a Scratch program puts the most recent answer it's received from an `ask and wait`{:class="blocksensing"} block.

+ Plug the block into your code like this:

```blocks
    when green flag clicked
    set size to (80) %
    switch costume to [monkey2-a v]
    ask [How many times do you flush the toilet each week?] and wait
    set [flushes v] to (answer)
```

Time for a bit of math! First you need somewhere to store a total.

+ Create another variable called `totalWater`{:class="blockdata"} and set its value to `0` at the start of the program.

```blocks
    when green flag clicked
    set [totalWater v] to [0]
```

+ Go to **Operators** and look for this block:

```blocks
    () * ()
```

It lets you **multiply** two numbers.

+ Drag it into a `change totalWater by`{:class="blockdata"} block, like this:

```blocks
    change [totalWater v] by (() * ())
```

+ Plug your `flushes`{:class="blockdata"} block into one side of the operator block and on the other side, type in the number `6`. 6 litres is roughly how much water is used for one toilet flush.

```blocks
    when green flag clicked
    set [totalWater v] to [0]
    set size to (80) %
    switch costume to [monkey2-a v]
    ask [How many times do you flush the toilet each week?] and wait
    set [flushes v] to (answer)
    change [totalWater v] by ((flushes) * (6))
```

+ Finish off the script with a couple of `say`{:class="blocklooks"} blocks to tell the user the result! You'll find the `join`{:class="blockoperators"} block in **Operators**.

```blocks
    when green flag clicked
    set [totalWater v] to [0]
    set size to (80) %
    switch costume to [monkey2-a v]
    ask [How many times do you flush the toilet each week?] and wait
    set [flushes v] to (answer)
    change [totalWater v] by ((flushes) * (6))
    say [You use...] for (2) secs
    say (join(totalWater) [ litres of water each week!]) for (5) secs
```

+ Click the green flag to test your code.

--- challenge ---

## Challenge: add more water uses to the calculation

+ Add another question to find out how many showers the person has per week. Then calculate how many litres of water this uses and add it to the total. 

A shower uses about 7 litres per minute, so a five-minute shower uses around 35 litres.

--- hints ---

--- hint ---

+ You'll need to create a variable to store the number of showers per week. 

+ Use the `ask and wait`{:class="blocksensing"} and `answer`{:class="blocksensing"} blocks to get the information from the user and store it in the new variable.

```blocks
    ask [How many showers do you have per week?] and wait
    set [showers v] to (answer)
```

--- /hint ---

--- hint ---

+ To calculate the amount of water used on showering, you'll need to multiply the number of showers by `35` (the amount of water for one five-minute shower).

```blocks
    (showers) * (35)
```

+ You can add the result to your total like this:

```blocks
    change [totalWater v] by ((showers) * (35))
```

--- /hint ---

--- hint ---

Your code should look something like this now:

```blocks
    when green flag clicked
    set [totalWater v] to [0]
    set size to (80) %
    switch costume to [monkey2-a v]
    ask [How many times do you flush the toilet each week?] and wait
    set [flushes v] to (answer)
    change [totalWater v] by ((flushes) * (6))
    ask [How many showers do you have per week?] and wait
    set [showers v] to (answer)
    change [totalWater v] by ((showers) * (35))
    say [You use...] for (2) secs
    say (join(totalWater) [ litres of water per week!]) for (5) secs
```

--- /hint ---

--- hint ---

If you want to, you can also ask them how many minutes they spend in the shower! In that case, you would need to do an extra calculation: multiply the number of minutes by `7` (litres per minute in the shower), and then multiply the result by the number of showers. You can put an operator inside an operator to do that, like this:

```blocks
    (showers) * ((showerMinutes) * (7))
```

Here's how your code would look:

```blocks
    when green flag clicked
    set [totalWater v] to [0]
    set size to (80) %
    switch costume to [monkey2-a v]
    ask [How many times do you flush the toilet each week?] and wait
    set [flushes v] to (answer)
    change [totalWater v] by ((flushes) * (6))
    ask [How many minutes do you usually spend in the shower?] and wait
    set [showerMinutes v] to (answer)
    ask [How many showers do you have per week?] and wait
    set [showers v] to (answer)
    change [totalWater v] by ((showers) * ((showerMinutes) * (7)))
    say [You use...] for (2) secs
    say (join(totalWater) [ litres of water per week!]) for (5) secs
```
--- /hint ---

--- /hints ---

--- /challenge ---
