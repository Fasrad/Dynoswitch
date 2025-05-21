# Dynoswitch
An auxiliary power system for bicycle dynamo hubs

The Dynoswitch is a relay box for bicycle dynamo lighting systems which senses whenever the dynamo hub spins, and turns on a separate auxiliary battery.    

When the the bike starts rolling, the box switches on the auxiliary 12V power, and everything plugged into the Dynoswitch turns on automatically. Currently this includes my front and rear cameras, some extra lights in addition to my normal dynamo lights, a USB socket for charging my phone, and in the winter, handlebar grip heaters. 

The Dynoswitch automatically turns everything off when I stop riding, just like the dynamo hub, but it has its own adjustable delay timer distinct from the dyamo lights' standlights. I have it set to stay on for 3 minutes, and my extra lights also stay full brightness while standing. 

The box doesn't draw any power from the dynamo hub. It just senses the dynamo voltage as a signal to turn itself on. When not riding, the stand-by drain on the aux battery is insignificant (about 20 micro-Amps). When riding, the load on the dynamo circuit is negligible. 

The 12V lights stay on steady and full brightness even when walking the bike, riding super slowly, or pushing the bike up a hill, which is a nice bonus where dynamo lights fall short. However, I still have the dynamo lights, which are completely separate, so I never have to worry about riding in the dark. But for me it would be worth it using this system even simply by using the dynamo hub to trigger the 12V, with no actual dynamo lights.

The circuit will work with any type of auxiliary battery above 4V, but the USB port doesn't work unless the battery voltage is at least 6 or 7 volts. I normally use 12V lithium batteries because then I can run 12V motorcycle or car accessories. The Dynoswitch has a voltmeter on it, so I can tell at a glance how charged the battery is. 

The Dynoswitch has a low-voltage protection feature designed to protect 3-cell unprotected lithium batteries, like drill batteries or R/C car batteries. This prevents over-discharging and damaging the batteries. When the battery protection kicks in, the box turns itself off, but you can manually bypass the protection circuit and continue using it for a while thereafter (like a reserve gas tank). If you are using something that doesn't need voltage protection, like protected 18650 cells, or one of those 12V LiFePo RV batteries that have their own battery management, or a battery of some other voltage, you can just leave the battery protection circuit bypassed all the time. 

You can also override the dynamo hub sensing itself, and just manually turn the box on. This could be good if the dynamo hub breaks or something, or if you just want to use the Dynoswitch as a power center without any dynamo at all. 

I normally run my Dynoswitch on Milwaukee M12 drill batteries. They are cheap, light, and use  a convenient charger. I used to use 12V LiPo batteries from RC cars, thinking that should be the lightest possible thing. But even though LiPo batteries have huge power-to-weight ratio, their capacity-to-weight ratio isn't actually any better than the drill batteries. The drill batteries come in 3Ah, 6Ah, and 9Ah but I normally use the smallest ones which last like a week, and just bring an extra one if needed. 

The dynamo lights are normal and still work off the dynamo in the normal way. If I take the auxiliary circuit off the bike, or the battery runs dead, the dynamo lights will always keep working like normal. And conversely, if I took the dynamo lights off the bike, the 12V system would still work as long as the dynamo hub were still there to trigger it. The Dynoswitch doesn't put any load on the dynamo hub, so even while charging my phone at 800mA, running 12V headlight and taillight, running front and rear cameras, and running 60W grip heaters, there is no extra rolling resistance. 

People have asked why doesn't the dynamo hub recharge the 12V battery, but the whole point of the Dynoswitch was to get more power than the 6W dynamo hub can provide, including more energy than the hub can provide over time, but still have that "just works", zero-effort convenience of dynamo lights that come on and off automatically. 

Other people have asked what's the point of having a dynamo hub at all, when I could just use battery lights. First of all, a dynamo hub is optional, because the Dynoswitch has a mechanical switch to turn it on or off. But I like having high-powered lights that work automatically like dynamo lights. And since I still have the dynamo lights I can't accidentally run a battery down and get stranded in the dark. 

The switching circuit is not completely custom, but is built from 2 different relay modules commonly available on Amazon or eBay. The first one is a comparator  / relay module that uses an LM335 comparator to sense the generator hub voltage and switch on a 12V automotive relay. The comparator  draws effectively no power from the generator hub, so the normal generator lights are not impacted and there's no increased rolling resistance. The comparator does draw a tiny bit of standby power from the 12V battery, on the order of micro-amps, which is less than the battery self-discharge, so there's no problem leaving the bike sitting for weeks or morths. 

The second module is a low-voltage dropout module that cuts the battery off if battery voltage drops below 10 volts. By putting a low-voltage cutoff on the bike, I can use any 12V battery I want and not have to worry about damaging it. When the voltage gets below 10V, the relay simply shuts off the battery. 

The two relay modules are stacked inside a 3D-printed case. No separate logic is needed to implement the turn-off delay. When the bike stops, the rectifying capacitor gradually discharges itself through the comparator's input bias current until the relay clicks off. This delay time can be adjusted with the Vref potentiometer on the relay board (and size of the capacitor). 

JST XH connectors are what I have, because they are used for 3D printers. They are polarized and keyed for size, but they are only rated for 3 Amps per pin, which is marginal for bigger 12V loads. I used a 6-pin JST connector for the 12V battery input, with three pins being for positive and 3 pins for negative, with a 10A main fuse. This also codes that header as the input for the battery. I used 4-pin headers for all the other generic 12V loads, which are interchangeable, and I used a 2-pin header for the generator input. This makes it impossible to hook it up wrong. Each plug only fits into the correct location. 

Because of the use of connectors, the 12V system can mostly be de-installed from my normal commuter bike at any time, leaving just the wire and JST connector on the standard generator lights. It's harder to de-install the cameras and lights of course, but the battery, fuse and hardware switch can be pulled out and used for something else, like another bike. 

Why did I make this at all? I love dynamo lights but there are a few downsides of dynamo lights as they are typically realized:

1) generator lights just aren't very bright. They are bright enough to see where you are going, but nothing like the other motorcycle lights, scooter lights, eBike lighs, or car lights out on the road. Brighter lights would help visibility on the big fast roads we have to deal with around here. 
2) generator lights don't stay on very long at stoplights. They stay on for about a minute, and during that time, they are very dim. This means when you are sitting at a stoplight or stop sign, where you particularly need lights to help your visibility, your lights are even weaker than normal, and there's a risk they will turn off completely. 
3) There's not much power available for running any other accessories. Most generator hubs put out 2 or 3 Watts. This is enough for bike lights, but that's about it. Some people use generator power to trickle charge phones or standby batteries, and that can be help extend your phone battery on long rides, but considering most phones charge at 20W or more nowadays, you can see that 3W is not enough power to really charge up a phone or run any accessory lights. With my auxiliary battery on the other hand I can now fully charge my phone off my auxiliary battery at full speed, even with the bike stationary if I want to. 

In the winter time, when I need to go to work in the dark, I used to supplement my generator lights with a second set of normal battery lights, and throw a travel charger in my bag for the phone. But I had all the same problems I've always had...the battery lights would run out of energy at a bad tim, or I would forget to turn them off and run them down, forget to even turn them on, have to stop and turn them on in the evening when it got darker, etc. 

I also installed heated handgrips at various times, powered by a separate 12V battery. Heated handgrips are amazing! Since I had this 12V battery anyway, I thought wouldn't it be nice if I could use the 12V battery for my lights, and have them come on and off with the dynamo hub, and that's Dynoswitch. 


