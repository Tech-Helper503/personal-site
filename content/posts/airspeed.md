---
title: "Airspeed Calculations"
date: 2023-07-11T08:18:45Z
draft: false
cover:
    image: "https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/True_airspeed_indicator.svg/389px-True_airspeed_indicator.svg.png"
    alt: "airspeed indicator"
    caption: "airspeed indicator showing ias/tas indications"
    relative: false # To use relative path for cover image, used in hugo Page-bundles
---
{{<katex>}}

# What is Airspeed
Airspeed is the speed of an aircraft, measured relative to air it is moving in. Airspeed is used due to the fact that **it dictates the amount of lift any given aircraft can produce**. The higher the airspeed, the higher the amount of lift the aircraft can produce. This also ensures that planes always have the same stall speed, regardless of weather conditions, such as clouds or headwinds and tailwinds.

# Types of Airspeed
There are various types of airspeed on an aircraft such as:
* Indicated airspeed **(IAS)**
* True Airspeed **(TAS)**
* Calibrated Airspeed **(CAS)**
* Mach Number **(Mach)**
* Equivalent Airspeed **(EAS)**

## Indicated Airspeed(IAS)
Indicated Airspeed is measured by the pitot and static ports on a plane. The pitot tube is placed directly into the airflow. The pitot tube takes advantage of Bernoulli's principle as well as geometry to measure total pressure...but you may be asking, what is total pressure. Well, let's take a humble step back to define the types of pressure:

* Static pressure: **another word for atmospheric pressure, are used interchangabely**
* Dyanamic: **the pressure created by moving through the airstream**
* Total pressure: **simply static pressure + dyanamic pressure**

As mentioned, the pitot tube uses the Bernoull's principle and uses it's geometry to bring the air to rest and is now able to measure to air pressure. What it's now measuring is the **total pressure**. Here's a diagram to help you understand how the pitot tube works:
![Pitot Tube Diagram](/lfs-large/pitottube.png)
The pressure sensors measure the total air pressure. For instance, if we we're moving through the airstream at 78m/s. We can calculate the total pressure by first working out the dyanamic pressure:
$$
d = \frac{pu^2}{2}
$$
where:
$$
d = \text{the dynamic pressure}
$$
$$
\text{p = air density}
$$
$$
\text{u = flow speed in m/s}
$$
Today, we'll be substituting those terms with 1.225kg/m3 and 78m/s. When we do that we get a dyanamic pressure of 3726.45 Pa. The last step we need to do to get total pressure is to add it to our static pressure of 101300 Pa $101300+3726.45=105026.45 Pa$

Using this figure we can finally calculate our indicated airspeed with following formula:
$$IAS = \sqrt{\frac{2(p_total - p_static)}{p0}}$$
where:
$$
IAS = \text{the indicated airspeed}
$$
$$
\text{ptotal = total pressure}
$$
$$
\text{pstatic = static pressure}
$$
$$
\text{p0 = air density}
$$
we get an airspeed of 78m/s

Another factor to keep in mind, is that indicated airspeed decreases altitude and less air entering the pitot tube is less difference between the pitot and static pressures. You may be asking, aren't all the air molecules going at the same speed entering the pitot tube so just having fewer air molecules won't affect the airspeed? It may seem right logically, but if we look at the pressure sensor, we will have a better clue:

Lets imagine:
* There are air molecules moving at 78m/s on  the surface
* There are other air molecules at 35,000 ft moving at the same speed

### What would happen?
Let's say there is 100% air molecules at the surface, but there's only 24% air molecules at 35,000 feet. We would only get 24% of the air molecules, so the percieved speed of the air molecules would be 24% of 78m/s in turn making our airspeed lower. This means that if you're
climbing the same airspeed -- let's say 278 knots, a typical climbing speed for mordern airliners, you would need more engine power climbing from 28,000 feet to 35,000 feet than from surface level to 28,000 feet

### What about climbing?
If we're climbing with a constant airspeed, we would have decrease our climb rate or add more power the higher we go higher in altitude due to the fact the indicated airspeed decreases as we climb higher. If we are descending, we would also have to reduce the descent rate or reduce power as the indicated airspeed would increase as we descend in altitude

## True Airspeded (TAS)
True Airspeed is the speed of the aircraft moving through the air, corrected for the pressure difference. Basically it is calculated by various methods:
* Using the Equivalent Airspeed(**EAS**)
* Using the Mach Number(**Mach**)
* Using impact pressure, static pressure and static air temperature

### Using the Equivalent Airspeed
This calculation method is useful for aircraft flying at low speeds, with:
$$
TAS = \frac{EAS}{\sqrt{\frac{p}{p0}}}
$$
where:
$$
TAS = \text{the true airspeed}
$$
$$
EAS = \text{the Equivalent Airspeed}
$$
$$
p = \text{pressure at current altitude}
$$
$$
p0 = \text{pressure at sea level}
$$

**This means if my EAS is 80kts at 750hpa of pressure(10,000ft pressure altitude) then my true airspeed will be 92kts**

