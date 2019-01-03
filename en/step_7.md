## Final tweaks

On this card you'll make a few small changes to control things like the speed of the animation. Customise the changes to suit your own program!

+ Change the number of steps after the `stamp`{:class="blockpen"} from `20` to `4`. You'll probably need make the first `move`{:class="blockmotion"} bigger, maybe `60` instead of `45`, to get the glass of water out from behind the text sprite again.

+ Move the `wait`{:class="blockcontrol"} out of the first loop and put it after the loop instead, but still inside the `repeat until`{:class="blockcontrol"} loop, and change the value to `1` or `2` seconds, or whatever you like.

+ Test it out, and tweak the numbers to suit you!

+ Finally, why not add a `say`{:class="blocklooks"} block to have the sprite display the number of litres of water being shown? 

```blocks
    say (join (item (counter) of [WaterAmounts v]) [ litres!])
```

+ I'm also adding in some code at the very end to change the sprite back to the monkey and get the user to think about ways to conserve water.

```blocks
    repeat until <(counter) = (length of [Sprites v])>
        change [counter v] by (1)
        go to (item (counter) of [Sprites v])
        move (45) steps
        say (join (item (counter) of [WaterAmounts v]) [ litres!])
        repeat (item (counter) of [WaterAmounts v])
            move (20) steps
            stamp
            wait (0.5) secs
        end
    end
    hide
    go to x: (0) y:(0)
    switch costume to [monkey2-a v]
    set size to (100) %
    show
    say [Think about ways you could use less water!] for (5) secs
```

--- collapse ---
---
title: Show me all the code!
---

Here is how the whole program looks now, do you can check it if something in yours is not working right:

```blocks
    when green flag clicked
    set [counter v] to [0]
    clear
    go to x:(0) y:(0)
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
    say [How about brushing your teeth?] for (2) secs
    say [It can be tempting to leave the tap running while you brush. But did you know...] for (4) secs
    say [...a running tap loses 6 litres of water per minute?] for (3) secs
    switch costume to [glass water-a v]
    set size to (35) %
    repeat until <(counter) = (length of [Sprites v])>
        change [counter v] by (1)
        go to (item (counter) of [Sprites v])
        move (45) steps
        say (join (item (counter) of [WaterAmounts v]) [ litres!])
        repeat (item (counter) of [WaterAmounts v])
            move (20) steps
            stamp
            wait (0.5) secs
        end
    end
    hide
    go to x: (0) y:(0)
    switch costume to [monkey2-a v]
    set size to (100) %
    show
    say [Think about ways you could use less water!] for (5) secs
```

--- /collapse ---

