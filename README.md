## Artificial Life
### --Potential Flashing Images Warning--
Various ways of running this code could cause flashing images, please be careful.

This repository has the code for the Artificial Life project as described on the 
[314reactor.com](https://314reactor.com/2017/10/16/artificial-life-project/) blog. 
The goal of the project is to use a Raspberry Pi and a [Unicorn Pi Hat](https://shop.pimoroni.com/products/unicorn-hat) 
to simulate a set of artificial lifeforms. Features of the program include: 

* Create a number of artificial lifeforms that can move around a board and have colour/movement properties assigned to 
* them via 3 random numbers; the ‘DNA’ of the life-form – and display them onto an easy-to-observe output.
* Have those artificial lifeforms be able to interact with each other to ‘breed’ and pass along their traits to offspring, 
* as well as ‘kill’ each other to keep the population in check.
* Have random chance for ‘genetic chaos’ whereby instead of passing along a life-form’s properties to its offspring a 
* random number is inserted into the offspring’s ‘DNA’.
* BONUS – plug the code into the Minecraft API and see what random patterns of blocks can be spawned from the 
* artificial life-form’s movements and properties.


### Installation

A more detailed set of instructions is available on the blog post for this project. Basic instructions are: 

1. Install Raspbian on a Raspberry Pi. 
2. Clone the repository
3. Install the dependencies

Install and set up the Unicorn HAT:
[Unicorn HAT GitHub code](https://github.com/pimoroni/unicorn-hat)

You can also use this with the Unicorn HAT Mini:
[Unicorn HAT Mini GitHub code](https://learn.pimoroni.com/article/getting-started-with-unicorn-hat-mini)

Or even the Unicorn HAT HD:
[Unicorn HAT HD GitHub code](https://github.com/pimoroni/unicorn-hat-hd)

```

sudo pip install -r requirements.txt

```

### Running The Program

Run the program from the command line - for some reason I have found that it requires sudo to work with the HAT.
It will default to use the original Unicorn HAT, but if you add in the parameter '-uh' you can then specify between
SD, HD or MINI.

This will also run on a system without a physical HAT installed thanks to the 
[Unicorn HAT simulator](https://github.com/jayniz/unicorn-hat-sim) - although it does have some bugs at the moment.


```

sudo env PATH="$PATH" python artificial_life.py

```

Arguments that can be passed: 

```
  -m MAX_NUM, --max-num MAX_NUM
                        Maximum number possible for any entity traits
  -ilc LIFE_FORM_TOTAL, --initial-lifeforms-count LIFE_FORM_TOTAL
                        Number of lifeforms to start with
  -s LOOP_SPEED, --refresh-rate LOOP_SPEED
                        The refresh rate for the buffer processing, also sets
                        a maximum speed for the main loop processing, if sync
                        is enabled (this is to prevent the display falling
                        behind the logic loop)
  -p POP_LIMIT, --population-limit POP_LIMIT
                        Limit of the population at any one time
  -dc DNA_CHAOS_CHANCE, --dna-chaos DNA_CHAOS_CHANCE
                        Percentage chance of random DNA upon breeding of
                        entities
  -shs CUSTOM_SIZE_SIMULATOR, --simulator-hat-size CUSTOM_SIZE_SIMULATOR
                        Maximum possible time to move number for entities
  -c, --combine-mode    Enables life forms to combine into bigger ones
  -mc, --minecraft-mode
                        Enables Minecraft mode
  -tr, --trails         Stops the HAT from being cleared, resulting in trails
                        of entities
  -g, --gravity         Gravity enabled, still entities will fall to the floor
  -rc, --radiation-change
                        Whether to adjust radiation levels across the
                        simulation or not
  -r RADIATION, --radiation RADIATION
                        Radiation enabled, will increase random mutation
                        chance and damage entities
  -mr MAX_RADIATION, --max-radiation MAX_RADIATION
                        Maximum radiation level possible
  -rbc RADIATION_BASE_CHANGE_CHANCE, --radiation-base-change RADIATION_BASE_CHANGE_CHANCE
                        The percentage chance that the base radiation level
                        will change randomly.
  -rt, --retry          Whether the loop will automatically restart upon the
                        expiry of all entities
  -sim, --unicorn-hat-sim
                        Whether to use the Unicorn HAT simulator or not
  -hm {SD,HD,MINI,PANEL,CUSTOM}, --hat-model {SD,HD,MINI,PANEL,CUSTOM}
                        What type of HAT the program is using. CUSTOM only
                        works with Unicorn HAT Simulator
  -l {CRITICAL,ERROR,WARNING,INFO,DEBUG,NOTSET}, --log-level {CRITICAL,ERROR,WARNING,INFO,DEBUG,NOTSET}
                        Logging level
  -ff, --fixed-function
                        Whether to bypass pixel composer and use fixed
                        function for drawing (faster, less pretty)
```