### Using the Mach Number
This formula is very useful to calculate the true airspeed if you flying at high speeds:
$$
TAS = a0M\sqrt{\frac{T}{T0}}
$$
where:
$$
TAS = \text{the true airspeed}
$$
$$
a0 = \text{the speed of sound(661kts)}
$$
$$
M = \text{the Mach Number(Mach)}
$$
$$
T = \text{static air temperature in Kelvins}
$$
$$
T0 = \text{sea level temperature in Kelvins(288.15K)}
$$

**This means if my mach number 0.78 and the static air temperature is -61C(pretty typical for 38,000 feet) my true airspeed will be 443kts**

But even better, if we know the mach number and static air temperature, the is a less complex, allbeit a less accurate approximation of the true airspeed with the following formula:
$$
TAS = 39M\sqrt{T}
$$
where:
$$
TAS = \text{the true airspeed}
$$
$$
M = \text{the Mach Number(Mach)}
$$
$$
T = \text{static air temperature in Kelvins}
$$

**If I calculate with this estimate instead,using the parametres of a mach numer 0.78, an air temperature is -61C(pretty typical for 38,000 feet) my true airspeed will be 440kts just 3 knots off the correct answer**

### Using impact pressure, static pressure and static air temperature

We can combine these expressions to get more accurate data, this calculation is never usually performed manually, it's automatically calculated by the air data computer the provide accurate estimations factoring in the wind component. It uses this formula:
$$
TAS = a0\sqrt{\frac{5T}{T0}}[(\frac{q_c}{P}+1)^\frac{2}{7}-1]
$$
where:
$$
TAS = \text{the true airspeed}
$$
$$
a0 = \text{the speed of sound(661kts)}
$$
$$
T = \text{static air temperature in Kelvins}
$$
$$
T0 = \text{sea level temperature in Kelvins(288.15K)}
$$
$$
q_c = \text{impact pressure(dyanamic pressure adjusted for compressibility of air)}
$$
$$
p = \text{static pressure}
$$

I will not go deep into this avenue of calculation but here are some resources if you are interested in that method of calculations:
* [(True airspeed explanation + calculator](https://aerotoolbox.com/airspeed-conversions/)

### What about climbing?
If we were to climb with a constant TAS what would happen is that we would climb at the same rate but our indicated airspeed would decrease. The same rules would apply to a descent but the other way around, as we descend at a specific true airspeed, as we get closer to sea level, our indicated air speed would begin to "catch up" to match our true airspeed


## Mach Number
Mach number is basically how fast you are moving relative to the air in terms of the speed of sound. We all know that is air density decreases, the speed of sound decreases so if I we're to climb at a constant a mach number my climb rate would have to decrease or I'd have to add power to maintain that mach number. Calculating the Mach Number is pretty simple unlike all the other previous types of airspeed. We just use the following formula
$$
M = \frac{TAS}{661}
$$
where:
$$
M = \text{Mach Number}
$$
$$
TAS = \text{True Airspeed}
$$

**For example if I were flying at 443 knots TAS, that means my mach number would be 0.78**

## CAS and EAS
### Calibrated Airspeed
Calibrated airspeed is pretty straightforward. It is when the indicated airspeed is calibrated to be more accurate. There is no calculation for this, just add or subtract the values provided by your plane manufacturer(usually found in the Pilots Operating Handbook).

It also possible to calculate CAS with EAS if you wish. The formula is:
$$
{\displaystyle CAS={EAS\times \left[1+{\frac {1}{8}}(1-\delta )M^{2}+{\frac {3}{640}}(1-10\delta +9\delta ^{2})M^{4}\right]}}
$$
where:
$$
\delta = \frac{p}{p0}
$$
$$
M = \text{the Mach Number(Mach)}
$$

For reference:
$$
p = \text{pressure at current altitude}
$$
$$
p0 = \text{pressure at sea level}
$$


### Equivalent Airspeed 
EAS can be obtained using
* Dyanamic pressure
* Mach Number
* TAS

#### Using Mach Number
It can be obtained with Mach Number using the following formula:
$$
EAS={a_{0}}M{\sqrt  {P \over P_{0}}}
$$
where:
$$
a0 = \text{the speed of sound(661kts)}
$$
$$
p = \text{pressure at current altitude}
$$
$$
p0 = \text{pressure at sea level}
$$
$$
M = \text{the Mach Number(Mach)}
$$

#### Using Dyanamic Pressure
It can also be obtained using dyanamic pressure using the following formula:
$$
EAS={\sqrt  {{\frac  {2q}{\rho _{0}}}}}
$$
$$
q = \text{dyanamic pressure}
$$
$$
p0 = \text{pressure at sea level}
$$

#### Using TAS
It can also be obtained from true airspeed using the following formula:
$$
EAS=TAS\times {\sqrt  {{\frac  {\rho }{\rho _{0}}}}}
$$
where:
$$
TAS = \text{the true airspeed}
$$
$$
p = \text{pressure at current altitude}
$$
$$
p0 = \text{pressure at sea level}
$$