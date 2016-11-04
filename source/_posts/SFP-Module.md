---
title: SFP Module_Limiting & Linear Interface
date: 2016-08-22 13:10:14
tags:
- SFP
- limiting, linear
- Direct Attach Cable
- jitter
categories:
- Technology
---
There are always saying two different types of SFP+ Modules, limiting and linear, as well as Direct Attach Cable (DAC). What is the difference and relationship between? 
According to [Wikipedia](https://en.wikipedia.org/wiki/Small_form-factor_pluggable_transceiver#cite_note-15):
SFP+ modules can be described as 'limiting' or 'linear' types; this describes the functionality of the inbuilt electronics. 
- Limiting SFP+ modules include a signal amplifier to re-shape the (degraded) received signal whereas linear ones do not. 
- Linear modules are mainly used with the low bandwidth standards such as [10GBASE-LRM](https://en.wikipedia.org/wiki/10_Gigabit_Ethernet#10GBASE-LRM); otherwise, limiting modules are preferred.
<!-- more-->


## SFP+ design
A detail explaination of limiting and linear module are descripbed in the article [*The road to SFP+: Examining module and system architectures*](http://www.lightwaveonline.com/articles/2008/01/the-road-to-sfp-examining-module-and-system-architectures-54884162.html). 
See below figure


Current Module, `Limiting Module` variant, includes a laser driver, a TOSA, a ROSA, and a **limiting amplifier**. The other variant, `Linear Module`, is majorly intended for 10G Ethernet LRM applications, requires a linear optical receiver path. The third is `Retimed Module` which is compliant with SFP+, it integrates CDR funtionality within the Tx and/or Rx path and resolves signal integrity challenges to many high-speed systems.
{% asset_img sfpdesign.png Three variants of SFP+ design %}

## Trasmission Design
In transmit direction, there is no difference between limiting and linear module. SFP specification has not requirement for ASIC/SerDes but only at point B. More information check [link](http://www.lightwaveonline.com/articles/2008/01/the-road-to-sfp-examining-module-and-system-architectures-54884162.html).

## Receive Design
In receive direction, three variants are significantly differ.

- **Limiting interface**, a binary 1/0 decision is made in amplitude but not in time. This results in squaring of the waveform, but jitter from the signal after O-to-E conversion is still present at the SFP+ connector. This is reflected in the limiting output jitter specification for Fibre Channel and Ethernet (draft values 0.71 UIpp and 0.7 UIpp, Â­respectively). 


- The second receive interface type is called the **Linear interface** because the entire input path is kept linear so electronic dispersion compensation (EDC) ICs on the host board can attempt to recover highly impaired signals. This module type is primarily targeted at 10-Gigabit Ethernet LRM applications, where signals must be sent over long distances of legacy multimode fiber. In the case of a linear interface, the received eye can be totally closed, making jitter measurements in terms of UI not meaningful.
  The linear module type shifts the majority of the standard compliance onto the host board since 1/0 decisions are not made within the module at all.
  *Linear modules also typically have lower gain than limiting modules, making output amplitudes smaller and potentially more difficult for hosts to recover. *

## Direct Attach Cable
In [SFF-8431](ftp://ftp.seagate.com/sff/SFF-8431.PDF), SFP+ compliant hosts are permitted to support just linear modules, just limiting modules, or both linear and limiting modules. Linear modules are modules which contain a linear receiver. Limiting modules are modules which contain a limiting receiver. Although not required, host supporting linear specification are encouraged to support 10GSFP+Cu direct attach cables (Appendix E). For other copper variants see SFF-8461.
{% asset_img copper_cable.jpg Copper Cable structure %}


## Jitter measurement
Related specification only provides requirement of jitter at B point. There are many factors contributes the jitter. As shown in figure below, They include 
 
 * 1) ASIC/SerDes output jitter (includes silicon performance, IC package, etc.); 
 * 2) ASIC/SerDes pre-emphasis set point accuracy and variation; 
 * 3) SFI channel loss with variation (temperature, humidity, manufacturing, etc.); 
 * 4) SFI channel return loss with variation; and 
 * 5) crosstalk, which can be a source of pulsewidth shrinkage (PWS). 
{% asset_img jitter.png Jitter %}

Deterministic jitter is combination of the above contributors plus optical module. ** WHat is [deterministic jitter](http://www.ieee802.org/3/ba/public/jan09/li_01_0109.pdf) **. In the lab test, total jitter may be less than individual measured jitter, so the determinstic jitter is cancling out. 