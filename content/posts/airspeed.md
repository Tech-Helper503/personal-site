---
title: "Airspeed Calculations"
date: 2023-07-11T08:18:45Z
draft: true
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

## Indicated Airspeed(IAS)
Indicated Airspeed is measured by the pitot and static ports on a plane. The pitot tube is placed directly into the airflow. The pitot tube takes advantage of Bernoulli's principle as well as geometry to measure total pressure...but you may be asking, what is total pressure. Well, let's take a humble step back to define the types of pressure:

* Static pressure: **another word for atmospheric pressure, are used interchangabely**
* Dyanamic: **the pressure created by moving through the airstream**
* Total pressure: **simply static pressure + dyanamic pressure**

As mentioned, the pitot tube uses the Bernoull's principle and uses it's geometry to bring the air to rest and is now able to measure to air pressure. What it's now measuring is the **total pressure**. Here's a diagram to help you understand how the pitot tube works:
![Pitot Tube Diagram](/lfs-large/pitottube.png)
The pressure sensors measure the total air pressure. For instance, if we we're moving through the airstream at 78m/s. We can calculate the total pressure by first working out the dyanamic pressure:
$$
\frac{pu^2}{2}
$$
where:
$$
\text{p = air density}
$$
$$
\text{u = flow speed in m/s}
$$
Today, we'll be substituting those terms with 1.225kg/m3 and 78m/s. When we do that we get a dyanamic pressure of 3726.45 Pa. The last step we need to do to get total pressure is to add it to our static pressure of 101300 Pa $101300+3726.45=105026.45 Pa$

Using this figure we can finally calculate our indicated airspeed with following formula:
$$\sqrt{\frac{2(p_total - p_static)}{p0}}$$