# Hardware Overview

The XTS hardware is actually difficult to define, it being made up of both the physical hardware and software objects that represent hardware concepts. 

Essentially we split into the following elements:

1. Module
2. NCT Module
3. Part
4. Track

Each of these plays a part in the operation of an XTS and so requires objects in the framework even if they are only conceptual, like a track.

To facilitate understanding the following definnitions apply:

## Module

A module, is a physical motor module, like an [AT2000](https://www.beckhoff.com/en-en/products/motion/xts-linear-product-transport/at2xxx-ath2xxx-xts-motor-modules/at2000.html), these are the elements used to create an XTS system. They have numerous diagnostic and status information for the physical system. They have a direct equivalent class to represent them and retrieve and process this data. The definition of a module class is [here](./Module%20Class.md).

## NCT Module

Like a module an NCT module is defined as a physical motor module with the NCT extension like the [AT2100](https://www.beckhoff.com/en-en/products/motion/xts-linear-product-transport/at2xxx-ath2xxx-xts-motor-modules/at2100.html). These have the same features as the module, but with the added extra of managing the NCT power and communication section. The definition of a NCT module class is [here](./NCT%20Module%20Class.md).

## Part

A part is a software element that represents a group of modules. A part can be made up of 1 or many modules.
They are the basis of the XTS ability to switch tracks with Track Management System (TMS). A system must have at least 1 part. The definition of a Part class is [here](./Part%20Class.md).

## Track

Finally a track is another software component, without a real physical equivalent. A track is a group of parts which are defined as creating a path for movers. A system must have at least 1 track. The definition of a Track class is [here](./Track%20Class.md).
