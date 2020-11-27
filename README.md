# PID Autotune 2 based (Under adaptation 2020-11-26)

Based on a programm builded by an example

```
This project has been created to support tuning a PID controller for a home brewing setup using [CraftBeerPI](https://github.com/Manuel83/craftbeerpi).
It consists of a brewing kettle simulation, a PID controller (based on [Arduino PID Library](http://brettbeauregard.com/blog/2011/04/improving-the-beginners-pid-introduction/)) and a PID autotune algorithm (based on [Arduino PID Autotune Library](http://brettbeauregard.com/blog/2012/01/arduino-pid-autotune-library/))
```

# Installation

1. Clone this repository:

`git clone https://github.com/DZPeru/pid-autotune-2`

2. Install the requirements:

`pip3 install -r requirements.txt` or `pip install -r requirements.txt` 

3. Run code.

<!-- 
After you have completed these steps, you should be able to run _sim.py_ as shown above. If plots are not shown, you have to configure the matplotlib backend, see [What is a backend?](http://matplotlib.org/faq/usage_faq.html#what-is-a-backend)
-->

## Options

1. Simulate

Example:

`sim.py --pid 'reference' 98 0.66 230 --pid 'Kp too low' 30 0.66 230 --pid 'Ki too low' 98 0.01 230`

Details:

```
usage: sim.py [-h] [-p name kp ki kd] [-a] [-v] [-e] [-n] [-t T] [-s T]
              [--ambient T] [-i t] [-d t] [--sampletime t] [--volume V]
              [--diameter d] [--power P] [--heatloss x] [--minout x]
              [--maxout x]

optional arguments:
  -h, --help            show this help message and exit
  -p name kp ki kd, --pid name kp ki kd
                        simulate a PID controller
  -a, --atune           simulate autotune
  -v, --verbose         be verbose
  -e, --export          export data to a .csv file
  -n, --noplot          do not plot the results
  -t T, --temp T        initial kettle temperature in °C (default: 40)
  -s T, --setpoint T    target temperature in °C (default: 45)
  --ambient T           ambient temperature in °C (default: 20)
  -i t, --interval t    simulated interval in minutes (default: 20)
  -d t, --delay t       system response delay in seconds (default: 15)
  --sampletime t        temperature sample time in seconds (default: 5)
  --volume V            kettle content volume in liters (default: 70)
  --diameter d          kettle diameter in cm (default: 50)
  --power P             heater power in kW (default: 6)
  --heatloss x          kettle heat loss factor (default: 1)
  --minout x            minimum PID controller output (default: 0)
  --maxout x            maximum PID controller output (default: 100)
```

2. Auto-tuning PID

Example:
`sim.py --atune --volume 50 --power 4`

List of autotuning algorithms:

```
- ziegler-nichols (PID)
-- pessen-integral (PID)
-- some-overshoot (PID)
-- no-overshoot (PID)
- brewing
- tyreus-luyben
- ciancone-marlin
```
