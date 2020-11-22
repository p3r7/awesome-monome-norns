# Awesome monome norns


<div align=center><img src="https://monome.org/images/norns-front-small.jpg" width="500"></div>

A list of links and resources for the [_norns_][hw norns doc] hardware music platform by [_monome_](https://monome.org/).

The community resides mostly on [llllllll.co](https://llllllll.co/) (pronounced _lines_).

<!-- https://llllllll.co/t/norns-dust/14015 -->
<!-- https://llllllll.co/t/ash-a-small-collection/21349 -->


## Table of Contents

- [What / why is _norns_?](#what--why-is-norns)
- [What can it do?](#what-can-it-do)
- [Hardware](#hardware)
  - [_norns shield_](#norns-shield)
  - [_monome_ hardware companions](#monome-hardware-companions)
  - [Other hardware companions](#other-hardware-companions)
- [Apps](#apps)
  - [List](#list)
  - [By I/O](#by-io)
- [_Pure Data_](#pure-data)
- [Development: General](#development-general)
  - [Documentation](#documentation)
  - [Tutorials & example apps](#tutorials--example-apps)
  - [Community](#community)
- [Development: Libraries & Engines](#development-libraries--engines)
  - [_Softcut_ & _Softcut_-based libs](#softcut--softcut-based-libs)
  - [_SuperCollider_ engines](#supercollider-engines)
  - [Lua libs](#lua-libs)
- [Development: C](#development-c)
- [Contributing](#contributing)
- [License](#license)


## What / why is _norns_?

_norns_ is a hardware music platform.

It's built around the idea of community: creating and sharing ideas in the form of small _apps_.

It allows running apps built with [_SuperCollider_](https://supercollider.github.io/) and/or **_softcut_**, a powerful live sampler / player.

In addition, [_Pure Data_](https://puredata.info/) patches can also be run (see [_Pure Data_](#pure-data)).

It runs Linux and is built around the Raspberry Pi (processing unit + USB ports) but uses a separate low-latency audio codec chip (ADC/DAC).

For more details, see [_the docs_][hw norns doc] and the [t/Approaching: norns][hw norns lines] thread, specifically posts:
 - [day 1: what](https://llllllll.co/t/approaching-norns/13236/126)
 - [day 2: specifications](https://llllllll.co/t/approaching-norns/13236/213)
 - [day 3: sound](https://llllllll.co/t/approaching-norns/13236/241)
 - [day 4: design](https://llllllll.co/t/approaching-norns/13236/320)
 - [day 5: code](https://llllllll.co/t/approaching-norns/13236/386)
 - [day 6: many tomorrows](https://llllllll.co/t/approaching-norns/13236/516)


## What can it do?

A more correct question would be _"What can it **be**?"_.

Switching apps allows going into totally different contexts.

Some are inspired by existing hardware / software, others are totally new and sometimes produce very experimental (yet musical) results.

To give you some concrete examples, _norns_ can be:
 - an analogue-sounding synth with **_molly_the_poly_**, a pimped up Juno-6 emulation
 - a 4 track tape recorder / looper with **_reels_**
 - chainable multieffects with **_pedalboard_**
 - an advanced sequencer with **_takt_**, inspired with the Electron Octatrack
 - a nasty sounding sample player with **_timber/keys_** (MPC-like) **_timber/player_** (rompler-like)

For a more complete list, see the [Apps](#apps) section.


## Hardware

There are 3 variations of the norns hardware:

| name                                                                   | audio path  | case                                                     | battery | audio monitor output | supported Raspberry Pi models | price point           | releases          |
| ---                                                                    | ---         | ---                                                      | :---:   | :---:                | ---                           | ---                   | ---               |
| [_norns_][hw norns lines] ([shop][hw norns shop])                      | cleanest \* | 2x aluminum block (hard anodized), custom caps & buttons | ✔       | ✔                    | CM3, CM3+                     | $800 / $680 (b-stock) | instant           |
| [_norns shield_][hw norns-shield lines] ([shop][hw norns-shield shop]) | clean       | basic acrylic face & back plates / DIY                   | ❌      | ✔                    | 3B, 3B+                       | $200 \*\*             | instant           |
| [_fates_][hw fates lines]                                              | cleanest \* | acrylic / DIY                                            | ❌      | ✔                    | 3B, 3B+, 4                    | n/a                   | with delay \*\*\* |

\*: the original _norns_ and _fates_ have an isolated audio power section which is much more immune to noise.

\*\*: to which must be added the price of the Raspberry Pi, micro SD card, power supply and eventually better case. So you're eventually looking more at ≃$300.

\*\*\*: _fates_ runs on an unofficial fork of the _norns_ software, with its own kernel, so update cycles run behind the official releases given there is a separate maintainer.

As of writting, all 3 versions are compatible with every app published.

_norns shield_ is currently the most economic version but is DIY and lacks some of the features of its big brother. It's design is [open source][hw norns-shield diy lines].

_fates_ is an unofficial project similar to the _norns shield_, not initiated by monome.

_norns_ and _norns shield_ use a CS4270 codec. _norns_ uses an additional amp chip to drive a monitor (headphone) output. _fates_ uses a WM8731 codec which embeds an headphone amp chip.


#### _norns shield_

For getting help regarding assembly please use [t/DIY: norns shield][hw norns-shield diy lines].

The case provided in kits is pretty minimal. People share their design of more rugged version in [t/norns shield case designs](https://llllllll.co/t/norns-shield-case-designs/30347).

A few highlights:
 - [nice 3D printing STL design](https://llllllll.co/t/norns-shield-case-designs/30347/224) by [u/JHC](https://llllllll.co/u/JHC) that complements the stock faceplate ([shop](https://llllllll.co/t/fs-ww-norns-shield-cases-3d-printed/36711/1)).
 - [nice laser-cut designs](https://llllllll.co/t/norns-shield-case-designs/30347/183) by [u/okyeron](https://llllllll.co/u/okyeron) ([shop](https://denki-oto.weebly.com/store/p39/norns-shield-case.html#/)).
 - [aluminium case](https://llllllll.co/t/fates-ww-commerce-thread/27165/79) by [u/Gregory_Delabelle](https://llllllll.co/u/Gregory_Delabelle) ([shop](https://docs.google.com/forms/d/e/1FAIpQLScJTDVgXTqiN6HnZBpKS0v8VNfar2rGikTGkOw3MjDAJp-1GQ/viewform)).
 - [simple laser cut front & back panels](https://github.com/infovore/norns-diy-panels) by [u/infovore](https://llllllll.co/u/infovore/summary).

If you don't have access to a fablab, you can use a laser-cut service such as [ponoko](https://www.ponoko.com/) (US) or [razorlab](https://razorlab.online/) (UK).

For encoder caps, any D-shaft knob cap should fit.

You can look at makers such as Sifam / Selco, the various offerings at aliexpress ([example](https://www.aliexpress.com/item/32781327404.html?spm=2114.13010708.0.0.3a994c4dQ4Aov1)) or even go the [3D printing route](https://llllllll.co/t/diy-norns-shield/27638/876).

For screws/spacers, use M2 for the screen and M2.5 for everything else.


#### _monome_ hardware companions

Some apps are made to pair with some of other _monome_ hardware.

The most prominent are:
 - [_grid_][hw grid doc], a keyboard mostly used for sequencer _apps_
 - [_arc_][hw arc doc], an array of knobs with sequencing functionalities
 - [_crow_][hw crow doc] for interacting with eurorack / modular synth gear

You don't necessarily have to own any of those "peripherals" to enjoy your _norns_. It depends of the _apps_ you plan to use.

See [the list of _apps_ by I/O](https://github.com/p3r7/awesome-monome-norns#by-io) to see what you're missing.

Please note that most _apps_ assume a 128 varybright grid. Older non-varybright models will work but you'll be missing some visual feedback.

There is a [DIY _grid_ project][hw grid-neotrellis lines] that allows making one for ≃$250. To use it with the _norns_, patching and recompiling is required to have it recognized. It will work right of the bat on a PC (with _Max_, _Pure Data_...). It doesn't (and will certainly never) work with eurorack _monome_ modules such as [_ansible_][hw ansible doc].

There is also a [DIY arc project][hw arc-diy src] which will also cost ≃$250. It does not require any special patching.


#### Other hardware companions

Synth _apps_ generally rely on MIDI inputs. So a keyboards, pads or sequencer is a must have. A computer with midi output will do as well.

Lots of parameters can also be controlled with midi CC by using anything with midi knobs / sliders.

Some examples related to the _monome_ community:
 - [16n faderbank][hw 16n site]
 - [bleached][hw bleached lines], [Four-N][hw Four-N lines] and [17][hw 17 lines]

Some trackers _apps_ (_orca_ and _nisp_) rely on a USB computer keyboard.

Those plus other hardware accessories & peripherals are discussed in [t/Friends of norns: gear, accessories, etc](https://llllllll.co/t/friends-of-norns-gear-accessories-etc/17150).


## Apps

#### List

Many apps are available through [maiden](https://monome.org/docs/norns/maiden/) ([real-time list](https://raw.githubusercontent.com/monome/norns-community/master/community.json)) but many more are missing.

The [documentation has a list of popular apps](https://monome.org/docs/norns/app/).

This section is aimed at being more complete and providing more meta-data to select which app corresponds to your needs.


Synths & drones:

| app                                          | on maiden | code                          | description                                                                                                 | demo                                               | doc                   |
| ---                                          | :---:     | ---                           | ---                                                                                                         | ---                                                | ---                   |
| [ash/earthsea][app ash lines]                | ✔️         | [gh][app ash src]             | PolySub engine. Also acts as a sequencer with grid.                                                         |                                                    |                       |
| [benjolis][app benjolis lines]               | ✔️         | [gh][app benjolis src]        | port of Alejandro Olarte’s Benjolis SuperCollider patch, inspired from Rob Hordijk’s Benjolin               | [1][app benjolis demo 1], [2][app benjolis demo 2] |                       |
| [dronecaster][app dronecaster lines]         | ✔️         | [gh][app dronecaster src]     | various drones                                                                                              | [1][app dronecaster demo 1]                        |                       |
| [fm7][app fm7 lines]                         | ✔️         | [gh][app fm7 src]             | DX7-inspired polyphonic FM synth                                                                            | [1][app fm7 demo 1]                                | [online][app fm7 doc] |
| [grendy][app grendy lines]                   | ✔️         | [gh][app grendy src]          | a simple drone synth, grendel drone commander inspired                                                      |                                                    |                       |
| [hachi][app hachi lines]                     | ✔️         | [gh][app hachi src]           | TR-808 reproduction with euclydian sequencer                                                                |                                                    |                       |
| [haven][app haven lines]                     | ✔️         | [gh][app haven src]           | two unique oscillators: one high, one low                                                                   | [1][app haven demo 1]                              |                       |
| [lissadron][app lissadron lines]             | ✔️         | [gh][app lissadron src]       | a software synth making extensive use of seeded randomness, internal sequencer for voice change             | [internal sequencer][app lissadron demo seq]       |                       |
| [mi-eng/macro-b][app mi-eng lines]           | ❌️️        | [gh][lib mi-engines gh sc]    | collection of complex oscillator sources, based upon the Mutable Instrument Braids macro-oscillator         | [1][app mi-eng/macro-b demo 1]                     |                       |
| [mi-eng/macro-p][app mi-eng lines]           | ❌️️        | [gh][lib mi-engines gh sc]    | collection of complex oscillator sources, based upon the Mutable Instrument Plaits macro-oscillator         | [1][app mi-eng/macro-p demo 1]                     |                       |
| [mi-eng/modal-e][app mi-eng lines]           | ❌️️        | [gh][lib mi-engines gh sc]    | modal synth, based upon the Mutable Instrument Elements                                                     | [1][app mi-eng/modal-e demo 1]                     |                       |
| [mi-eng/resonate-r][app mi-eng lines]        | ❌️️        | [gh][lib mi-engines gh sc]    | ring resonator, can be used as basic percusive oscillator, based upon the Mutable Instrument Rings          | [1][app mi-eng/resonate-r demo 1]                  |                       |
| [molly_the_poly][app molly_the_poly lines]   | default️   | [gh][app molly_the_poly src]  | Juno-6 voice structure with chorus, the extra modulation of a Jupiter-8, and CS-80 inspired ring modulation | [1][app molly_the_poly demo 1]                     |                       |
| [moln][app moln lines]                       | ✔️         | [gh][app moln src]            | Polyphonic substractive synthesizer                                                                         |                                                    |                       |
| [passersby][app passersby lines]             | ✔️         | [gh][app passersby src]       | Wave folding, FM, LPG, spring-ish reverb, LFO and two dice to roll                                          | [1][app passersby demo 1]                          |                       |
| [rudiments][app rudiments lines]             | ✔️         | [gh][app rudiments src]       | 8 voice lofi percussion synthesizer and sequencer (playfair-style)                                          |                                                    |                       |
| [showers][app showers lines]                 | ✔️         | [gh][app showers src]         | a thunderstorm (rain & thunder)                                                                             |                                                    |                       |
| [stjoernuithrott][app stjoernuithrott lines] | ✔️         | [gh][app stjoernuithrott src] | drone synth inspired by the Moffeenzeef Stargazer                                                           |                                                    |                       |
| [there][app there lines]                     | ❌️        | [gh][app there src]           | a theremin                                                                                                  |                                                    |                       |


Granular sample players and synths:

| app                        | on maiden | code                 | description                                                                              | demo                     | doc |
| ---                        | :---:     | ---                  | ---                                                                                      | ---                      | --- |
| [ash/angl][app ash lines]  | ✔️         | [gh][app ash src]    | use an arc to control pitch and speed granulation of four audio files                    | [1][app ash/angl demo 1] |     |
| [glut][app glut lines]     | ✔️         | [gh][app glut src]   | granular synth inspired by mlr/rove, [grainfield][app grainfield lines] & loomer cumulus | [1][app glut demo 1]     |     |
| [gemini][app gemini lines] | ✔️         | [gh][app gemini src] | one file, two granulators                                                                | [1][app gemini demo 1]   |     |
| [langl][app langl lines]   | ❌️         | [gh][app langl src]  | ash/angl-inspired granulator, also uses arc and offer more control                       | [1][app langl demo 1]    |     |
| [mangl][app mangl lines]   | ✔️         | [gh][app mangl src]  | a 7 track granular sample player                                                         | [1][app mangl demo 1]    |     |
| [uhf][app uhf lines]       | ✔️         | [gh][app uhf src]    | your tapes transmitted thru late-night static and broken antenna frequencies             |                          |     |


Sample players:

| app                               | on maiden | code                    | description                                                  | demo                                                                | doc |
| ---                               | :---:     | ---                     | ---                                                          | ---                                                                 | --- |
| [beets][app beets lines]          | ✔         | [gh][app beets src]     | drum loop slicer / player                                    | [1][app beets demo 1], [2][app beets demo 2], [3][app beets demo 3] |     |
| [crash][app crash lines]          | ✔         | [gh][app crash src]     | random drum kit player (606 samples)                         |                                                                     |     |
| [drum_room][app drum_room lines]  | ✔         | [gh][app drum_room src] | MIDI-controlled drum kits                                    | [1][app drum_room demo 1]                                           |     |
| [timber/keys][app timber lines]   | ✔         | [gh][app timber src]    | map a sample at different pitches  across midi keys / grid   | [1][app timber/keys demo 1]                                         |     |
| [timber/player][app timber lines] | ✔         | [gh][app timber src]    | load whole directory of samples mapped onto midi keys / grid | [1][app timber/player demo 1]                                       |     |


Basic samplers:

| app                  | on maiden | code              | description                                     | demo | doc |
| ---                  | :---:     | ---               | ---                                             | ---  | --- |
| [sam][app sam lines] | ✔         | [gh][app sam src] | record, adjust start & end points, save to tape |      |     |


Sequencers:

| app                                                | on maiden | code                        | description                                                                         | demo                                                             | doc                                   |
| ---                                                | :---:     | ---                         | ---                                                                                 | ---                                                              | ---                                   |
| [animator][app animator lines]                     | ✔️         | [gh][app animator src]      | 2D polyphonic sequencer for grids                                                   | [1][app animator demo 1], [2][app animator demo 2]               | [online][app animator doc]            |
| [arcologies][app arcologies lines]                 | ✔️         | [gh][app arcologies src]    | interactive environment for designing 2d sound arcologies                           | [gallery][app arcologies demos]                                  | [online][app arcologies doc]          |
| [arp_index][app arp_index lines]                   | ✔️         | [gh][app arp_index src]     | generate sequence from company stocks                                               | [1][app arp_index demo 1]                                        |                                       |
| [ash/earthsea][app ash lines]                      | ✔️         | [gh][app ash src]           | grid-enabled shape-memory pattern instrument                                        |                                                                  |                                       |
| [ash/playfair][app ash lines]                      | ✔️         | [gh][app ash src]           | euclidean drummer, four sequences, each with its own sample                         | [1][app ash/playfair demo 1]                                     |                                       |
| [awake][app awake lines]                           | default   | [gh][app awake src]         | two looped sequences                                                                | [1][app awake demo 1]                                            |                                       |
| [boing][app boingg lines]                          | ✔         | [gh][app boingg src]        | a bouncing ball sequencer                                                           | [1][app boingg demo 1]                                           |                                       |
| [buoys][app buoys lines]                           | ✔         | [gh][app buoys src]         | kinetic sequencer based on motion of water                                          | [1][app buoys demo 1]                                            |                                       |
| [cheat_codes][app cheat_codes lines]               | ✔️         | [gh][app cheat_codes src]   | sample playground                                                                   | [1][app cheat_codes demo 1]                                      | [pdf][app cheat_codes doc]            |
| [circles][app circles lines]                       | ✔️         | [gh][app circles src]       | move cursor, place circles, make music                                              | [1][app circles demo 1]                                          |                                       |
| [cyrene][app cyrene lines]                         | ✔️         | [gh][app cyrene src]        | drum pattern generator                                                              | [1][app cyrene demo 1], [grid][app cyrene demo grid]             |                                       |
| [dunes][app dunes lines]                           | ✔         | [gh][app dunes src]         | function sequencer, inspired by [spacetime][app spacetime study]                    | [audio][app dunes demo audio], [midi][app dunes demo midi]       |                                       |
| [drift][app drift lines]                           | ❌        | [gh][app drift src]         | sequencer based on particle systems                                                 | [midi][app drift demo midi]                                      |                                       |
| [euclidigons][app euclidigons lines]               | ✔️         | [gh][app euclidigons src]   | plucky geometric rhythm generator                                                   | [1][app euclidigons demo 1], [2][app euclidigons demo 2]         |                                       |
| [foulplay][app foulplay lines]                     | ✔️         | [gh][app foulplay src]      | euclidean drummer, inspired by [ash/playfair][app ash lines]                        | [1][app foulplay demo 1]                                         | [online][app foulplay doc]            |
| fretwork                                           | ️❌        | [gh][app fretwork src]      | ornamental sequencer                                                                | [1][app fretwork demo 1]                                         |                                       |
| [fugu][app fugu lines]                             | ✔         | [gh][app fugu src]          | 4 playhead sequencer, inspired by the Fugue Machine iOS app                         | [1][app fugu demo 1], [2][app fugu demo 2], [3][app fugu demo 3] |                                       |
| [grd][app grd lines]                               | ❌️        | [gh][app grd src]           | 8x8 autonomy                                                                        | [1][app grd demo 1], [2][app grd demo 2]                         |                                       |
| [gridstep][app gridstep lines]                     | ❌️        | [gh][app gridstep src]      | step-based 16-track polyphonic sequencer with various grid layouts and micro-timing | [1][app gridstep demo 1]                                         | [online][app gridstep doc]            |
| [islands][app islands lines]                       | ✔️         | [gh][app islands src]       | kria-based sequencer with internal playback                                         | [1][app islands demo 1]                                          | [presentation video][app islands doc] |
| [isoseq][app isoseq lines]                         | ✔️         | [gh][app isoseq src]        | isomorphic step sequence                                                            | [1][app isoseq demo 1]                                           | [presentation video][app islands doc] |
| [kria_midi][app kria_midi lines]                   | ✔️         | [gh][app kria_midi src]     | port of the kria sequencer with midi output                                         | [1][app kria_midi demo 1], [1][app kria_midi demo 2]             |                                       |
| [less_concepts][app less_concepts lines]           | ✔️         | [gh][app less_concepts src] | cellular automata sequencer                                                         | [1][app less_concepts demo 1]                                    |                                       |
| [loom][app loom lines]                             | ✔️         | [gh][app loom src]          | pattern weaving sequencer for grids                                                 | [1][app loom demo 1], [2][app loom demo 2]                       |                                       |
| [meadowphysics][app meadowphysics lines]           | ✔️         | [gh][app meadowphysics src] | grid-enabled rhizomatic cascading counter                                           | [1][app meadowphysics demo 1]                                    | [online][app meadowphysics doc]       |
| [nono][app nono lines]                             | ❌️        | [gh][app nono src]          | Nanoloop-inspired 4 channel sequencer                                               | [1][app nono demo 1]                                             |                                       |
| [orbital][app orbital lines]                       | ❌️        | [gh][app orbital src]       | circular 16 step sequencer                                                          |                                                                  |                                       |
| [orca][app orca lines]                             | ✔️         | [gh][app orca src]          | esoteric programming language                                                       | [1][app orca demo 1], [2][app orca demo 2]                       |                                       |
| [patchwork][app patchwork lines]                   | ✔️         | [gh][app patchwork src]     | dual function (note + command patterns) sequencer                                   | [1][app patchwork demo 1]                                        |                                       |
| [punchcard][app punchcard lines]                   | ✔️         | [gh][app punchcard src]     | experimental sequencer that works like a classic punchcard computer                 | [1][app punchcard demo 1], [2][app punchcard demo 2]             |                                       |
| [qfwfq][app qfwfq lines]                           | ✔️         | [gh][app qfwfq src]         | sequencer inspired by brute force password hacking                                  |                                                                  |                                       |
| [quence][app quence lines]                         | ✔️         | [gh][app quence src]        | a probabilistic 4-track sequencer                                                   | [1][app quence demo 1], [2][app quence demo 2]                   |                                       |
| [rebound][app rebound lines]                       | ✔️         | [gh][app rebound src]       | a kinetic sequencer                                                                 | [1][app rebound demo 1]                                          |                                       |
| [spacetime][app spacetime study] `we/study/study3` | ✔️         |                             | a weird function sequencer                                                          | [1][app spacetime demo 1]                                        |                                       |
| [step][app step lines]                             | ✔️         | [gh][app step src]          | a simple step sequencer                                                             |                                                                  |                                       |
| [strides][app strides lines]                       | ✔️         | [gh][app step src]          | sample or midi pattern sequencer                                                    | [1][app strides demo 1]                                          | [online][app strides doc]             |
| [strum][app strum lines]                           | ✔️         | [gh][app strum src]         | 16-step sequencer w/ a variety of pattern transition mechanisms                     | [1][app strum demo 1]                                            |                                       |
| [takt][app takt lines]                             | ✔️         | [gh][app takt src]          | Digitakt-inspired parameter locking step sequencer                                  | [1][app takt demo 1]                                             | [online][app takt doc]                |
| [tambla][app tambla lines]                         | ✔️         | [gh][app tambla src]        | Arpgegio sequencer                                                                  |                                                                  | [online][app tambla doc]              |
| [torii][app torii lines]                           | ✔️         | [gh][app torii src]         | gated audio sequencer                                                               | [1][app torii demo 1], [2][app torii demo 2]                     |                                       |
| [vials][app vials lines]                           | ✔️         | [gh][app vials src]         | 4 track performance-oriented sample sequencer                                       |                                                                  | [online][app vials doc]               |
| [zeelen][app zeelen lines]                         | ✔️         | [gh][app zeelen src]        | game of Life based sequencer                                                        | [1][app zeelen demo 1], [crow][app zeelen demo crow]             | [online][app takt doc]                |


Trackers:

| app                              | on maiden | code                    | description                              | demo                                                 | doc                         |
| ---                              | :---:     | ---                     | ---                                      | ---                                                  | ---                         |
| [nisp][app nisp lines]           | ✔️         | [gh][app nisp src]      | LISP (Scheme dialect) livecoding tracker | [1][app nisp demo 1], [2][app nisp demo 2]           |                             |
| [yggdrasil][app yggdrasil lines] | ✔️         | [gh][app yggdrasil src] | "cyberdeck" tracker                      | [1][app yggdrasil demo 1], [2][app yggdrasil demo 2] | [online][app yggdrasil doc] |


Control Modulation sources:

| app                                | on maiden | code                     | description                                         | demo                                               | doc |
| ---                                | :---:     | ---                      | ---                                                 | ---                                                | --- |
| [barycenter][app barycenter lines] | ❌        | [gh][app barycenter src] | fluctuating relationships in orbit                  |                                                    |     |
| [buoys][app buoys lines]           | ✔️         | [gh][app buoys src]      | its midi output mode produces abstract midi CC LFOs |                                                    |     |
| [cccccccc][app cccccccc lines]     | ✔️         | [gh][app cccccccc src]   | 8 LFOs as MIDI CC output, arc-controlled            | [1][app cccccccc demo 1], [1][app cccccccc demo 2] |     |
| [changes][app changes lines]       | ✔️         | [gh][app changes src]    | 8 connected sine wave LFOs as MIDI CC output        | [1][app changes demo 1], [2][app changes demo 2]   |     |
| [shapes][app shapes lines]         | ❌        | [gh][app shapes src]     | visually based modulation source for crow           |                                                    |     |
| [strides][app strides lines]       | ✔         | [gh][app strides src]    | allows midi CC record / replay with knobs           |                                                    |     |


Audio effects:

| app                                   | on maiden | code                       | description                                                               | demo                              | doc |
| ---                                   | :---:     | ---                        | ---                                                                       | ---                               | --- |
| [greyhole][app greyhole lines]        | ✔️         | [gh][app greyhole src]     | echo / delay                                                              | [1][app greyhole demo 1]          |     |
| [manifold][app manifold lines]        | ✔️         | [gh][app manifold src]     | multi-effects processing for live performance                             | [1][app manifold demo 1]          |     |
| [mi-eng/modal-e][app mi-eng lines]    | ❌️        | [gh][lib mi-engines gh sc] | modal synth, affects input audio, based upon the Mutable Instrument Rings | [1][app mi-eng/modal-e demo 1]    |     |
| [mi-eng/resonate-r][app mi-eng lines] | ❌️        | [gh][lib mi-engines gh sc] | ring resonator, based upon the Mutable Instrument Rings                   | [1][app mi-eng/resonate-r demo 1] |     |
| [pedalboard][app pedalboard lines]    | ✔️         | [gh][app pedalboard src]   | chainable effects for live performance                                    |                                   |     |
| [phyllis][app phyllis lines]          | ✔️         | [gh][app phyllis src]      | digitally modeled analog                                                  | [1][app phyllis demo 1]           |     |
| [pools][app pools lines]              | ✔️         | [gh][app pools src]        | a shimmery reverb                                                         | [1][app pools demo 1]             |     |
| [stack][app stack lines]              | ✔️         | [gh][app stack src]        | stack of bandpass filter, sequenceable                                    |                                   |     |
| [sway][app sway lines]                | ✔️         | [gh][app sway src]         | analysis-driven live audio processing                                     | [1][app sway demo 1]              |     |
| [timeparty][app timeparty lines]      | ✔️         | [gh][app timeparty src]    | sequenced time-based multi-effect                                         |                                   |     |


Loopers, live samplers & crazy delays:

| app                                    | on maiden | code                       | description                                                                            | demo                                                                                       | doc                     |
| ---                                    | :---:     | ---                        | ---                                                                                    | ---                                                                                        | ---                     |
| [ash/orbit][app ash lines]             | ✔️         | [gh][app ash src]          | dual async start-stop loop recorder                                                    |                                                                                            |                         |
| [barcode][app barcode lines]           | ✔️         | [gh][app barcode src]      | a randomized looper                                                                    | [1][app barcode demo 1]                                                                    |                         |
| [b-b-b-b-beat][app b-b-b-b-beat lines] | ✔️         | [gh][app b-b-b-b-beat src] | beat repeater/glitcher inspired by Ableton's Beat Repeat, MASF Possessed & MWFX Judder | [1][app b-b-b-b-beat demo 1]                                                               |                         |
| [blndr][app blndr lines]               | ✔️         | [gh][app blndr src]        | a quantized delay with time bending effects                                            | [1][app blndr demo 1]                                                                      |                         |
| [bounds][app bounds lines]             | ✔️         | [gh][app bounds src]       | kinetic stere looper / delay, _otis_ with _rebound_ mechanics                          | [1][app bounds demo 1]                                                                     |                         |
| [clcks][app clcks lines]               | ✔️         | [gh][app clcks src]        | a tempo-locked repeater                                                                | [1][app clcks demo 1]                                                                      |                         |
| [compass][app compass lines]           | ✔️         | [gh][app compass src]      | asynchronous looper, with command-based sequencer                                      | [1][app compass demo 1]                                                                    |                         |
| [cranes][app cranes lines]             | ✔️         | [gh][app cranes src]       | stereo varispeed looper / delay / timeline-smoosher                                    | [1][app cranes demo 1]                                                                     | [video][app cranes doc] |
| [here-there][app here-there lines]     | ✔️         | [gh][app here-there src]   | feedback of granular replay and sines                                                  |                                                                                            |                         |
| [glitchlets][app glitchlets lines]     | ❌️        | [gh][app glitchlets src]   | glitches incoming audio, quantized to the global tempo                                 | [1][app glitchlets demo 1]                                                                 |                         |
| [jiffy][app jiffy lines]               | ✔️         | [gh][app jiffy src]        | 16 seconds looper                                                                      |                                                                                            |                         |
| [mi-eng/texture-c][app mi-eng lines]   | ❌️        | [gh][lib mi-engines gh sc] | realtime granualr audio processor, based upon the Mutable Instrument Rings             | [1][app mi-eng/texture-c demo 1]                                                           |                         |
| [mlr][app mlr lines]                   | ✔️         | [gh][app mlr src]          | live sample-cutting platform                                                           | [1][app mlr demo 1], [2][app mlr demo 2]                                                   |                         |
| [oooooo][app oooooo lines]             | ✔️         | [gh][app oooooo src]       | digital tape loops x6                                                                  | [1][app oooooo demo 1], [2][app oooooo demo 2]                                             |                         |
| [otis][app otis lines]                 | ✔️         | [gh][app otis src]         | dual tape delay/looper/sampler                                                         | [1][app otis demo 1]                                                                       |                         |
| [piwip][app piwip lines]               | ✔️         | [gh][app piwip src]        | a sampler that works in realtime                                                       | [1][app piwip demo 1], [2][app piwip demo 2], [3][app piwip demo 3], [4][app piwip demo 4] |                         |
| [reels][app reels lines]               | ✔️         | [gh][app reels src]        | a 4-track asynchronous looper                                                          | [1][app reels demo 1]                                                                      |                         |
| [samsara][app samsara lines]           | ✔️         | [gh][app samsara src]      | minimalist looper that eventually reaches nirvana                                      |                                                                                            |                         |
| [tunnels][app tunnels lines]           | ✔️         | [gh][app tunnels src]      | a collection of uncertain delays                                                       | [1][app tunnels demo 1]                                                                    |                         |


Midi effects:

| app                                    | on maiden | code                    | description                               | demo                                                             | doc |
| ---                                    | :---:     | ---                     | ---                                       | ---                                                              | --- |
| [athenaeum/delay][app athenaeum lines] | ❌        | [gh][app athenaeum src] | generates MIDI delay with visual feedback | [1][app athenaeum/delay demo 1], [2][app athenaeum/delay demo 2] |     |


Utilities:

| app                                    | on maiden | code                       | description                                                   | demo                                             | doc |
| ---                                    | :---:     | ---                        | ---                                                           | ---                                              | --- |
| [athenaeum/arc][app athenaeum lines]   | ❌        | [gh][app athenaeum src]    | interract with arc, read and write leds, no sound             | [1][app athenaeum/arc demo 1]                    |     |
| [caliper][app caliper lines]           | ✔         | [gh][app caliper src]      | tuner for eurorack modules using _norns_ + _crow_             |                                                  |     |
| [clarck][app clarck lines]             | ✔         | [gh][app clarck src]       | use _arc_ as a clock to display time                          | [1][app clarck demo 1]                           |     |
| [foundry][app foundry lines]           | ❌        | [gh][app foundry src]      | browse all glyphs of all installed fonts, play with options   |                                                  |     |
| [grid-test][app grid-test lines]       | ❌        | [gh][app grid-test src]    | utility to test grids                                         | [1][app grid-test demo 1]                        |     |
| [librarian][app librarian lines]       | ❌️        | [gh][app librarian src]    | install, update and remove apps directly                      |                                                  |     |
| [midimatrix][app midimatrix lines]     | ❌️        | [gh][app midimatrix src]   | simple midi matrix example app                                |                                                  |     |
| [midi-monitor][app midi-monitor lines] | ✔️         | [gh][app midi-monitor src] | simple midi monitor with note feedback                        | [1][app midi-monitor demo 1]                     |     |
| [monitor][app monitor lines]           | ✔️         | [gh][app monitor src]      | midi monitor and input/output channel & note transpose        | [1][app monitor demo 1], [2][app monitor demo 2] |     |
| [n16o][app n16o lines]                 | ✔️         | [gh][app n16o src]         | turn a Korg nanoKONTROL2 into an ER-301 controller            |                                                  |     |
| [norman][app norman lines]             | ✔️         | [gh][app norman src]       | normalize & auto-trim sample files on disk                    |                                                  |     |
| [norns.online][app norns.online lines] | ✔️         | [gh][app norns.online src] | expose norns screen and buttons/encodeers to the internet     | [1][app norns.online demo 1]                     |     |
| [onehanded][app onehanded lines]       | ✔️         | [gh][app onehanded src]    | simple MIDI note / CC trigger                                 |                                                  |     |
| [practice][app practice lines]         | ❌️        | [gh][app practice src]     | musical scale quizz                                           |                                                  |     |
| [rpmate][app rpmate lines]             | ❌️        | [gh][app rpmate src]       | utility to help feeding a sped up audio to a hardware sampler |                                                  |     |
| [seaflex][app seaflex lines]           | ✔  ️       | [gh][app seaflex src]      | practice chords shapes on grid, _earthsea_ layout             |                                                  |     |
| [shell_runner][app shell_runner lines] | ❌  ️      | [gh][app shell_runner src] | menu to launch shell scripts                                  |                                                  |     |
| [tuner][app tuner lines]               | ✔️         | [gh][app tuner src]        | a tuner                                                       |                                                  |     |


#### By I/O

| symbol | meaning             |
| :---:  | ---                 |
| ✔️      | yes                 |
| 🔴     | mandatory           |
| 🔶     | strongly encouraged |
| ⚪     | optional            |


| app                                                | audio in | midi sync | midi in | keyboard | grid   | arc   | audio out | midi out | crow  |
| ---                                                | :---:    | :---:     | :---:   | :---:    | :---:  | :---: | :---:     | :---:    | :---: |
| [ash/angl][app ash lines]                          |          |           |         |          |        | 🔴    | ✔         |          |       |
| [ash/earthsea][app ash lines]                      |          |           | ✔       |          | ⚪     |       | ✔         |          | ✔     |
| [ash/orbit][app ash lines]                         | ✔        |           |         |          |        |       | ✔         |          |       |
| [ash/playfair][app ash lines]                      |          | ⚪        |         |          |        |       | ✔         |          |       |
| [athenaeum/arc][app athenaeum lines]               |          |           |         |          |        | 🔴    |           |          |       |
| [athenaeum/delay][app athenaeum lines]             | ✔        |           |         |          |        |       |           | ✔        |       |
| [arcologies][app arcologies lines]                 |          |           |         |          | 🔴     |       | ✔         | ✔        | ✔     |
| [arp_index][app arp_index lines]                   |          |           | ⚪      |          |        |       | ✔         |          |       |
| [awake][app awake lines]                           |          | ⚪        |         |          | ⚪     |       | ✔️         |          | ✔️     |
| [barcode][app barcode lines]                       | ✔        |           |         |          |        |       | ✔️         | ️         |       |
| [barycenter][app barycenter lines]                 |          |           |         |          |        |       | ✔️         | ✔️        |       |
| [beets][app beets lines]                           |          | ✔         | ⚪      |          | ⚪     | ⚪    | ✔️         | ️         |       |
| [b-b-b-b-beat][app b-b-b-b-beat lines]             | ✔        | ✔         |         |          |        |       | ✔️         | ️         |       |
| [benjolis][app benjolis lines]                     |          |           |         |          |        |       | ✔️         | ️         |       |
| [boing][app boingg lines]                          |          |           |         |          | ⚪     |       | ✔️         | ✔️        | ✔     |
| [bounds][app bounds lines]                         | ✔        |           |         |          |        |       | ✔️         | ️         |       |
| [buoys][app buoys lines]                           |          | ✔         |         |          | 🔴     | ⚪    | ️✔         | ✔️        | ✔     |
| [caliper][app caliper lines]                       | ✔        |           |         |          |        |       |           |          | ✔     |
| [cccccccc][app cccccccc lines]                     |          |           |         |          |        | 🔴    |           | ✔        |       |
| [changes][app changes lines]                       |          |           |         |          |        |       |           | ✔        |       |
| [cheat_codes][app cheat_codes lines]               |          |           |         |          | 🔶 \** | 🔶    |           |          |       |
| [circles][app circles lines]                       |          |           |         |          |        |       | ✔         | ✔        |       |
| [clarck][app clarck lines]                         |          |           |         |          |        | 🔴    |           |          |       |
| [clcks][app clcks lines]                           | ✔        |           |         |          |        |       | ✔         |          |       |
| [compass][app compass lines]                       | ✔        |           |         |          | ⚪     |       | ✔         |          |       |
| [cranes][app cranes lines]                         | ✔️        |           |         |          | ⚪     |       | ✔️         |          |       |
| [crash][app crash lines]                           | ️         | ?         |         |          |        |       | ✔️         |          |       |
| [cyrene][app cyrene lines]                         | ️         |           |         |          | ⚪     | ⚪    | ️          | ✔        | ✔     |
| [drift][app drift lines]                           |          |           |         |          |        |       | ✔️         | ✔        |       |
| [dronecaster][app dronecaster lines]               |          |           |         |          |        |       | ✔️         |          |       |
| [drum_room][app drum_room lines]                   |          |           | 🔴      |          |        |       | ✔️         |          |       |
| [dunes][app dunes lines]                           |          |           |         |          |        |       | ✔️         |          |       |
| [euclidigons][app euclidigons lines]               |          |           |         |          |        |       | ✔️         | ✔️        |       |
| [foulplay][app foulplay lines]                     |          |           |         |          | 🔶     |       | ✔️         | ✔️        |       |
| fretwork                                           |          |           |         |          | ⚪     |       | ✔️         | ✔️        | ✔     |
| [fm7][app fm7 lines]                               |          |           | 🔶      |          | 🔶     |       | ✔️         |          |       |
| [fugu][app fugu lines]                             |          |           |         |          | 🔴     |       | ✔️         |          |       |
| [gemini][app gemini lines]                         | ️         |           |         |          |        | ⚪    | ✔️         |          |       |
| [glitchlets][app glitchlets lines]                 | ✔        | ⚪        |         |          |        |       | ✔️         |          |       |
| [glut][app glut lines]                             | ️         |           |         |          | 🔶     |       | ✔️         |          |       |
| [grd][app grd lines]                               | ️         |           |         |          |        |       | ✔️         |          |       |
| [greyhole][app greyhole lines]                     | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [grid-test][app grid-test lines]                   | ️         |           |         |          | 🔴     |       | ️          |          |       |
| [gridstep][app gridstep lines]                     | ️         |           |         |          | 🔴     |       | ✔️         | ✔        |       |
| [hachi][app hachi lines]                           | ️         |           |         |          |        |       | ✔️         |          |       |
| [haven][app haven lines]                           | ️         |           |         |          |        |       | ✔️         |          |       |
| [here-there][app here-there lines]                 | ✔        |           |         |          |        |       | ✔️         |          |       |
| [islands][app islands lines]                       |          |           |         |          | 🔶     |       | ✔️         |          |       |
| [isoseq][app isoseq lines]                         |          | ⚪        |         |          | 🔴     |       | ✔️         | ✔        |       |
| [kria_midi][app kria_midi lines]                   |          |           |         |          | 🔶     |       | ✔️         |          |       |
| [langl][app langl lines]                           |          |           |         |          |        | 🔴    | ✔️         |          |       |
| [less_concepts][app less_concepts lines]           |          |           |         |          | 🔶     |       | ✔️         | ✔        | ✔     |
| [librarian][app librarian lines]                   |          |           |         |          |        |       | ️          |          |       |
| [lissadron][app lissadron lines]                   |          |           | 🔶      |          |        |       | ✔️         |          |       |
| [loom][app loom lines]                             |          | ⚪        |         |          | 🔴     |       | ✔️         | ✔        |       |
| [mangl][app mangl lines]                           |          |           |         |          | 🔶     | 🔶    | ✔️         | ️         |       |
| [manifold][app manifold lines]                     | ✔        |           | 🔶      |          |        |       | ✔️         | ️         |       |
| [meadowphysics][app meadowphysics lines]           |          |           |         |          | 🔴     |       | ✔️         | ✔️        |       |
| [mi-eng/macro-b][app mi-eng lines]                 |          |           | ✔       |          |        |       | ✔️         | ️         |       |
| [mi-eng/macro-p][app mi-eng lines]                 |          |           | ✔       |          |        |       | ✔️         | ️         |       |
| [mi-eng/modal-e][app mi-eng lines]                 | ✔        |           | ✔       |          |        |       | ✔️         | ️         |       |
| [mi-eng/texture-c][app mi-eng lines]               | ✔        |           |         |          |        |       | ✔️         | ️         |       |
| [mi-eng/resonate-r][app mi-eng lines]              | ✔        |           | ✔       |          |        |       | ✔️         | ️         |       |
| [midimatrix][app midimatrix lines]                 |          | ✔         |         |          |        |       | ✔️         | ️         |       |
| [midi-monitor][app midi-monitor lines]             |          | ✔         |         |          |        |       | ✔️         | ️         |       |
| [mlr][app mlr lines]                               | ✔️        |           |         |          | 🔴     |       | ✔️         |          |       |
| [molly_the_poly][app molly_the_poly lines]         |          |           | 🔴 \*   |          | ⚪ \*  |       | ✔️         |          |       |
| [moln][app moln lines]                             |          |           | 🔴 \*   |          | ⚪ \*  | ⚪    | ✔️         |          |       |
| [monitor][app monitor lines]                       |          | ✔         |         |          |        |       | ️          | ✔️        |       |
| [n16o][app n16o lines]                             |          |           | 🔴      |          |        |       | ️          |          | ✔     |
| [nisp][app nisp lines]                             |          |           |         | 🔴       |        |       | ✔️         |          |       |
| [nono][app nono lines]                             |          |           |         |          |        |       | ✔️         | ✔        |       |
| [norman][app norman lines]                         |          |           |         |          |        |       | ️          |          |       |
| [norns.online][app norns.online lines]             |          |           |         |          |        |       | ️          |          |       |
| [onehanded][app onehanded lines]                   | ️         |           |         |          |        |       | ️          | ✔        |       |
| [oooooo][app oooooo lines]                         | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [orbital][app orbital lines]                       | ️         |           |         |          |        |       | ✔️         |          |       |
| [orca][app orca lines]                             | ✔️        |           | ✔       | 🔴       | ⚪     |       | ✔️         | ✔        |       |
| [otis][app otis lines]                             | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [passersby][app passersby lines]                   |          |           | 🔴 \*   |          | ⚪ \*  |       | ✔️         |          |       |
| [patchwork][app patchwork lines]                   |          |           |         | 🔴       | 🔴     |       |           | ✔️        | ✔️     |
| [pedalboard][app pedalboard lines]                 | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [piwip][app piwip lines]                           |          |           |         |          |        |       |           |          |       |
| [pools][app pools lines]                           | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [practice][app practice lines]                     |          |           |         |          |        |       |           | ️         |       |
| [punchcard][app punchcard lines]                   |          |           |         |          | 🔴     |       |           | ✔️        |       |
| [qfwfq][app qfwfq lines]                           |          | ⚪        |         |          |        |       | ✔         | ✔️        |       |
| [quence][app quence lines]                         |          |           |         |          | 🔴     |       | ✔         | ✔️        | ✔     |
| [rebound][app rebound lines]                       | ️         | ⚪        |         |          |        |       | ️          | ✔        |       |
| [reels][app reels lines]                           | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [rpmate][app rpmate lines]                         | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [rudiments][app rudiments lines]                   | ️         |           |         |          | ⚪     |       | ✔️         |          |       |
| [seaflex][app seaflex lines]                       |          |           |         |          | 🔴     |       | ✔         |          |       |
| [shapes][app shapes lines]                         |          |           |         |          |        |       |           |          | ✔     |
| [shell_runner][app shell_runner lines]             |          |           |         |          |        |       |           |          |       |
| [spacetime][app spacetime study] `we/study/study3` |          |           |         |          |        |       | ✔️         |          |       |
| [step][app step lines]                             |          |           |         |          | 🔴     | ⚪    | ✔️         |          |       |
| [stjoernuithrott][app stjoernuithrott lines]       |          |           | ⚪      |          |        |       | ✔️         |          |       |
| [strides][app strides lines]                       |          |           | ✔️       |          | 🔴     |       | ✔️         | ✔️        |       |
| [strum][app strum lines]                           |          | ⚪        | ✔️       |          | 🔴     |       | ✔️         | ✔️        |       |
| [takt][app takt lines]                             |          |           |         |          | 🔴     |       | ✔️         |          |       |
| [tambla][app tambla lines]                         |          |           | 🔴 \*️   |          | ⚪ \*  |       | ✔️         | ✔        |       |
| [there][app there lines]                           |          |           |         |          |        |       | ✔️         |          |       |
| [timber/keys][app timber lines]                    |          | ⚪        | 🔴 \*   |          |        |       | ✔️         |          |       |
| [timber/player][app timber lines]                  |          | ⚪        | 🔴 \*   |          | ⚪ \*  |       | ✔️         |          |       |
| [timeparty][app timeparty lines]                   | ✔        | ⚪        |         |          | 🔴     |       | ✔️         |          | ⚪    |
| [torii][app torii lines]                           |          |           |         |          | ⚪     |       | ✔️         |          |       |
| [tuner][app tuner lines]                           | ✔        |           |         |          |        |       | ️          |          |       |
| [uhf][app uhf lines]                               |          |           |         |          |        |       | ✔️         |          |       |
| [vials][app vials lines]                           |          |           |         |          | 🔶     |       | ✔️         |          |       |
| [yggdrasil][app yggdrasil lines]                   |          | ⚪        |         | 🔴       |        |       | ✔️         | ✔        | ✔     |
| [zeelen][app zeelen lines]                         |          |           |         |          | 🔴     |       | ✔️         | ✔        | ✔     |

Special cases:

 - \*: grid acts as a midi keyboard and can replace it
 - \**: grid can be replaced by TouchOSC


## _Pure Data_

[_Pure Data_](https://puredata.info/) patches originally built for the [_Organelle_](https://www.critterandguitari.com/organelle) can run on any _norns_ device.

This is done by escaping the norns runtime environment and booting into a _Pure Data_-compatible one.

Please note that [next release](https://llllllll.co/t/approaching-3-0-universal-engine-support/25255/1) of the _norns_ software will add native support of _Pure Data_, akin to what we currently have with _SuperCollider_.

This is easily done thanks to the combination of 2 projects:

 - _Sidekick_ by [u/thetechnobear](https://llllllll.co/u/thetechnobear/summary) that allows booting out of the _norns_ software and into other ones ([lines thread](https://llllllll.co/t/orac-sidekick-pure-data-and-sc-for-norns/26198))
 - _Mother_ by [u/oxbown](https://llllllll.co/u/oxbown/summary) that provides a compatibility layer for running Organelle patches ([lines thread](https://llllllll.co/t/norns-mother-organelle-patches-on-norns/30237))

In addition, installing _Sideckick_ also provides:

 - _Orac_: a patch chaining software for _Pure Data_
 - _NuiLite_: a lightweight _Pure Data_ _external_ (i.e. extension) for making and running patches without depending on the _Organelle/Mother_ or _Orac_ layer.

For more details, see also the [the _Sidekick_ project wiki](https://github.com/TheTechnobear/NuiLite/wiki).


## Development: General

The _norns_ platform allows developing small programs using the [lua](https://www.lua.org/) programming language.

They are generally referred to as _scripts_, and _apps_ once packaged and distributed.

2 internal sound processing units are at our disposal:

 - `engine`: an instance of [SuperCollider](https://supercollider.github.io/) (sometimes also referred to as `external`)
 - `softcut`: a live multi-channel sampler / player that can be used to build crazy loopers and delays

<div align=center><img src="https://monome.org/docs/norns/image/norns-audio-route.png" width="750"></div>

Even though _SuperCollider_ is generally used to define a virtual synthesizer, it can also take audio from the inputs (missing on the above diagram).

Most scripts you'll find in the wild use either _softcut_ or _engine_, but some might use the 2 of them.


#### Documentation

 - [basic lua scripting reference](https://monome.org/docs/norns/reference/)
 - [complete lua APIs doc](https://monome.org/docs/norns/api/)


#### Tutorials & example apps

 - [norns studies](https://monome.org/docs/norns/studies-landing/)
 - [norns: tutorial](https://llllllll.co/t/norns-tutorial/23241) by [Devine Lu Linvega](https://xxiivv.com/)
 - [softcut studies](https://github.com/monome/softcut-studies)
 - [foundry][app foundry lines] app ([code][app foundry src]) for text & fonts (`screen.text` API)
 - [athenaeum/arc][app athenaeum lines] app ([code][app athenaeum src]) for arc interactions
 - [hid-demo][app hid-demo lines] example apps ([code][app hid-demo lines]) for HID input (keyboard, mouse, touchpad...)
 - [waveviz][app waveviz src] example app for _softcut_ waveform visualization
 - [video tutorial on adding midi out to an existing app](https://llllllll.co/t/norns-walkthrough-hacking-a-script-to-add-midi-output/34969)
 - [tutorial on adding computer keyboard support to an existing app](https://llllllll.co/t/norns-without-a-grid/32996/28)
 - [example usage of the `pattern_time` lib](https://llllllll.co/t/norns-pattern-class-examples/32166/2)


#### Community

When wanting to contribute or seeking help, use one of those threads:

 - [t/norns: scripting](https://llllllll.co/t/norns-scripting/14120): getting help with app development (lua)
 - [t/norns 2.0: softcut](https://llllllll.co/t/norns-2-0-softcut/20550): getting help with app development (softcut)
 - [t/norns: SuperCollider](https://llllllll.co/t/norns-supercollider/22822): getting help with app development (SuperCollider side)
 - [t/norns: development](https://llllllll.co/t/norns-development/14073) and [t/Approaching 3.0: universal engine support](https://llllllll.co/t/approaching-3-0-universal-engine-support/25255/1): following and participating to evolutions to core norns code
 - [t/norns: crone/supercollider](https://llllllll.co/t/norns-crone-supercollider/14616): following and participating to evolutions to core norns code (SuperCollider / Crone)
 - [t/Exquisite Script: A collective scripting game for norns](https://llllllll.co/t/exquisite-script-a-collective-scripting-game-for-norns/34989): a cadavre exquis, collective development of an app

Additionally, there is a [Discord norns study group](https://discord.com/invite/hfC5Fmw) ([lines thread](https://llllllll.co/t/discord-norns-study-group/14233)) that meets regularly for sharing development knowledge.



## Development: Libraries & Engines

When developing apps/scripts, you rely on lua libraries (classes & modules). One of them, _engine_, allows interacting with a running _SuperCollider_ instance.

When using _SuperCollider_, one can rely on an already installed _SuperCollider_ library on spin their own. Those _SuperCollider_ libraries (in essence a _SynthDef_) are called _engines_ in the context of **norns** development.

Most advanced apps come with their own custom libraries / engine.

Here are listed the ones most often spotted in the wild.


#### _Softcut_ & _Softcut_-based libs

| library                        | code                                                       | description                         | provided by          | used by              |
| --                             | ---                                                        | ---                                 | ---                  | ---                  |
| [softcut][lib softcut lines]   | [lua][lib softcut gh lua], [undelying C][lib softcut gh C] | sample record & playback            | installed by default | sam, reels, piwip    |
| [supercut][lib supercut lines] | [lua][lib supercut gh lua]                                 | higher-level wrapper around softcut |                      | wrms                 |
| halfsecond                     | [lua][lib halfsecond gh]                                   | simple 1/2s delay                   | awake                | awake, vials, tambla |


#### _SuperCollider_ engines

To get the list of engines installed on your _norns_, type `tab.print(engine.names)` in the _matron_ console in _maiden_.

| library                            | code                                                                         | description                                                                        | provided by                                | used by                                                         |
| --                                 | ---                                                                          | ---                                                                                | ---                                        | ---                                                             |
| ack                                | [lua wrapper][lib ack gh lua], [sclang][lib ack gh sc]                       | simple sample playback                                                             |                                            | step, ash/playfair, foulplay, takt, crash, vials, strides       |
| timber                             | [lua wrapper][lib timber gh lua], [sclang][lib timber gh sc]                 | advanced sample playback                                                           | [timber][app timber lines]                 | timber, orca                                                    |
| glut                               | [sclang][lib glut gh sc]                                                     | granular sample playback                                                           | [glut][app glut lines]                     | glut, mangl, uhf, langl                                         |
| PolyPerc                           | [sclang][lib PolyPerc gh sc]                                                 | simple polyphonic filtered decaying square wave                                    | installed by default                       | awake, meadowphysics, barycenter, zeelen, orbital, nono, tambla |
| PolySub                            | [sclang][lib PolySub gh sc]                                                  | multi-type oscillator with polyphonic modulation busses for polytimbral expression | installed by default                       | ash/earthsea                                                    |
| Gong                               | [sclang][lib Gong gh sc]                                                     | basic FM synth                                                                     | installed by default                       |                                                                 |
| TestSine                           | [sclang][lib TestSine gh sc]                                                 | a basic single mono sinewave                                                       | installed by default                       | there                                                           |
| [R][lib R lines]                   | [sclang][lib R gh sc]                                                        | collection of engines that link together in a modular synth-style workflow         | installed by default                       | moln, torii                                                     |
| [mi-engines][lib mi-engines lines] | [lua+scland][lib mi-engines gh sc]                                           | port of Mutable Instruments rack modules                                           | [mi-eng/\*][app mi-eng lines]              | mi-eng/\*                                                       |
| molly_the_poly                     | [lua wrapper][lib molly_the_poly gh lua], [sclang][lib molly_the_poly gh sc] | analogue (substractive) synth                                                      | [molly_the_poly][app molly_the_poly lines] | molly_the_poly, arp_index, loom, quence, fugu                   |
| passersby                          | [lua wrapper][lib passersby gh lua], [sclang][lib passersby gh sc]           | westcoast-style synth                                                              | [passersby][app passersby lines]           | passersby, less_concepts, dunes                                 |
| [Dust2][lib Dust2 lines]           | [sclang][lib Dust2 gh sc]                                                    | impulses (ticks)                                                                   | [bgc_dust][app bgc_dust lines]             | euclidigons                                                     |
| PrimitiveString                    | [sclang][lib PrimitiveString gh sc]                                          |                                                                                    | [euclidigons][app euclidigons lines]       | euclidigons                                                     |


#### Lua libs

Those are more generic Lua libs that add either:
- improve handling of midi / LFOs
- provide support for additional hardware
- provide additional drawing utils


| library                                | code                       | description                                                            | provided by | used by                                            |
| ---                                    | ---                        | ---                                                                    | ---         | ---                                                |
| [passthrough][lib passthrough lines]   | [lua][lib passthrough gh]  | allows norns to pass through midi between connected devices            | passthrough | passthrough, b-b-b-b-beat, beets, stjoernuithrott  |
| midi                                   | [lua][lib midi gh]         | helper to trig MIDI out                                                | euclidigons | euclidigons                                        |
| hnds                                   | [lua][lib hnds gh]         | LFOs to modulate app parameters                                        | otis        | otis, pools, greyhole, pedalboard, wrms, timeparty |
| [nest\_][lib nest_ gh]                 | [lua][lib nest_ gh]        | advanced, callback-based, user interaction definitions, _grid_ support |             |                                                    |
| [arcify][lib arcify lines]             | [lua][lib arcify gh]       | simple parameter binding to _arc_                                      |             | beets, compass                                     |
| [shnth][lib shnth lines]               | [lua][lib shnth gh]        | use the shbobo shnth as a controller                                   |             |                                                    |
| screencap                              | [lua][lib screencap gh]    | animated capture of the screen (into an animated png)                  |             |                                                    |
| [grid-capture][lib grid-capture lines] | [lua][lib grid-capture gh] | capture a _grid_ button press sequence as a gif                        |             |                                                    |
| shape                                  | [lua][lib shape gh]        | draw shapes on screen                                                  | euclidigons | euclidigons                                        |
| noise                                  | [lua][lib noise gh]        | draw perlin Noise on screen                                            |             |                                                    |
| [moreFilters][lib moreFilters lines]   | [lua][lib moreFilters gh]  | provides a moving, windowed RMS/standard deviation filter              |             |                                                    |
| p8                                     | [lua][lib p8 gh]           | pico-8 code adaptation layer                                           |             |                                                    |


## Development: C

A niche use-case is to disable the _norns_ software services and interact with the internal sound routing and hardware peripherals using pure C.

This effort is discussed in [t/low-level-norns](https://llllllll.co/t/low-level-norns/22921).

For a working example with grid and arc support see project [norns-lowlevel](https://github.com/paulbatchelor/norns-lowlevel) ([explanation & demo](https://llllllll.co/t/low-level-norns/22921/37)).


## Contributing

Contributions and suggestions are always welcome!

[I](https://llllllll.co/u/eigen) am by no mean the owner of this document, merely its initiator. It belongs to the community.

To discuss about the general structure and content use [t/Index of norns-related resources](https://llllllll.co/t/index-of-norns-related-resources/37007).

For less impacting modifications / suggestions, you can:
 - submit a pull request
 - create an issue
 - [comment on the lines thread](https://llllllll.co/t/index-of-norns-related-resources/37007)
 - [send me a PM](https://llllllll.co/u/eigen)


## License

[![unlicense](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)


<!-- ====================================================================== -->

<!-- hw: norns -->
[hw norns lines]: https://llllllll.co/t/approaching-norns/13236
[hw norns doc]: https://monome.org/docs/norns/
[hw norns shop]: https://market.monome.org/collections/primary/products/norns
[hw norns-shield lines]: https://llllllll.co/t/approaching-diy-norns-shield/25554
[hw norns-shield shop]: https://market.monome.org/collections/primary/products/norns-shield-kit
[hw norns-shield diy lines]: https://llllllll.co/t/diy-norns-shield/27638
[hw norns-shield case lines]: https://llllllll.co/t/norns-shield-case-designs/30347
[hw fates lines]: https://llllllll.co/t/fates-a-diy-norns-dac-board-for-raspberry-pi/22999
<!-- hw: other monome -->
[hw grid doc]: https://monome.org/docs/grid/
[hw grid-neotrellis lines]: https://llllllll.co/t/diy-monome-compatible-grid-w-adafruit-neotrellis/28106
[hw arc-diy src]: https://github.com/TheSlowGrowth/MonomeArcClone
[hw arc doc]: https://monome.org/docs/arc/
[hw crow doc]: https://monome.org/docs/crow/
[hw ansible doc]: https://monome.org/docs/ansible/
<!-- hw: monome-related -->
[hw 16n site]: https://16n-faderbank.github.io/
[hw bleached lines]: https://llllllll.co/t/bleached-diy-midi-controller/33786
[hw Four-N lines]: https://llllllll.co/t/four-n-128-sized-knob-controller/24
[hw 17 lines]: https://llllllll.co/t/17-diy-teensy-midi-controller/28539


<!-- softcut libs -->
[lib softcut lines]: https://llllllll.co/t/norns-2-0-softcut/20550
[lib softcut gh lua]: https://github.com/monome/norns/blob/main/lua/core/softcut.lua
[lib softcut gh C]: https://github.com/monome/softcut-lib
[lib supercut lines]: https://llllllll.co/t/supercut-lib/29526
[lib supercut gh lua]: https://github.com/andr-ew/supercut
[lib halfsecond gh]: https://github.com/tehn/awake/blob/master/lib/halfsecond.lua

<!-- supercolier libs -->
[lib ack gh lua]: https://github.com/antonhornquist/ack/blob/master/lib/ack.lua
[lib ack gh sc]: https://github.com/antonhornquist/ack/blob/master/lib/Engine_Ack.sc
[lib glut gh sc]: https://github.com/artfwo/glut/blob/master/Engine_Glut.sc
[lib timber gh lua]: https://github.com/markwheeler/timber/blob/master/lib/timber_engine.lua
[lib timber gh sc]: https://github.com/markwheeler/timber/blob/master/lib/Engine_Timber.sc
<!-- [lib PolyPerc gh sc]: https://github.com/tehn/awake/blob/master/lib/Engine_PolyPerc.sc -->
[lib PolyPerc gh sc]: https://github.com/monome/dust/blob/master/lib/sc/Engine_PolyPerc.sc
[lib PolySub gh sc]: https://github.com/monome/dust/blob/master/lib/sc/Engine_PolySub.sc
[lib Gong gh sc]: https://github.com/monome/dust/blob/master/lib/sc/Engine_Gong.sc
[lib TestSine gh sc]: https://github.com/monome/dust/blob/master/lib/sc/Engine_TestSine.sc
[lib molly_the_poly gh lua]: https://github.com/markwheeler/molly_the_poly/blob/master/lib/molly_the_poly_engine.lua
[lib molly_the_poly gh sc]: https://github.com/markwheeler/molly_the_poly/blob/master/lib/Engine_MollyThePoly.sc
[lib passersby gh lua]: https://github.com/markwheeler/passersby/blob/master/lib/passersby_engine.lua
[lib passersby gh sc]: https://github.com/markwheeler/passersby/blob/master/lib/Engine_Passersby.sc
[lib PrimitiveString gh sc]: https://github.com/synthetiv/euclidigons/blob/main/lib/Engine_PrimitiveString.sc
[lib R lines]: https://llllllll.co/t/norns-r-engine/21071
[lib R gh sc]: https://github.com/antonhornquist/r
[lib mi-engines lines]: https://llllllll.co/t/mi-ugens-for-norns/31781
[lib mi-engines gh sc]: https://github.com/okyeron/mi-eng
[lib Dust2 lines]: https://llllllll.co/t/bgc-dust/32033
[lib Dust2 gh sc]: https://github.com/bgc/bgc_dust/blob/master/engine/Engine_bgcDust.sc

<!-- lua libs -->
[lib arcify lines]: https://llllllll.co/t/arcify/22133
[lib arcify gh]: https://github.com/mimetaur/arcify
[lib arcify doc]: https://mimetaur.github.io/arcify/
[lib hnds gh]: https://github.com/justmat/otis/blob/master/lib/hnds.lua
[lib grid-capture lines]: https://llllllll.co/t/grid-capture/33158
[lib grid-capture gh]: https://github.com/tlubke/GridCapture
[lib screencap gh]: https://github.com/tlubke/capture
[lib nest_ gh]: https://github.com/andr-ew/nest_
[lib passthrough lines]: https://llllllll.co/t/passthrough/31156
[lib passthrough gh]: https://github.com/nattog/passthrough
[lib midi gh]: https://github.com/synthetiv/euclidigons/blob/main/lib/midi.lua
[lib shape gh]: https://github.com/synthetiv/euclidigons/blob/main/lib/shape.lua
[lib shnth lines]: https://llllllll.co/t/norns-shnth-library/33238
[lib shnth gh]: https://github.com/cfdrake/shnth
[lib noise gh]: https://github.com/naus3a/NauNorns/blob/master/lib/noise.lua
[lib moreFilters lines]: https://llllllll.co/t/rms-filter/36994
[lib moreFilters gh]: https://github.com/naus3a/NauNorns/blob/master/lib/noise.lua
[lib p8 gh]: https://github.com/p3r7/p8

<!-- apps -->
[app athenaeum lines]: https://llllllll.co/t/athenaeum/36660
[app athenaeum src]: https://github.com/tyleretters/athenaeum
[app athenaeum/arc demo 1]: https://www.youtube.com/watch?list=PLe1BFUbUceS0YCUHGYtbKZsl5_MmxlF5f
[app athenaeum/delay demo 1]: https://www.youtube.com/watch?v=ETG9Ixzcp5c
[app athenaeum/delay demo 2]: https://www.instagram.com/p/CF1faQIhlkh/
[app animator lines]: https://llllllll.co/t/animator/28242
[app animator src]: https://github.com/crimclark/animator
[app animator doc]: https://github.com/crimclark/animator/blob/master/README.md
[app animator demo 1]: https://www.instagram.com/p/B6-3E6qlMBa/
[app animator demo 2]: https://www.instagram.com/p/B6GvRIWlSH_/
[app arcologies lines]: https://llllllll.co/t/arcologies-v1-1-15-music-hackspace-workshop-oct-10th/35752
[app arcologies src]: https://github.com/tyleretters/arcologies
[app arcologies doc]: https://tyleretters.github.io/arcologies-docs
[app arcologies demos]: https://tyleretters.github.io/arcologies-docs/gallery
[app arp_index lines]: https://llllllll.co/t/the-arp-index
[app arp_index src]: https://github.com/markwheeler/arp_index
[app arp_index demo 1]: https://www.instagram.com/p/B140GeKB3ga/
[app ash lines]: https://llllllll.co/t/ash-a-small-collection/21349
[app ash src]: https://github.com/tehn/ash
[app ash/angl demo 1]: https://vimeo.com/312196152
[app ash/playfair demo 1]: https://vimeo.com/270668759
[app awake lines]: https://llllllll.co/t/awake
[app awake src]: https://github.com/tehn/awake
[app awake demo 1]: https://vimeo.com/327848801
[app barcode lines]: https://llllllll.co/t/barcode/35297
[app barcode src]: https://github.com/schollz/barcode
[app barcode demo 1]: https://www.instagram.com/p/CDxUwsSh7oP/
[app barycenter lines]: https://llllllll.co/t/barycenter
[app barycenter src]: https://github.com/echophon/barycenter
[app b-b-b-b-beat lines]: https://llllllll.co/t/b-b-b-b-beat-ableton-beat-repeater/35047
[app b-b-b-b-beat src]: https://github.com/frederickk/b-b-b-b-beat/
[app b-b-b-b-beat demo 1]: https://www.instagram.com/p/CDef8pQIRA8/
[app beets lines]: https://llllllll.co/t/beets-1-1-1/30069
[app beets src]: https://github.com/mattb/beets
[app beets demo 1]: https://www.youtube.com/watch?v=inLgAmwhvfI
[app beets demo 2]: https://www.youtube.com/watch?v=AT6j5OpXpuU
[app beets demo 3]: https://www.instagram.com/p/B_LVBBgJ4Gi/
[app benjolis lines]: https://llllllll.co/t/benjolis/28061
[app benjolis src]: https://github.com/scazan/benjolis
[app benjolis demo 1]: https://www.instagram.com/p/B6tJ036BuwC/
[app benjolis demo 2]: https://www.instagram.com/p/B6vAYhEB4Hi/
[app bgc_dust lines]: https://llllllll.co/t/bgc-dust/32033
[app bgc_dust src]: https://github.com/bgc/bgc_dust
[app blndr lines]: https://llllllll.co/t/blndr/35106
[app blndr src]: https://github.com/schollz/blndr
[app blndr demo 1]: https://llllllll.co/t/blndr/35106
[app boingg lines]: https://llllllll.co/t/boingg/26536
[app boingg src]: https://github.com/justmat/boingg
[app boingg demo 1]: https://vimeo.com/368803868
[app bounds lines]: https://github.com/justmat/bounds
[app bounds src]: https://github.com/justmat/boingg
[app bounds demo 1]: https://vimeo.com/342848400
[app buoys lines]: https://llllllll.co/t/buoys/37639
[app buoys src]: https://github.com/lylepmills/buoys
[app buoys demo 1]: https://vimeo.com/472114370
[app caliper lines]: https://llllllll.co/t/caliper/31353
[app caliper src]: https://github.com/synthetiv/caliper/
[app cccccccc lines]: https://llllllll.co/t/cccccccc/22271
[app cccccccc src]: https://github.com/ypxk/cccccccc
[app cccccccc demo 1]: https://www.youtube.com/watch?v=bgwQ0zUg9c4
[app cccccccc demo 2]: https://www.instagram.com/p/BxP9crfAshp/
[app changes lines]: https://llllllll.co/t/changes/33799
[app changes src]: https://github.com/markwheeler/changes/
[app changes demo 1]: https://www.instagram.com/p/CBwHD-ABSSj/
[app changes demo 2]: https://www.instagram.com/p/CCD9ooUjqbi/
[app cheat_codes lines]: https://llllllll.co/t/31655
[app cheat_codes src]: https://github.com/dndrks/cheat_codes
[app cheat_codes doc]: https://llllllll.co/uploads/short-url/mkkpeOUJCreIwVIP0Jdf8rpfYDJ.pdf
[app cheat_codes demo 1]: https://www.youtube.com/watch?v=gfM5MiYKvxc&t=132s
[app circles lines]: https://llllllll.co/t/circles/22951
[app circles src]: https://github.com/JakeCarter/circles
[app circles demo 1]: https://www.instagram.com/p/ByL_pJpha8A/
[app clarck lines]: https://llllllll.co/t/clarck/21251
[app clarck src]: https://github.com/okyeron/clarck
[app clarck demo 1]: https://vimeo.com/22323803
[app clcks lines]: https://llllllll.co/t/clcks/35732
[app clcks src]: https://github.com/schollz/clcks
[app clcks demo 1]: https://www.instagram.com/p/CEWzDaXB6VX/
[app compass lines]: https://llllllll.co/t/compass/25192
[app compass src]: https://github.com/oliviercreurer/compass
[app compass demo 1]: https://llllllll.co/t/compass/25192
[app cranes lines]: https://llllllll.co/t/cranes/21207
[app cranes src]: https://github.com/dndrks/cranes
[app cranes doc]: https://www.youtube.com/watch?v=pVVKC3KnRLg
[app cranes demo 1]: https://www.instagram.com/p/Bv5klu_l9mp/
[app crash lines]: https://llllllll.co/t/crash/35697
[app crash src]: https://github.com/tomwaters/Crash
[app cyrene lines]: https://llllllll.co/t/cyrene-a-drum-sequencer-based-on-mutable-instruments-grids-v1-4-0/31648
[app cyrene src]: https://github.com/21echoes/cyrene
[app cyrene demo 1]: https://www.instagram.com/p/CA7kP8ijizm/
[app cyrene demo grid]: https://www.instagram.com/p/CA7nVs0DUQv/
[app drift lines]: https://llllllll.co/t/drift/36138
[app drift src]: https://github.com/echophon/drift
[app drift demo midi]: https://www.instagram.com/p/CE9ramVKrLO/
[app dronecaster lines]: https://l.llllllll.co/dronecaster
[app dronecaster src]: https://github.com/tyleretters/dronecaster
[app dronecaster demo 1]: https://www.youtube.com/watch?v=sYnHYDg3rhg
[app drum_room lines]: https://llllllll.co/t/drum-room/23467
[app drum_room src]: https://github.com/markwheeler/drum_room
[app drum_room demo 1]: https://www.instagram.com/p/BzBuAq9B961/
[app dunes lines]: https://llllllll.co/t/dunes
[app dunes src]: https://github.com/oliviercreurer/dunes
[app dunes demo audio]: https://llllllll.co/t/dunes/24790
[app dunes demo midi]: https://llllllll.co/t/dunes/24790/18
[app euclidigons lines]: https://llllllll.co/t/euclidigons/36666
[app euclidigons src]: https://github.com/synthetiv/euclidigons/
[app euclidigons demo 1]: https://www.youtube.com/watch?v=o9bUmd2UaYc
[app euclidigons demo 2]: https://www.instagram.com/p/CFkNeIID3e7/
[app fm7 lines]: https://llllllll.co/t/fm7-norns/21395
[app fm7 src]: https://github.com/lazzarello/fm7
[app fm7 doc]: https://github.com/lazzarello/fm7/blob/master/README.md
[app fm7 demo 1]: https://www.youtube.com/watch?v=HI9B-vuWF4A
[app foulplay lines]: https://llllllll.co/t/foulplay/21081
[app foulplay src]: https://github.com/justmat/foulplay
[app foulplay doc]: https://github.com/justmat/foulplay/blob/master/readme.md
[app foulplay demo 1]: https://vimeo.com/328283781
[app foundry lines]: https://llllllll.co/t/foundry/33933
[app foundry src]: https://github.com/csboling/foundry
[app fretwork src]: https://github.com/synthetiv/fretwork
[app fretwork demo 1]: https://www.instagram.com/p/B8-JSEGF-7d/
[app fugu lines]: https://llllllll.co/t/fugu/21033
[app fugu src]: https://github.com/synthetiv/fretwork
[app fugu demo 1]: https://www.instagram.com/p/BrxIZAZFzI7/
[app fugu demo 2]: https://www.instagram.com/p/Btiq_0YlX7Q/
[app fugu demo 3]: https://www.instagram.com/p/Br9UYx3BQkq/
[app gemini lines]: https://llllllll.co/t/gemini/21086
[app gemini src]: https://github.com/mhetrick/gemini/
[app gemini demo 1]: https://www.instagram.com/p/BwOp6t1FVeX/
[app glitchlets lines]: https://llllllll.co/t/glitchlets/37069
[app glitchlets src]: https://github.com/schollz/glitchlets
[app glitchlets demo 1]: https://www.instagram.com/p/CGG1TPdhdCO/
[app glut lines]: https://llllllll.co/t/glut/21175
[app glut src]: https://github.com/artfwo/glut
[app glut demo 1]: https://www.youtube.com/watch?v=uvikPhSNA4U
[app grainfield lines]: https://llllllll.co/t/grainfields-8-voice-granular-synthesizer-for-128-grids-m4l-update/5164
[app grd lines]: https://llllllll.co/t/grd/33768
[app grd src]: https://github.com/yotamorimoto/norns_grd
[app grd demo 1]: https://www.instagram.com/p/CBQpV_dAfBU/
[app grd demo 2]: https://www.instagram.com/p/CBsjkmPAcit/
[app grendy lines]: https://llllllll.co/t/grendy-a-drone-synth-for-norns/31721
[app grendy src]: https://github.com/cfdrake/grendy
[app greyhole lines]: https://llllllll.co/t/greyhole
[app greyhole src]: https://github.com/justmat/greyhole
[app greyhole demo 1]: https://vimeo.com/379334153
[app grid-test lines]: https://llllllll.co/t/grid-test/29346
[app grid-test src]: https://github.com/okyeron/grid-test
[app grid-test demo 1]: https://www.instagram.com/p/B8aiA-NBYqJ/
[app gridstep lines]: https://llllllll.co/t/gridstep/38559
[app gridstep src]: https://github.com/Quixotic7/gridstep
[app gridstep doc]: https://github.com/Quixotic7/gridstep/blob/master/doc/README.md
[app gridstep demo 1]: https://www.youtube.com/watch?v=GpFIpESiTMs
[app hachi lines]: https://llllllll.co/t/hachi-euclidean-drum-machine/35947
[app hachi src]: https://github.com/pangrus/hachi
[app haven lines]: https://llllllll.co/t/haven/21285
[app haven src]: https://github.com/tai-studio/haven
[app haven demo 1]: https://www.youtube.com/watch?v=1mEBZmao-uc
[app here-there lines]: https://llllllll.co/t/here-there/36170
[app here-there src]: https://github.com/speakerdamage/here-there
[app hid-demo lines]: https://llllllll.co/t/hid-demo/21315
[app hid-demo src]: https://github.com/okyeron/hid-demo/
[app islands lines]: https://www.youtube.com/watch?v=PApL2LFjBPQ
[app islands src]: https://github.com/junklight/islands
[app islands doc]: https://www.youtube.com/watch?v=PApL2LFjBPQ
[app islands demo 1]: https://www.youtube.com/watch?v=Rvt7K0rEVLc
[app isoseq lines]: https://llllllll.co/t/isoseq/21026
[app isoseq src]: https://github.com/carvingCode/isoseq
[app isoseq demo 1]: https://vimeo.com/328649268
[app jiffy lines]: https://llllllll.co/t/jiffy/25475
[app jiffy src]: https://github.com/lukes-anger/jiffy
[app kria_midi lines]: https://llllllll.co/t/kria-midi/21255
[app kria_midi src]: https://github.com/junklight/misc/tree/master/dust/code/Kria
[app kria_midi demo 1]: https://www.youtube.com/watch?v=FtyTv8ngdI4
[app kria_midi demo 2]: https://www.instagram.com/p/BwG_lQVjxbw/
[app langl lines]: https://llllllll.co/t/langl/26931
[app langl src]: https://github.com/burgessv/langl
[app langl demo 1]: https://vimeo.com/373190679
[app less_concepts lines]: https://llllllll.co/t/less-concepts/21109
[app less_concepts src]: https://github.com/dndrks/less_concepts
[app less_concepts demo 1]: https://www.youtube.com/watch?v=AHuZm-aHN6k
[app librarian lines]: https://llllllll.co/t/librarian/21213
[app librarian src]: https://github.com/itsyourbedtime/Librarian/
[app lissadron lines]: https://llllllll.co/t/lissadron/32509
[app lissadron src]: https://github.com/tai-studio/lissadron
[app lissadron demo seq]: https://www.instagram.com/p/CCphM5eB5Ue/
[app loom lines]: https://llllllll.co/t/loom/21091
[app loom src]: https://github.com/markwheeler/loom/
[app loom demo 1]: https://www.instagram.com/p/Bwh6ASJFMTF/
[app loom demo 2]: https://www.instagram.com/p/CA9mb4Rl9kJ/
[app mangl lines]: https://llllllll.co/t/mangl/21066
[app mangl src]: https://github.com/justmat/mangl
[app mangl demo 1]: https://vimeo.com/328160082
[app manifold lines]: https://llllllll.co/t/manifold/22098
[app manifold src]: https://github.com/carltesta/manifold
[app manifold demo 1]: https://www.instagram.com/p/Bw9I_tjoHUg/?utm_source=ig_web_button_share_sheet
[app meadowphysics lines]: https://llllllll.co/t/meadowphysics-norns/21185
[app meadowphysics src]: https://github.com/alpha-cactus/meadowphysics
[app meadowphysics doc]: https://monome.org/docs/meadowphysics/
[app meadowphysics demo 1]: https://vimeo.com/146731772
[app mi-eng lines]: https://llllllll.co/t/mi-engines/32338
[app mi-eng/macro-b demo 1]: https://www.instagram.com/p/CAKK_2ChxP4/
[app mi-eng/macro-p demo 1]: https://www.instagram.com/p/B_oUfbfhlHY/
[app mi-eng/modal-e demo 1]: https://www.instagram.com/p/B_osZdTh1OH/
[app mi-eng/resonate-r demo 1]: https://www.instagram.com/p/B_mEYRohEXA/
[app mi-eng/texture-c demo 1]: https://www.instagram.com/p/B_oUfbfhlHY/
[app midimatrix lines]: https://llllllll.co/t/norns-as-usb-midi-host-router/37883/9
[app midimatrix src]: https://gist.github.com/dndrks/817cd450ab432c79c97507c1a1a0a1f6
[app midi-monitor lines]: https://llllllll.co/t/midi-monitor/35036
[app midi-monitor src]: https://github.com/okyeron/midi-monitor
[app midi-monitor demo 1]: https://www.youtube.com/watch?v=-zXIbLDpzAo
[app mlr lines]: https://llllllll.co/t/mlr-norns
[app mlr src]: https://github.com/tehn/mlr
[app mlr demo 1]: https://vimeo.com/266741634
[app mlr demo 2]: https://www.instagram.com/p/CFpjWyrIvuh/
[app molly_the_poly lines]: https://llllllll.co/t/molly-the-poly
[app molly_the_poly src]: https://github.com/markwheeler/molly_the_poly
[app molly_the_poly demo 1]: https://www.instagram.com/p/BoXJavpAE3R/
[app moln lines]: https://llllllll.co/t/moln/21111
[app moln src]: https://github.com/antonhornquist/moln
[app monitor lines]: https://llllllll.co/t/monitor/23273
[app monitor src]: https://github.com/neauoire/monitor
[app monitor demo 1]: https://www.youtube.com/watch?v=g_joxEeB3ss
[app monitor demo 2]: https://www.youtube.com/watch?v=L8jhEIHqPNU
[app n16o lines]: https://llllllll.co/t/n16o/28198
[app n16o src]: https://github.com/jlmitch5/n16o
[app nisp lines]: https://llllllll.co/t/nisp
[app nisp src]: https://github.com/itsyourbedtime/NISP
[app nisp demo 1]: https://www.instagram.com/p/B54rUM6hnWJ/
[app nisp demo 2]: https://www.instagram.com/p/B545yPRh5QA/
[app nono lines]: https://llllllll.co/t/nono-a-4-channel-nanoloop-inspired-midi-sequencer-for-norns/28189
[app nono src]: https://github.com/pselodux/nono
[app nono demo 1]: https://www.instagram.com/p/B65YwmLhynJ/
[app norman lines]: https://llllllll.co/t/norman/22606
[app norman src]: https://github.com/crimclark/norman
[app norns.online lines]: https://llllllll.co/t/norns-online/38547
[app norns.online src]: https://github.com/crimclark/norman
[app norns.online demo 1]: https://vimeo.com/481548384
[app onehanded lines]: https://llllllll.co/t/onehanded/25869
[app onehanded src]: https://github.com/mimetaur/onehanded
[app oooooo lines]: https://llllllll.co/t/oooooo/35828
[app oooooo src]: https://github.com/schollz/oooooo
[app oooooo demo 1]: https://www.instagram.com/p/CEeMRPDhCt_/
[app oooooo demo 2]: https://www.instagram.com/p/CEb2CDQBXaz/
[app orbital lines]: https://llllllll.co/t/orbital-norns/21379
[app orbital src]: https://github.com/P580C/orbital
[app orca lines]: https://llllllll.co/t/orca/22492
[app orca src]: https://github.com/itsyourbedtime/orca/
[app orca demo 1]: https://www.instagram.com/p/BxRUGzlFqEX/
[app orca demo 2]: https://www.instagram.com/p/BxJcIL8lhqf/
[app otis lines]: https://llllllll.co/t/otis/22149
[app otis src]: https://github.com/justmat/otis
[app otis demo 1]: https://vimeo.com/333979510
[app passersby lines]: https://llllllll.co/t/passersby/21089
[app passersby src]: https://github.com/markwheeler/passersby
[app passersby demo 1]: https://www.instagram.com/p/Bl1VFffnz7w/
[app patchwork lines]: https://llllllll.co/t/patchwork/28800
[app patchwork src]: https://github.com/oliviercreurer/patchwork
[app patchwork demo 1]: https://www.instagram.com/p/B74VEXZBv20/
[app pedalboard lines]: https://llllllll.co/t/31119
[app pedalboard src]: https://github.com/21echoes/pedalboard
[app phyllis lines]: https://llllllll.co/t/phyllis/27988
[app phyllis src]: https://github.com/justmat/phyllis
[app phyllis demo 1]: https://vimeo.com/381676550
[app piwip lines]: https://llllllll.co/t/piwip
[app piwip src]: https://github.com/schollz/piwip
[app piwip demo 1]: https://www.instagram.com/p/CFmmnnyB1DV/
[app piwip demo 2]: https://www.instagram.com/p/CFla2iJh9zC/
[app piwip demo 3]: https://www.instagram.com/p/CFr8Yu1BCT0/
[app piwip demo 4]: https://www.instagram.com/p/CGJtLCohHRU/
[app pools lines]: https://llllllll.co/t/pools
[app pools src]: https://github.com/justmat/pools
[app pools demo 1]: https://vimeo.com/383786715
[app practice lines]: https://llllllll.co/t/practice/29429
[app practice src]: https://github.com/unit-cell/practice
[app punchcard lines]: https://llllllll.co/t/punchcard
[app punchcard src]: https://github.com/neauoire/punchcard
[app punchcard demo 1]: https://www.youtube.com/watch?v=jZUtkNuEDqY
[app punchcard demo 2]: https://www.youtube.com/watch?v=QO7T6MYkqZo
[app qfwfq lines]: https://llllllll.co/t/qfwfq/38499
[app qfwfq src]: https://github.com/cachilders/qfwfq
[app quence lines]: https://llllllll.co/t/quence/29436
[app quence src]: https://github.com/millxing/QUENCE
[app quence demo 1]: https://www.youtube.com/watch?v=w7hcWn9swu4
[app quence demo 2]: https://www.youtube.com/watch?v=ogu7FdoMybw
[app rebound lines]: https://llllllll.co/t/rebound/23243
[app rebound src]: https://github.com/nf/rebound
[app rebound demo 1]: https://www.instagram.com/p/BmSiQgrAhRg/
[app rpmate lines]: https://llllllll.co/t/rpmate/38542
[app rpmate src]: https://github.com/p3r7/rpmate
[app reels demo 1]: https://www.youtube.com/watch?v=SuF1uTTlyn4
[app reels lines]: https://llllllll.co/t/reels
[app reels src]: https://github.com/itsyourbedtime/reels
[app reels demo 1]: https://www.youtube.com/watch?v=SuF1uTTlyn4
[app rudiments lines]: https://llllllll.co/t/rudiments-lofi-percussion-synth-and-sequencer-for-norns/31828
[app rudiments src]: https://github.com/cfdrake/rudiments
[app sam lines]: https://llllllll.co/t/sam/23943
[app sam src]: https://github.com/justmat/sam
[app samsara lines]: https://llllllll.co/t/samsara-a-minimalist-looper-v1-0-0/34095
[app samsara src]: https://github.com/21echoes/samsara
[app seaflex lines]: https://llllllll.co/t/seaflex/23209
[app seaflex src]: https://github.com/tlubke/shapes
[app shapes lines]: https://llllllll.co/t/shapes/36759
[app shapes src]: https://github.com/tlubke/shapes
[app shell_runner lines]: https://llllllll.co/t/shell-runner/30887
[app shell_runner src]: https://github.com/scazan/shell_runner
[app showers lines]: https://llllllll.co/t/showers/31622
[app showers src]: https://github.com/justmat/showers
[app spacetime study]: https://monome.org/docs/norns/study-3/
[app spacetime demo 1]: https://vimeo.com/276054881
[app stack lines]: https://llllllll.co/t/stack-stereo-bandpass-filterbank-for-norns/35218
[app stack src]: https://github.com/cfdrake/stack
[app step lines]: https://llllllll.co/t/step/21093
[app step src]: https://github.com/antonhornquist/step
[app stjoernuithrott lines]: https://llllllll.co/t/stjornuithrott-stargazer-inspired-drone/33889
[app stjoernuithrott src]: https://github.com/frederickk/stjoernuithrott
[app strides lines]: https://llllllll.co/t/strides/21101
[app strides src]: https://github.com/justmat/strides
[app strides doc]: https://github.com/justmat/strides/blob/master/README.md
[app strides demo 1]: https://vimeo.com/328470668
[app strum lines]: https://llllllll.co/t/strum/21025
[app strum src]: https://github.com/carvingCode/strum
[app strum demo 1]: https://vimeo.com/328638255
[app sway lines]: https://llllllll.co/t/sway/21117
[app sway src]: https://github.com/antonhornquist/step
[app sway demo 1]: https://www.youtube.com/watch?v=w9RZHmo4JAs
[app takt lines]: https://llllllll.co/t/takt/21032
[app takt src]: https://github.com/itsyourbedtime/takt
[app takt doc]: https://github.com/monome/dust/blob/master/docs/bedtime/index.md
[app takt demo 1]: https://www.instagram.com/p/Brm-za6FWMZ/
[app tambla lines]: https://llllllll.co/t/tambla/37965
[app tambla src]: https://github.com/ngwese/tambla
[app tambla doc]: https://github.com/ngwese/tambla-docs/blob/main/README.md
[app there lines]: https://llllllll.co/t/there/27892
[app there src]: https://github.com/infovore/norns-there
[app timber lines]: https://llllllll.co/t/timber/21407
[app timber src]: https://github.com/markwheeler/timber
[app timber/keys demo 1]: https://www.instagram.com/p/Bs4PuShBTbZ/
[app timber/player demo 1]: https://llllllll.co/uploads/default/original/3X/5/3/53f651f809d88726e5d9ee9b5493908bfefc3313.jpegZ/
[app torii lines]: https://llllllll.co/t/torii/30476
[app torii src]: https://github.com/okyeron/torii
[app torii demo 1]: https://www.instagram.com/p/B9V3djWhUwn/
[app torii demo 2]: https://www.instagram.com/p/B-Buf_LBxst/
[app tunnels lines]: https://llllllll.co/t/tunnels/21973
[app tunnels src]: https://github.com/speakerdamage/tunnels
[app tunnels demo 1]: https://www.instagram.com/p/BwwdlZcls4V/
[app tuner lines]: https://llllllll.co/t/tuner/21088
[app tuner src]: https://github.com/markwheeler/tuner
[app timber lines]: https://llllllll.co/t/21407
[app timeparty lines]: https://llllllll.co/t/timeparty/22837
[app timeparty src]: https://github.com/crimclark/timeparty
[app vials lines]: https://llllllll.co/t/vials/23109
[app vials src]: https://github.com/nattog/vials
[app vials doc]: https://github.com/nattog/vials/blob/main/README.md
[app uhf lines]: https://llllllll.co/t/uhf-norns/21154
[app uhf src]: https://github.com/speakerdamage/uhf
[app waveviz src]: https://github.com/csboling/waveviz
[app yggdrasil lines]: https://llllllll.co/t/yggdrasil-v1-0-6/38040
[app yggdrasil src]: https://github.com/northern-information/yggdrasil
[app yggdrasil doc]: https://northern-information.github.io/yggdrasil-docs/
[app yggdrasil demo 1]: https://www.youtube.com/watch?v=8ac2qw9gmaw
[app yggdrasil demo 2]: https://vimeo.com/476850905
[app zeelen src]: https://github.com/sarweiler/zellen
[app zeelen demo 1]: https://www.youtube.com/watch?v=BawpNsvTHe8
[app zeelen lines]: https://llllllll.co/t/zellen/21107
[app zeelen src]: https://github.com/sarweiler/zellen
[app zeelen demo 1]: https://www.youtube.com/watch?v=BawpNsvTHe8
[app zeelen demo crow]: https://www.youtube.com/watch?v=0YFQPW84zM8
