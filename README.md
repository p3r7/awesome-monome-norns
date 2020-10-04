# awesome-monome-norns


<img src="https://monome.org/images/norns-front-small.jpg" width="500">

A list of links and resources for the [norns](https://monome.org/docs/norns/) hardware music platform by [monome](https://monome.org/).

The community resides mostly on [llllllll.co](https://llllllll.co/) (pronounced _lines_).


## Hardware

There are 2 variations of the norns hardware:

 - [norns](https://market.monome.org/collections/primary/products/norns), relying on a Raspbery Pi CM3 or CM3+
 - [norns shield](https://market.monome.org/collections/primary/products/norns-shield-kit), a HAT for Raspbery Pi 3B or 3B+.


#### norns shield

The **norns shield** option is DIY and more economic but lacks a battery, has no monitor output, a less clean audio path and is more generally less rugged.

For more information about building your own norns using the **norns shield**:

 - [llllllll.co/t/diy-norns-shield](https://llllllll.co/t/diy-norns-shield/27638) for general build help
 - [llllllll.co/t/norns-shield-case-designs](https://llllllll.co/t/norns-shield-case-designs/30347) for building a case

[u/JHC](https://llllllll.co/u/JHC) provided a [nice 3D printing STL design](https://llllllll.co/t/norns-shield-case-designs/30347/224).

[u/okyeron](https://llllllll.co/u/okyeron) created some [nice laser-cut designs](https://llllllll.co/t/norns-shield-case-designs/30347/183) that he also sells for a very reasonable cost [on his online store](https://denki-oto.weebly.com/store/p39/norns-shield-case.html#/).

If you don't have access to a fablab, you can use a laser-cut service such as:

 - [ponoko](https://www.ponoko.com/) (US)
 - [razorlab](https://razorlab.online/) (UK)

For encoder caps, you can look at makers such as Sifam / Selco, the various offerings at aliexpress ([example](https://www.aliexpress.com/item/32781327404.html?spm=2114.13010708.0.0.3a994c4dQ4Aov1)) or even go the [3D printing route](https://llllllll.co/t/diy-norns-shield/27638/876).


#### Hardware companions

Some apps are made to work only with some of other **monome** hardware (such as **grid**, **arc** and **crow**).

Others rely on other input devices such as MIDI controllers (pad, keyboards...) or a computer keyboard.

For discussing those options, see [llllllll.co/t/friends-of-norns](https://llllllll.co/t/friends-of-norns-gear-accessories-etc/17150).



## Development

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

 - [llllllll.co/t/norns-scripting](https://llllllll.co/t/norns-scripting/14120): getting help with app development (lua)
 - [llllllll.co/t/norns-supercollider](https://llllllll.co/t/norns-supercollider/22822): getting help with app development (SuperCollider side)
 - [llllllll.co/t/norns-development](https://llllllll.co/t/norns-development/14073): proposing evloutions to core norns code
 - [llllllll.co/t/exquisite-script-a-collective-scripting-game-for-norns](https://llllllll.co/t/exquisite-script-a-collective-scripting-game-for-norns/34989): a cadavre exquis, collective development of an app


## Libraries & Engines

| engine                                                   | code                                        | description              | provided by                           |
| --                                                       | ---                                         | ---                      | ---                                   |
| [softcut](https://llllllll.co/t/norns-2-0-softcut/20550) |                                             | sample record & playback | installed by default                  |
| ack                                                      | [gh](https://github.com/antonhornquist/ack) | advanced sample playback   | installed by default                  |
| timber                                                   | [gh](https://github.com/markwheeler/timber) | advanced sample playback | [timber](https://llllllll.co/t/21407) |


## Apps

#### List

A list of apps available through [maiden](https://monome.org/docs/norns/maiden/) is available in the [documentation](https://monome.org/docs/norns/app/).

This section is aimed at being more complete and providing more meta-data to select which app corresponds to your needs.


| app                                                                   | on maiden | code                                                | sequencer | synth | sampler           | audio effect | demo                                                                                         | doc                                                                          |
| ---                                                                   | ---       | ---                                                 | ---       | ---   | ---               | ---          | ---                                                                                          | ---                                                                          |
| [arcologies](https://llllllll.co/t/arcologies)                        | X         | [gh](https://github.com/tyleretters/arcologies)     | X         | X     | X                 |              | [gallery](https://tyleretters.github.io/arcologies-docs/gallery)                             | [online](https://tyleretters.github.io/arcologies-docs)                      |
| [arp_index](https://llllllll.co/t/the-arp-index)                      | X         | [gh](https://github.com/markwheeler/arp_index)      |           | X     |                   |              | [1](https://www.instagram.com/p/B140GeKB3ga/)                                                |                                                                              |
| [awake](https://llllllll.co/t/awake)                                  |           | [gh](https://github.com/tehn/awake)                 | X         | X     |                   |              |                                                                                              |                                                                              |
| [barycenter](https://llllllll.co/t/barycenter)                        |           | [gh](https://github.com/echophon/barycenter)        |           | X     |                   |              |                                                                                              |                                                                              |
| [cheat codes](https://llllllll.co/t/cheat-codes)                      |           |                                                     |           |       | X                 |              | [1](https://www.youtube.com/watch?v=gfM5MiYKvxc&t=132s)                                      | [pdf](https://llllllll.co/uploads/short-url/mkkpeOUJCreIwVIP0Jdf8rpfYDJ.pdf) |
| [dunes](https://llllllll.co/t/dunes)                                  |           | [gh](https://github.com/oliviercreurer/dunes)       | X         |       |                   |              | [1](https://llllllll.co/t/dunes/24790)                                                       |                                                                              |
| [greyhole](https://llllllll.co/t/greyhole)                            |           | [gh](https://github.com/justmat/greyhole)           |           |       |                   | X            | [1](https://vimeo.com/379334153)                                                             |                                                                              |
| [mlr](https://llllllll.co/t/mlr-norns)                                |           | [gh](https://github.com/tehn/mlr)                   |           |       | X                 |              | [1](https://vimeo.com/266741634)                                                             |                                                                              |
| [molly_the_poly](https://llllllll.co/t/molly-the-poly)                | X         | [gh](https://github.com/markwheeler/molly_the_poly) |           | X     |                   |              | [1](https://www.instagram.com/p/BoXJavpAE3R/)                                                |                                                                              |
| [nisp](https://llllllll.co/t/nisp)                                    | X         | [gh](https://github.com/itsyourbedtime/NISP)        | X         |       | X (only playback) |              | [1](https://www.instagram.com/p/B54rUM6hnWJ/), [2](https://www.instagram.com/p/B545yPRh5QA/) |                                                                              |
| [pedalboard](https://llllllll.co/t/31119)                             | X         | [gh](https://github.com/21echoes/pedalboard)        |           |       |                   | X            |                                                                                              |                                                                              |
| [piwip](https://llllllll.co/t/piwip)                                  |           |                                                     |           |       |                   | X            | [1](https://www.instagram.com/p/CFla2iJh9zC/)                                                |                                                                              |
| [pools](https://llllllll.co/t/pools)                                  | X         | [gh](https://github.com/justmat/pools)              |           |       |                   | X            | [1](https://vimeo.com/383786715)                                                             |                                                                              |
| [punchcard](https://llllllll.co/t/punchcard)                          | X         | [gh](https://github.com/neauoire/punchcard)         | X         |       |                   |              | [1](https://www.youtube.com/watch?v=QO7T6MYkqZo)                                             |                                                                              |
| [reels](https://llllllll.co/t/reels)                                  | X         | [gh](https://github.com/itsyourbedtime/reels)       |           |       | X                 | X            | [1](https://www.youtube.com/watch?v=SuF1uTTlyn4)                                             |                                                                              |
| [shapes](https://llllllll.co/t/shapes/36759)                          |           |                                                     |           |       |                   |              |                                                                                              |                                                                              |
| [spacetime](https://monome.org/docs/norns/study-3/) `we/study/study3` |           |                                                     |           |       |                   |              |                                                                                              |                                                                              |


#### By I/O

| symbol                 | meaning              |
| ---                    | ---                  |
| :red_circle:           | mandatory            |
| :large_orange_diamond: | strongly encouraged, |
| :white_circle:         | optional             |


| app                                                                   | audio in | midi in                    | keyboard     | grid                   | arc                    | TouchOSC               | audio out | midi out       | crow |
| ---                                                                   | ---      | ---                        | ---          | ---                    | ---                    | ---                    | ---       | ---            | ---  |
| [arcologies](https://llllllll.co/t/arcologies)                        |          |                            |              | :red_circle:           |                        |                        |           |                |      |
| [arp_index](https://llllllll.co/t/the-arp-index)                      |          | :white_circle:             |              |                        |                        |                        | X         | :white_circle: |      |
| [awake](https://llllllll.co/t/awake)                                  |          | :white_circle: (only sync) |              | :white_circle:         |                        |                        | X         |                |      |
| [barycenter](https://llllllll.co/t/barycenter)                        |          |                            |              |                        |                        |                        |           |                |      |
| [cheat codes](https://llllllll.co/t/cheat-codes)                      |          |                            |              | :large_orange_diamond: | :large_orange_diamond: | :large_orange_diamond: |           |                |      |
| [dunes](https://llllllll.co/t/dunes)                                  |          |                            |              |                        |                        |                        | X         |                |      |
| [greyhole](https://llllllll.co/t/greyhole)                            | X        |                            |              |                        |                        |                        | X         |                |      |
| [mlr](https://llllllll.co/t/mlr-norns)                                | X        |                            |              | :red_circle:           |                        |                        | X         |                |      |
| [molly_the_poly](https://llllllll.co/t/molly-the-poly)                |          | X                          |              | :white_circle:         |                        |                        | X         |                |      |
| [nisp](https://llllllll.co/t/nisp)                                    |          |                            | :red_circle: |                        |                        |                        | X         |                |      |
| [pedalboard](https://llllllll.co/t/31119)                             | X        |                            |              |                        |                        |                        | X         |                |      |
| [piwip](https://llllllll.co/t/piwip)                                  |          |                            |              |                        |                        |                        |           |                |      |
| [pools](https://llllllll.co/t/pools)                                  | X        |                            |              |                        |                        |                        | X         |                |      |
| [punchcard](https://llllllll.co/t/punchcard)                          |          |                            |              | :red_circle:           |                        |                        |           | X              |      |
| [reels](https://llllllll.co/t/reels)                                  | X        |                            |              |                        |                        |                        | X         |                |      |
| [shapes](https://llllllll.co/t/shapes/36759)                          |          |                            |              |                        |                        |                        |           |                |      |
| [spacetime](https://monome.org/docs/norns/study-3/) `we/study/study3` |          |                            |              |                        |                        |                        | X         |                |      |
