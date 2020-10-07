# awesome-monome-norns


<div align=center><img src="https://monome.org/images/norns-front-small.jpg" width="500"></div>

A list of links and resources for the [norns](https://monome.org/docs/norns/) hardware music platform by [monome](https://monome.org/).

It allows running apps built with [SuperCollider](https://supercollider.github.io/) and/or **softcut**, a powerfull live sampler / player.

In addition, [Pure Data](https://puredata.info/) patches can also be run (see [Mother, Pure Data & Orac](#mother-pure-data--orac)).

The community resides mostly on [llllllll.co](https://llllllll.co/) (pronounced _lines_).

<!-- https://llllllll.co/t/norns-dust/14015 -->
<!-- https://llllllll.co/t/ash-a-small-collection/21349 -->

## Hardware

There are 2 variations of the norns hardware:

 - [norns](https://market.monome.org/collections/primary/products/norns), relying on a Raspbery Pi CM3 or CM3+
 - [norns shield](https://market.monome.org/collections/primary/products/norns-shield-kit), a HAT for Raspbery Pi 3B or 3B+.


#### norns shield

The **norns shield** option is DIY and more economic but lacks a battery, has no monitor output, a less clean audio path and is more generally less rugged.

For more information about building your own norns using the **norns shield**:

 - [t/diy-norns-shield](https://llllllll.co/t/diy-norns-shield/27638) for general build help
 - [t/norns-shield-case-designs](https://llllllll.co/t/norns-shield-case-designs/30347) for building a case

[u/JHC](https://llllllll.co/u/JHC) provided a [nice 3D printing STL design](https://llllllll.co/t/norns-shield-case-designs/30347/224).

[u/okyeron](https://llllllll.co/u/okyeron) created some [nice laser-cut designs](https://llllllll.co/t/norns-shield-case-designs/30347/183) that he also sells for a very reasonable cost [on his online store](https://denki-oto.weebly.com/store/p39/norns-shield-case.html#/).

If you don't have access to a fablab, you can use a laser-cut service such as [ponoko](https://www.ponoko.com/) (US) or [razorlab](https://razorlab.online/) (UK).

For encoder caps, you can look at makers such as Sifam / Selco, the various offerings at aliexpress ([example](https://www.aliexpress.com/item/32781327404.html?spm=2114.13010708.0.0.3a994c4dQ4Aov1)) or even go the [3D printing route](https://llllllll.co/t/diy-norns-shield/27638/876).


#### Hardware companions

Some apps are made to work only with some of other **monome** hardware (such as **grid**, **arc** and **crow**).

Others rely on other input devices such as MIDI controllers (pad, keyboards...) or a computer keyboard.

For discussing those options, see [t/friends-of-norns](https://llllllll.co/t/friends-of-norns-gear-accessories-etc/17150).


## Development: General

The **norns** platform allows developping small programs using the [lua](https://www.lua.org/) programming language.

They are generally refered to as _scripts_, and _apps_ once packaged and distributed.

2 internal sound processing units are at our disposal:

 - `engine`: an instance of [SuperCollider](https://supercollider.github.io/) (sometimes also refered to as `external`)
 - `softcut`: a live multi-channel sampler / player that can be used to build crazy loopers and delays

<div align=center><img src="https://monome.org/docs/norns/image/norns-audio-route.png" width="750"></div>

Even though _SuperCollider_ is generally used to define a virtual synthesizer, it can also take audio from the inputs (missing on the above diagram).

Most scripts you'll find in the wild use either _softcut_ or _engine_, but some might use the 2 of them.


#### Documentation

 - [basic lua scripting reference](https://monome.org/docs/norns/script-reference/)
 - [complete lua APIs doc](https://monome.org/norns/)


#### Tutorials & example apps

 - [norns studies](https://monome.org/docs/norns/studies-landing/)
 - [norns: tutorial](https://llllllll.co/t/norns-tutorial/23241) by [Devine Lu Linvega](https://xxiivv.com/)
 - [foundry](https://llllllll.co/t/foundry) app ([code](https://github.com/csboling/foundry)) for text & fonts
 - [video tutorial on adding midi out to an existing app](https://llllllll.co/t/norns-walkthrough-hacking-a-script-to-add-midi-output/34969)


#### Community

When wanting to contribute or seeking help, use one of those threads:

 - [t/norns-scripting](https://llllllll.co/t/norns-scripting/14120): getting help with app development (lua)
 - [t/norns-softcut](https://llllllll.co/t/norns-2-0-softcut/20550): getting help with app development (softcut)
 - [t/norns-supercollider](https://llllllll.co/t/norns-supercollider/22822): getting help with app development (SuperCollider side)
 - [t/norns-development](https://llllllll.co/t/norns-development/14073): proposing evloutions to core norns code
 - [t/exquisite-script-a-collective-scripting-game-for-norns](https://llllllll.co/t/exquisite-script-a-collective-scripting-game-for-norns/34989): a cadavre exquis, collective development of an app


## Development: Libraries & Engines

When developping apps/scripts, you rely on lua libraries (classes & modules). One of them, _engine_, allows interracting with a running SuperCollider instance.

When using SuperCollider, one can rely on an already installed SuperCollider library on spin their own. Those SuperCollider libraries (in essence a _SynthDef_) are called _engines_ in the context of **norns** development.

Most advanced apps come with their own custom libraries / engine.

Here are listed the ones most often spotted in the wild.


#### Softcut & Softcut-based libs

| library                        | code                                                       | description                         | based upon | provided by          | used by                            |
| --                             | ---                                                        | ---                                 | ---        | ---                  | ---                                |
| [softcut][lib softcut lines]   | [lua][lib softcut gh lua], [undelying C][lib softcut gh C] | sample record & playback            |            | installed by default | sam, reels, piwip                  |
| ack                            | [lua][lib ack gh lua]                                      | advanced sample playback            | softcut    | installed by default | step, ash/playfair, foulplay, takt |
| [supercut][lib supercut lines] | [lua][lib supercut gh lua]                                 | higher-level wrapper around softcut | softcut    |                      | wrms                               |


#### SuperColider engines

| library         | code                                                                        | description                                                                        | provided by                                | used by                                  |
| --              | ---                                                                         | ---                                                                                | ---                                        | ---                                      |
| timber          | [lua wrapper][lib timber gh lua], [sclang][lib timber gh sc]                | advanced sample playback                                                           | [timber][app timber lines]                 | timber, orca                             |
| PolyPerc        | [sclang][lib polyperc gh sc]                                                | simple polyphonic filtered decaying square wave                                    | [awake][app awake lines]                   | awake, meadowphysics, barycenter, zeelen |
| PolySub         |                                                                             | multi-type oscillator with polyphonic modulation busses for polytimbral expression |                                            |                                          |
| molly_the_poly  | [lua wrapper][lib molly_the_poly gh lua] [sclang][lib molly_the_poly gh sc] |                                                                                    | [molly_the_poly][app molly_the_poly lines] | molly_the_poly, arp_index, loom, quence  |
| passersby       | [lua wrapper][lib passersby gh lua] [sclang][lib passersby gh sc]           |                                                                                    | [passersby][app passersby lines]           | passersby, less_concepts, dunes          |
| PrimitiveString | [sclang][lib PrimitiveString gh sc]                                         |                                                                                    | [euclidigons][app euclidigons lines]       | euclidigons                              |
| R               | [sclang][lib R gh sc]                                                       | collection of engines that link together in a modular synth-style workflow         |                                            | moln                                     |


## Apps

#### List

Many apps are available through [maiden](https://monome.org/docs/norns/maiden/) but many more are missing.

The [documentation has a list of popular apps](https://monome.org/docs/norns/app/).

This section is aimed at being more complete and providing more meta-data to select which app corresponds to your needs.

Synths & drones:

| app                                        | on maiden | code                         | description                                                                                                 | demo                                               | doc                   |
| ---                                        | :---:     | ---                          | ---                                                                                                         | ---                                                | ---                   |
| [benjolis][app benjolis lines]             | ✔️         | [gh][app benjolis src]       | port of Alejandro Olarte’s Benjolis SuperCollider patch, inspired from Rob Hordijk’s Benjolin               | [1][app benjolis demo 1], [2][app benjolis demo 2] |                       |
| [dronecaster][app dronecaster lines]       | ✔️         | [gh][app dronecaster src]    | Various drones                                                                                              | [1][app dronecaster demo 1]                        |                       |
| [fm7][app fm7 lines]                       | ✔️         | [gh][app fm7 src]            | DX7-inspired polyphonic FM synth                                                                            | [1][app fm7 demo 1]                                | [online][app fm7 doc] |
| [grendy][app grendy lines]                 | ✔️         | [gh][app grendy src]         | a simple drone synth, grendel drone commander inspired                                                      |                                                    |                       |
| [lissadron][app lissadron lines]           | ✔️         | [gh][app lissadron src]      | A software synth making extensive use of seeded randomness, internal sequencer for voice change             | [internal sequencer][app lissadron demo seq]       |                       |
| [molly_the_poly][app molly_the_poly lines] | default️   | [gh][app molly_the_poly src] | Juno-6 voice structure with chorus, the extra modulation of a Jupiter-8, and CS-80 inspired ring modulation | [1][app molly_the_poly demo 1]                     |                       |
| [moln][app moln lines]                     | ✔️         | [gh][app moln src]           | Polyphonic subtractive synthesizer                                                                          | [1][app moln demo 1]                               |                       |
| [passersby][app passersby lines]           | ✔️         | [gh][app passersby src]      | Wave folding, FM, LPG, spring-ish reverb, LFO and two dice to roll                                          | [1][app passersby demo 1]                          |                       |
| [rudiments][app rudiments lines]           | ✔️         | [gh][app rudiments src]      | 8 voice lofi percussion synthesizer and sequencer (playfair-style)                                          |                                                    |                       |
| [showers][app showers lines]               | ✔️         | [gh][app showers src]        | a thunderstorm (rain & thunder)                                                                             |                                                    |                       |

Granular (sample-based) synths:

| app                        | on maiden | code                 | description                                                                              | demo                   | doc |
| ---                        | :---:     | ---                  | ---                                                                                      | ---                    | --- |
| [glut][app glut lines]     | ✔️         | [gh][app glut src]   | granular synth inspired by mlr/rove, [grainfield][app grainfield lines] & loomer cumulus | [1][app glut demo 1]   |     |
| [gemini][app gemini lines] | ✔️         | [gh][app gemini src] | one file, two granulators                                                                | [1][app gemini demo 1] |     |
| [mangl][app mangl lines]   | ✔️         | [gh][app mangl src]  | a 7 track granular sample player.                                                        | [1][app mangl demo 1]  |     |


Sample players:

| app                               | on maiden | code                    | description                                                  | demo                          | doc |
| ---                               | :---:     | ---                     | ---                                                          | ---                           | --- |
| [drum_room][app drum_room lines]  | ✔         | [gh][app drum_room src] | MIDI-controlled drum kits                                    | [1][app drum_room demo 1]     |     |
| [timber/keys][app timber lines]   | ✔         | [gh][app timber src]    | split & map a sample accross midi keys / grid                | [1][app timber/keys demo 1]   |     |
| [timber/player][app timber lines] | ✔         | [gh][app timber src]    | load whole directory of samples mapped onto midi keys / grid | [1][app timber/player demo 1] |     |


Basic samplers:

| app                  | on maiden | code              | description                                     | demo | doc |
| ---                  | :---:     | ---               | ---                                             | ---  | --- |
| [sam][app sam lines] |           | [gh][app sam src] | record, adjust start & end points, save to tape |      |     |


Sequencers & trackers:

| app                                                    | on maiden | code                        | description                                                         | demo                                                       | doc                             |
| ---                                                    | :---:     | ---                         | ---                                                                 | ---                                                        | ---                             |
| [animator][app animator lines]                         | ✔️         | [gh][app animator src]      | 2D polyphonic sequencer for grids                                   | [1][app animator demo 1], [2][app animator demo 2]         | [online][app animator doc]      |
| [arcologies][app arcologies lines]                     | ✔️         | [gh][app arcologies src]    | interactive environment for designing 2d sound arcologies           | [gallery][app arcologies demos]                            | [online][app arcologies doc]    |
| [arp_index][app arp_index lines]                       | ✔️         | [gh][app arp_index src]     | generate sequence from company stocks                               | [1][app arp_index demo 1]                                  |                                 |
| [ash/playfair][app ash lines]                          | ✔️         | [gh][app ash/playfair src]  | euclidean drummer, four sequences, each with its own sample         | [1][app ash/playfair demo 1]                               |                                 |
| [awake][app awake lines]                               | default   | [gh][app awake src]         | two looped sequences                                                | [1][app awake demo 1]                                      |                                 |
| [boing][app boingg lines]                              | ✔         | [gh][app boingg src]        | a bouncing ball sequencer                                           | [1][app boingg demo 1]                                     |                                 |
| [cheat_codes][app cheat_codes lines]                   | ✔️         | [gh][app cheat_codes src]   | sample playground                                                   | [1][app cheat_codes demo 1]                                | [pdf][app cheat_codes doc]      |
| [circles][app circles lines]                           | ✔️         | [gh][app circles src]       | move cursor, place circles, make music                              | [1][app circles demo 1]                                    |                                 |
| [dunes][app dunes lines]                               | ✔         | [gh][app dunes src]         | function sequencer, inspired by [spacetime][app spacetime study]    | [audio][app dunes demo audio], [midi][app dunes demo midi] |                                 |
| [drift][app drift lines]                               |           | [gh][app drift src]         | sequencer based on particle systems                                 | [midi][app drift demo midi]                                |                                 |
| [euclidigons][app euclidigons lines]                   | ✔️         | [gh][app euclidigons src]   | plucky geometric rhythm generator                                   | [1][app euclidigons demo 1], [2][app euclidigons demo 2]   |                                 |
| [foulplay][app foulplay lines]                         | ✔️         | [gh][app foulplay src]      | euclidean drummer, inspired by [ash/playfair][app ash lines]        | [1][app foulplay demo 1]                                   | [online][app foulplay doc]      |
| fretwork                                               | ️          | [gh][app fretwork src]      | ornamental sequencer                                                | [1][app fretwork demo 1]                                   |                                 |
| [grd][app grd lines]                                   | ️          | [gh][app grd src]           | 8x8 autonomy                                                        | [1][app grd demo 1], [2][app grd demo 2]                   |                                 |
| [less_concepts][app less_concepts lines]               | ✔️         | [gh][app less_concepts src] | cellular automata sequencer                                         | [1][app less_concepts demo 1]                              | [online][app meadowphysics doc] |
| [loom][app loom lines]                                 | ✔️         | [gh][app loom src]          | pattern weaving sequencer for grids                                 | [1][app loom demo 1], [2][app loom demo 2]                 |                                 |
| [meadowphysics][app meadowphysics lines]               | ✔️         | [gh][app meadowphysics src] | grid-enabled rhizomatic cascading counter                           | [1][app meadowphysics demo 1]                              | [online][app meadowphysics doc] |
| [nisp][app nisp lines]                                 | ✔️         | [gh][app nisp src]          | LISP (Scheme dialect) livecoding tracker                            | [1][app nisp demo 1], [2][app nisp demo 2]                 |                                 |
| [orca][app orca lines]                                 | ✔️         | [gh][app orca src]          | esotheric programming language                                      | [1][app orca demo 1], [2][app orca demo 2]                 |                                 |
| [punchcard][app punchcard lines]                       | ✔️         | [gh][app punchcard src]     | experimental sequencer that works like a classic punchcard computer | [1][app punchcard demo 1], [2][app punchcard demo 2]       |                                 |
| [quence][app quence lines]                             | ✔️         | [gh][app quence src]        | a probabilistic 4-track sequencer                                   | [1][app quence demo 1], [2][app quence demo 2]             |                                 |
| [rebound][app rebound lines]                           | ✔️         |                             | a kinetic sequencer                                                 | [1][app rebound demo 1]                                    |                                 |
| [spacetime][app spacetime study] aka `we/study/study3` | ✔️         |                             | a weird function sequencer                                          | [1][app spacetime demo 1]                                  |                                 |
| [step][app step lines]                                 | ✔️         | [gh][app step src]          | a simple step sequencer                                             |                                                            |                                 |
| [takt][app takt lines]                                 | ✔️         | [gh][app takt src]          | Digitakt-inspired parameter locking step sequencer                  | [1][app takt demo 1]                                       | [online][app takt doc]          |
| [zeelen][app zeelen lines]                             | ✔️         | [gh][app zeelen src]        | Game of Life based sequencer                                        | [1][app zeelen demo 1], [crow][app zeelen demo crow]       | [online][app takt doc]          |


Control Modulation sources:

| app                                | on maiden | code                     | description                                   | demo                                             | doc |
| ---                                | :---:     | ---                      | ---                                           | ---                                              | --- |
| [barycenter][app barycenter lines] |           | [gh][app barycenter src] | Fluctuating relationships in orbit            |                                                  |     |
| [changes][app changes lines]       |           | [gh][app changes src]    | eight connected sine wave LFOs as MIDI output | [1][app changes demo 1], [2][app changes demo 2] |     |
| [shapes][app shapes lines]         |           | [gh][app shapes src]     | Visually based modulation source for crow     |                                                  |     |



Audio effects:

| app                                | on maiden | code                     | description                                   | demo                     | doc |
| ---                                | :---:     | ---                      | ---                                           | ---                      | --- |
| [greyhole][app greyhole lines]     | ✔️         | [gh][app greyhole src]   | echo / delay                                  | [1][app greyhole demo 1] |     |
| [manifold][app manifold lines]     | ✔️         | [gh][app manifold src]   | multi-effects processing for live performance | [1][app manifold demo 1] |     |
| [pedalboard][app pedalboard lines] | ✔️         | [gh][app pedalboard src] | chainable effects for live performance        |                          |     |
| [phyllis][app phyllis lines]       | ✔️         | [gh][app phyllis src]    | digitally modeled analog                      | [1][app phyllis demo 1]  |     |
| [pools][app pools lines]           | ✔️         | [gh][app pools src]      | a shimmery reverb                             | [1][app pools demo 1]    |     |
| [stack][app stack lines]           | ✔️         | [gh][app stack src]      | stack of bandpass filter, sequencable         |                          |     |
| [sway][app sway lines]             | ✔️         | [gh][app sway src]       | analysis-driven live audio processing         | [1][app sway demo 1]     |     |


Loopers, live samplers & crazy delays:

| app                          | on maiden | code                  | description                                         | demo                                           | doc                     |
| ---                          | :---:     | ---                   | ---                                                 | ---                                            | ---                     |
| [barcode][app barcode lines] | ✔️         | [gh][app barcode src] | a randomized looper                                 | [1][app barcode demo 1]                        |                         |
| [blndr][app blndr lines]     | ✔️         | [gh][app blndr src]   | a quantized delay with time bending effects         | [1][app blndr demo 1]                          |                         |
| [cranes][app cranes lines]   | ✔️         | [gh][app cranes src]  | stereo varispeed looper / delay / timeline-smoosher | [1][app cranes demo 1]                         | [video][app cranes doc] |
| [mlr][app mlr lines]         | ✔️         | [gh][app mlr src]     | live sample-cutting platform                        | [1][app mlr demo 1], [2][app mlr demo 2]       |                         |
| [oooooo][app oooooo lines]   | ✔️         | [gh][app oooooo src]  | digital tape loops x6                               | [1][app oooooo demo 1], [2][app oooooo demo 2] |                         |
| [otis][app otis lines]       | ✔️         | [gh][app otis src]    | dual tape delay/looper/sampler                      | [1][app otis demo 1]                           |                         |
| [piwip][app piwip lines]     | ✔️         | [gh][app piwip src]   | a sampler that works in realtime                    | [1][app piwip demo 1]                          |                         |
| [reels][app reels lines]     | ✔️         | [gh][app reels src]   | a 4-track asynchronous looper                       | [1][app reels demo 1]                          |                         |
| [samsara][app samsara lines] | ✔️         | [gh][app samsara src] | minimalist looper that eventually reaches nirvana   |                                                |                         |
| [tunnels][app tunnels lines] | ✔️         | [gh][app tunnels src] | a collection of uncertain delays                    | [1][app tunnels demo 1]                        |                         |


#### By I/O

| symbol | meaning             |
| :---:  | ---                 |
| ✔️      | yes                 |
| 🔴     | mandatory           |
| 🔶     | strongly encouraged |
| ⚪     | optional            |


| app                                                | audio in | midi sync | midi in | keyboard | grid   | arc   | audio out | midi out | crow  |
| ---                                                | :---:    | :---:     | :---:   | :---:    | :---:  | :---: | :---:     | :---:    | :---: |
| [arcologies][app arcologies lines]                 |          |           |         |          | 🔴     |       |           |          |       |
| [arp_index][app arp_index lines]                   |          |           | ⚪      |          |        |       | ✔         |          |       |
| [awake][app awake lines]                           |          | ⚪        |         |          | ⚪     |       | ✔️         |          |       |
| [barcode][app barcode lines]                       | ✔        |           |         |          |        |       | ✔️         | ️         |       |
| [barycenter][app barycenter lines]                 |          |           |         |          |        |       | ✔️         | ✔️        |       |
| [benjolis][app benjolis lines]                     |          |           |         |          |        |       | ✔️         | ️         |       |
| [boing][app boingg lines]                          |          |           |         |          | ⚪     |       | ✔️         | ✔️        | ✔     |
| [changes][app changes lines]                       |          |           |         |          |        |       |           | ✔        |       |
| [cheat_codes][app cheat_codes lines]               |          |           |         |          | 🔶 \** | 🔶    |           |          |       |
| [circles][app circles lines]                       |          |           |         |          |        |       | ✔         | ✔        |       |
| [cranes][app cranes lines]                         | ✔️        |           |         |          | ⚪     |       | ✔️         |          |       |
| [drift][app drift lines]                           |          |           |         |          |        |       | ✔️         | ✔        |       |
| [dronecaster][app dronecaster lines]               |          |           |         |          |        |       | ✔️         |          |       |
| [drum_room][app drum_room lines]                   |          |           | 🔴      |          |        |       | ✔️         |          |       |
| [dunes][app dunes lines]                           |          |           |         |          |        |       | ✔️         |          |       |
| [euclidigons][app euclidigons lines]               |          |           |         |          |        |       | ✔️         | ✔️        |       |
| [foulplay][app foulplay lines]                     |          |           |         |          | 🔶     |       | ✔️         | ✔️        |       |
| fretwork                                           |          |           |         |          |        |       | ✔️         | ✔️        | ✔     |
| [fm7][app fm7 lines]                               |          |           | 🔶      |          | 🔶     |       | ✔️         |          |       |
| [gemini][app gemini lines]                         | ️         |           |         |          |        | ⚪    | ✔️         |          |       |
| [glut][app glut lines]                             | ️         |           |         |          | 🔶     |       | ✔️         |          |       |
| [grd][app grd lines]                               | ️         |           |         |          |        |       | ✔️         |          |       |
| [greyhole][app greyhole lines]                     | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [less_concepts][app less_concepts lines]           |          |           |         |          | 🔶     |       | ✔️         | ✔        | ✔     |
| [lissadron][app lissadron lines]                   |          |           | 🔶      |          |        |       | ✔️         |          |       |
| [loom][app loom lines]                             |          | ⚪        |         |          | 🔴     |       | ✔️         | ✔        |       |
| [mangl][app mangl lines]                           |          |           |         |          | 🔶     | 🔶    | ✔️         | ️         |       |
| [manifold][app manifold lines]                     | ✔        |           | 🔶      |          |        |       | ✔️         | ️         |       |
| [meadowphysics][app meadowphysics lines]           |          |           |         |          | 🔴     |       | ✔️         | ✔️        |       |
| [mlr][app mlr lines]                               | ✔️        |           |         |          | 🔴     |       | ✔️         |          |       |
| [molly_the_poly][app molly_the_poly lines]         |          |           | 🔴 \*   |          | ⚪ \*  |       | ✔️         |          |       |
| [moln][app moln lines]                             |          |           | 🔴 \*   |          | ⚪ \*  | ⚪    | ✔️         |          |       |
| [nisp][app nisp lines]                             |          |           |         | 🔴       |        |       | ✔️         |          |       |
| [oooooo][app oooooo lines]                         | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [orca][app orca lines]                             | ✔️        |           | ✔       | 🔴       | ⚪     |       | ✔️         | ✔        |       |
| [otis][app otis lines]                             | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [passersby][app passersby lines]                   |          |           | 🔴 \*   |          | ⚪ \*  |       | ✔️         |          |       |
| [pedalboard][app pedalboard lines]                 | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [piwip][app piwip lines]                           |          |           |         |          |        |       |           |          |       |
| [pools][app pools lines]                           | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [punchcard][app punchcard lines]                   |          |           |         |          | 🔴     |       |           | ✔️        |       |
| [quence][app quence lines]                         |          |           |         |          | 🔴     |       | ✔         | ✔️        | ✔     |
| [rebound][app rebound lines]                       | ️         | ⚪        |         |          |        |       | ️          | ✔        |       |
| [reels][app reels lines]                           | ✔️        |           |         |          |        |       | ✔️         |          |       |
| [shapes][app shapes lines]                         |          |           |         |          |        |       |           |          | ✔     |
| [spacetime][app spacetime study] `we/study/study3` |          |           |         |          |        |       | ✔️         |          |       |
| [step][app step lines]                             |          |           |         |          | 🔴     | 🔶    | ✔️         |          |       |
| [takt][app takt lines]                             |          |           |         |          | 🔴     |       | ✔️         |          |       |
| [timber/keys][app timber lines]                    |          | ⚪        | 🔴 \*   |          | ⚪ \*  |       | ✔️         |          |       |
| [timber/player][app timber lines]                  |          | ⚪        | 🔴 \*   |          | ⚪ \*  |       | ✔️         |          |       |
| [zeelen][app zeelen lines]                         |          |           |         |          | 🔴     |       | ✔️         | ✔        | ✔     |

Special cases:

 - \*: grid acts as a midi keyboard and can replace it
 - \**: grid can be replaced by TouchOSC


## Mother, Pure Data & Orac

[Pure Data](https://puredata.info/) patches originally built for the [Organelle](https://www.critterandguitari.com/organelle) can run on any _norns_ device.

This is easilly done thanks to the combination of 2 projects:

 - _Sidekick_ by [u/thetechnobear](https://llllllll.co/u/thetechnobear/summary) that allows booting out of the _norns_ software and into other ones ([lines thread](https://llllllll.co/t/orac-sidekick-pure-data-and-sc-for-norns/26198))
 - _Mother_ by [u/oxbown](https://llllllll.co/u/oxbown/summary) that provides a compatibility layer for running Organelle patches ([lines thread](https://llllllll.co/t/norns-mother-organelle-patches-on-norns/30237))

In addition, installing _Sideckick_ also provides:

 - _Orac_: a patch chaining software for _Pure Data_
 - _NuiLite_: a lightweight _Pure Data_ _external_ (i.e. extension) for making and running patches without depending on the _Organelle/Mother_ or _Orac_ layer.

For more details, see also the [the _Sidekick_ project wiki](https://github.com/TheTechnobear/NuiLite/wiki).



<!-- ====================================================================== -->

<!-- softcut libs -->
[lib softcut lines]: https://llllllll.co/t/norns-2-0-softcut/20550
[lib softcut gh lua]: https://github.com/monome/norns/blob/main/lua/core/softcut.lua
[lib softcut gh C]: https://github.com/monome/softcut-lib
[lib ack gh lua]: https://github.com/antonhornquist/ack
[lib supercut lines]: https://llllllll.co/t/supercut-lib/29526
[lib supercut gh lua]: https://github.com/andr-ew/supercut

<!-- supercolier libs -->
[lib timber gh lua]: https://github.com/markwheeler/timber/blob/master/lib/timber_engine.lua
[lib timber gh sc]: https://github.com/markwheeler/timber/blob/master/lib/Engine_Timber.sc
[lib polyperc gh sc]: https://github.com/tehn/awake/blob/master/lib/Engine_PolyPerc.sc
[lib molly_the_poly gh lua]: https://github.com/markwheeler/molly_the_poly/blob/master/lib/molly_the_poly_engine.lua
[lib molly_the_poly gh sc]: https://github.com/markwheeler/molly_the_poly/blob/master/lib/Engine_MollyThePoly.sc
[lib passersby gh lua]: https://github.com/markwheeler/passersby/blob/master/lib/passersby_engine.lua
[lib passersby gh sc]: https://github.com/markwheeler/passersby/blob/master/lib/Engine_Passersby.sc
[lib PrimitiveString gh sc]: https://github.com/synthetiv/euclidigons/blob/main/lib/Engine_PrimitiveString.sc
[lib R gh sc]: https://github.com/antonhornquist/r


<!-- apps -->
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
[app ash/playfair src]: https://github.com/tehn/ash/blob/master/playfair.lua
[app ash/playfair demo 1]: https://vimeo.com/270668759
[app awake lines]: https://llllllll.co/t/awake
[app awake src]: https://github.com/tehn/awake
[app awake demo 1]: https://vimeo.com/327848801
[app barcode lines]: https://llllllll.co/t/barcode/35297
[app barcode src]: https://github.com/schollz/barcode
[app barcode demo 1]: https://www.instagram.com/p/CDxUwsSh7oP/
[app barycenter lines]: https://llllllll.co/t/barycenter
[app barycenter src]: https://github.com/echophon/barycenter
[app benjolis lines]: https://llllllll.co/t/benjolis/28061
[app benjolis src]: https://github.com/scazan/benjolis
[app benjolis demo 1]: https://www.instagram.com/p/B6tJ036BuwC/
[app benjolis demo 2]: https://www.instagram.com/p/B6vAYhEB4Hi/
[app blndr lines]: https://llllllll.co/t/blndr/35106
[app blndr src]: https://github.com/schollz/blndr
[app blndr demo 1]: https://llllllll.co/t/blndr/35106
[app boingg lines]: https://llllllll.co/t/boingg/26536
[app boingg src]: https://github.com/justmat/boingg
[app boingg demo 1]: https://vimeo.com/368803868
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
[app cranes lines]: https://llllllll.co/t/cranes/21207
[app cranes src]: https://github.com/dndrks/cranes
[app cranes doc]: https://www.youtube.com/watch?v=pVVKC3KnRLg
[app cranes demo 1]: https://www.instagram.com/p/Bv5klu_l9mp/
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
[app fretwork src]: https://github.com/synthetiv/fretwork
[app fretwork demo 1]: https://www.instagram.com/p/B8-JSEGF-7d/
[app gemini lines]: https://llllllll.co/t/gemini/21086
[app gemini src]: https://github.com/mhetrick/gemini/
[app gemini demo 1]: https://www.instagram.com/p/BwOp6t1FVeX/
[app glut lines]: https://llllllll.co/t/glut/21175
[app glut src]: https://github.com/artfwo/glut
[app glut demo 1]: https://www.youtube.com/watch?v=uvikPhSNA4U
[app grd lines]: https://llllllll.co/t/grd/33768
[app grd src]: https://github.com/yotamorimoto/norns_grd
[app grd demo 1]: https://www.instagram.com/p/CBQpV_dAfBU/
[app grd demo 2]: https://www.instagram.com/p/CBsjkmPAcit/
[app grendy lines]: https://llllllll.co/t/grendy-a-drone-synth-for-norns/31721
[app grendy src]: https://github.com/cfdrake/grendy
[app grainfield lines]: https://llllllll.co/t/grainfields-8-voice-granular-synthesizer-for-128-grids-m4l-update/5164
[app greyhole lines]: https://llllllll.co/t/greyhole
[app greyhole src]: https://github.com/justmat/greyhole
[app greyhole demo 1]: https://vimeo.com/379334153
[app haven lines]: https://llllllll.co/t/haven/21285
[app haven src]: https://github.com/tai-studio/haven
[app haven demo 1]: https://www.youtube.com/watch?v=1mEBZmao-uc
[app less_concepts lines]: https://llllllll.co/t/less-concepts/21109
[app less_concepts src]: https://github.com/dndrks/less_concepts
[app less_concepts demo 1]: https://www.youtube.com/watch?v=AHuZm-aHN6k
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
[app mlr lines]: https://llllllll.co/t/mlr-norns
[app mlr src]: https://github.com/tehn/mlr
[app mlr demo 1]: https://vimeo.com/266741634
[app mlr demo 2]: https://www.instagram.com/p/CFpjWyrIvuh/
[app molly_the_poly lines]: https://llllllll.co/t/molly-the-poly
[app molly_the_poly src]: https://github.com/markwheeler/molly_the_poly
[app molly_the_poly demo 1]: https://www.instagram.com/p/BoXJavpAE3R/
[app moln lines]: https://llllllll.co/t/moln/21111
[app moln src]: https://github.com/antonhornquist/moln
[app moln demo 1]: https://www.instagram.com/p/BoXJavpAE3R/
[app nisp lines]: https://llllllll.co/t/nisp
[app nisp src]: https://github.com/itsyourbedtime/NISP
[app nisp demo 1]: https://www.instagram.com/p/B54rUM6hnWJ/
[app nisp demo 2]: https://www.instagram.com/p/B545yPRh5QA/
[app oooooo lines]: https://llllllll.co/t/oooooo/35828
[app oooooo src]: https://github.com/schollz/oooooo
[app oooooo demo 1]: https://www.instagram.com/p/CEeMRPDhCt_/
[app oooooo demo 2]: https://www.instagram.com/p/CEb2CDQBXaz/
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
[app pedalboard lines]: https://llllllll.co/t/31119
[app pedalboard src]: https://github.com/21echoes/pedalboard
[app phyllis lines]: https://llllllll.co/t/phyllis/27988
[app phyllis src]: https://github.com/justmat/phyllis
[app phyllis demo 1]: https://vimeo.com/381676550
[app piwip lines]: https://llllllll.co/t/piwip
[app piwip src]: https://github.com/schollz/piwip
[app piwip demo 1]: https://www.instagram.com/p/CFla2iJh9zC/
[app pools lines]: https://llllllll.co/t/pools
[app pools src]: https://github.com/justmat/pools
[app pools demo 1]: https://vimeo.com/383786715
[app punchcard lines]: https://llllllll.co/t/punchcard
[app punchcard src]: https://github.com/neauoire/punchcard
[app punchcard demo 1]: https://www.youtube.com/watch?v=jZUtkNuEDqY
[app punchcard demo 2]: https://www.youtube.com/watch?v=QO7T6MYkqZo
[app quence lines]: https://llllllll.co/t/quence/29436
[app quence src]: https://github.com/millxing/QUENCE
[app quence demo 1]: https://www.youtube.com/watch?v=w7hcWn9swu4
[app quence demo 2]: https://www.youtube.com/watch?v=ogu7FdoMybw
[app rebound lines]: https://llllllll.co/t/rebound/23243
[app rebound src]: https://github.com/nf/rebound
[app rebound demo 1]: https://www.instagram.com/p/BmSiQgrAhRg/
[app reels lines]: https://llllllll.co/t/reels
[app reels src]: https://github.com/itsyourbedtime/reels
[app reels demo 1]: https://www.youtube.com/watch?v=SuF1uTTlyn4
[app rudiments lines]: https://llllllll.co/t/rudiments-lofi-percussion-synth-and-sequencer-for-norns/31828
[app rudiments src]: https://github.com/cfdrake/rudiments
[app sam lines]: https://llllllll.co/t/sam/23943
[app sam src]: https://github.com/justmat/sam
[app samsara lines]: https://llllllll.co/t/samsara-a-minimalist-looper-v1-0-0/34095
[app samsara src]: https://github.com/21echoes/samsara
[app shapes lines]: https://llllllll.co/t/shapes/36759
[app shapes src]: https://github.com/tlubke/shapes
[app showers lines]: https://llllllll.co/t/showers/31622
[app showers src]: https://github.com/justmat/showers
[app spacetime study]: https://monome.org/docs/norns/study-3/
[app spacetime demo 1]: https://vimeo.com/276054881
[app stack lines]: https://llllllll.co/t/stack-stereo-bandpass-filterbank-for-norns/35218
[app stack src]: https://github.com/cfdrake/stack
[app step lines]: https://llllllll.co/t/step/21093
[app step src]: https://github.com/antonhornquist/step
[app sway lines]: https://llllllll.co/t/sway/21117
[app sway src]: https://github.com/antonhornquist/step
[app sway demo 1]: https://www.youtube.com/watch?v=w9RZHmo4JAs
[app takt lines]: https://llllllll.co/t/takt/21032
[app takt src]: https://github.com/itsyourbedtime/takt
[app takt doc]: https://github.com/monome/dust/blob/master/docs/bedtime/index.md
[app takt demo 1]: https://www.instagram.com/p/Brm-za6FWMZ/
[app timber lines]: https://llllllll.co/t/timber/21407
[app timber src]: https://github.com/markwheeler/timber
[app timber/keys demo 1]: https://www.instagram.com/p/Bs4PuShBTbZ/
[app timber/player demo 1]: https://llllllll.co/uploads/default/original/3X/5/3/53f651f809d88726e5d9ee9b5493908bfefc3313.jpegZ/
[app tunnels lines]: https://llllllll.co/t/tunnels/21973
[app tunnels src]: https://github.com/speakerdamage/tunnels
[app tunnels demo 1]: https://www.instagram.com/p/BwwdlZcls4V/
[app timber lines]: https://llllllll.co/t/21407
[app zeelen lines]: https://llllllll.co/t/zellen/21107
[app zeelen src]: https://github.com/sarweiler/zellen
[app zeelen demo 1]: https://www.youtube.com/watch?v=BawpNsvTHe8
[app zeelen demo crow]: https://www.youtube.com/watch?v=0YFQPW84zM8
