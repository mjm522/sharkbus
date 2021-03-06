# sharkbus
Code for controlling Invcare Sharkbus protocol wheelchairs

This repo contains both Python and C code for communicating with an Invacare Pronto wheelchair.
The chair uses the Sharkbus protocol to communicate from the joystick to the motor controller.

This code was worked out through a combination of reverse engineering, with a little help from 
an insider at Invacare who filled in the gaps I hadn't worked out.

The python code is probably easier to understand, and I'd recommend looking at the hexportmon/sharkmon.py for
an example of decoding the Sharkbus messages.

The 'brainstem' folder contains my C reimplementation of the python code - sacu.c contains most of the goodies.

The timing contstraints on SharkBus are very strict, and failure to deliver a message in the appropriate time
slot will result in the wheelchair going into an error condition and refusing to accept any further commands.

Hope this repo helps someone out.

## Setup instructions for Ubuntu

It is better to install and play in a virtual environment. If you already have one, proceed to step 2.

#### Step 1: Install virtual environment; this library is compatable only with python2

      a) pip install virtualenv
      b) open /home/<usr name>/basrc file and add the following lines.
         <source /usr/local/bin/virtualenvwrapper.sh>
         <export WORKON_HOME=~/.virtualenvs>
      c) mkvirtualenv shark

#### Step 2: Clone this library to a folder
    
    a) sudo apt-get install libgmp3-dev
    b) workon shark
    c) pip intall gmpy
    d) pip install pygame

#### Step 3: Run the sharkmon.py from sharkbus/hexpormon



