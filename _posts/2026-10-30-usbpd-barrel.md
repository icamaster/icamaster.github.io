---
title: "USB-C PD Barrel Adapter"
date: 2026-10-30
image: images/USBPD_BARREL/usbpd-barrel-in-use.jpg
tag: "USB-C PD Barrel Adapter"
blurb: >-
  Wall plug adapter for the DER EE DE-5000, which takes any USB-C PD compliant power source. 
---

I recently wanted to use my DE-5000 LCR meter, but the 9V battery that was inside had died. I then had to waste time going out to buy a 9V battery, as I didn't have the right wall plug adapter. After I was done with it, I remembered Mike Harrison's video on ["USBCing all the things"](https://www.youtube.com/watch?v=BElU9LPbaA8) and decided to do the same.  

I did not want to modify my LCR meter internally, in case I decide to sell it later on, so the obvious solution was for the adapter to have a barrel plug, instead of a jack. Annoyingly, the DE-5000 doesn't use that standard 5.5x2.1/2.5 barrel, but a thin one, 3.5x1.35 (dimensions in mm). Since I used the [WCH CH224A](https://www.wch-ic.com/products/CH233.html) integrated circuit, the schematic and PCB were simple enough to do. I decided to use solderable jumpers for the config pins, in case I want to change the output voltage later for other purposes. 

You can see the schematic below, courtesy of [Kicanvas](https://kicanvas.org). Unfortunately, the table with the jumper options doesn't render correctly, so check out the [PDF schematic](https://raw.githubusercontent.com/icamaster/usbpd-barrel/refs/tags/v1.0/outputs/usbpd-barrel_v1.0.pdf) if you're interested in that. 

<script>
  try {
    if (!localStorage.getItem("kc:prefs:theme"))
      localStorage.setItem("kc:prefs:theme", JSON.stringify({ val: "kicad" }));
  } catch (e) {}
</script>
<script type="module" src="/vendor/kicanvas/kicanvas.js"></script>
<div class="kicanvas-wrap">
  <kicanvas-embed controls="full" theme="kicad" style="height: 600px;">
    <kicanvas-source src="https://raw.githubusercontent.com/icamaster/usbpd-barrel/refs/tags/v1.0/usbpd-barrel.kicad_pro"></kicanvas-source>
    <kicanvas-source src="https://raw.githubusercontent.com/icamaster/usbpd-barrel/refs/tags/v1.0/usbpd-barrel.kicad_sch"></kicanvas-source>
    <kicanvas-source src="https://raw.githubusercontent.com/icamaster/usbpd-barrel/refs/tags/v1.0/usbpd-barrel.kicad_pcb"></kicanvas-source>
  </kicanvas-embed>
</div><br>

The only thing that is missing is some overvoltage protection. I wanted to keep it simple, however my friend Steven mentioned that Vishay's SIP32440 would be a perfect fit, and he is totally right. If I ever do a revision, I'll definitely add that in. Alternative, you can use the STMicroelectronic STUSB4531, which has VUSB monitoring and undervoltage / overvoltage protections included, but it's not as simple to use as the CH223.

Below you can see some pictures of the PCB assembly. 

<div class="figure-row">
{% include figure.html
   src="/images/USBPD_BARREL/usbpd-barrel-assembly-top.JPG"
   caption="usbpd-barrel - assembly top" %}
{% include figure.html
   src="/images/USBPD_BARREL/usbpd-barrel-assembly-bot.JPG"
   caption="usbpd-barrel - assembly bot" %}
</div>

I also decided to use a piece of shrink tube over the board, and the yellow matches perfectly with my LCR meter.

{% include figure.html
   src="/images/USBPD_BARREL/usbpd-barrel-in-use.jpg"
   caption="usbpd-barrel - in use" %}

That's it, enjoy!