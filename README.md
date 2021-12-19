# PureData_live_Panoramix_ambisonics

![Schermata 2021-12-19 alle 18 15 19](https://user-images.githubusercontent.com/79996126/146684207-003801e5-def1-442b-bd87-d53b14bccfa3.png)
 
**History and abstract**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

Small framework for playing in Pure Data and handling Ambisonics spatialization via Panoramix.
Pure Data is used as a sound generation engine and Panoramix is used as software for real-time Ambisonics spatialization. 
Panoramix is a post-production workstation for 3D audio contents. This open source software offers a comprehensive environment for mixing, reverberating, and spatializing sound materials and it is developed by Ircam [https://www.ircam.fr/].

There are still many many (many) changes to be made, but I would like to leave the possibility of modifying the framework to anyone.
The framework was realised during the "Computer Music Project" course with JOhannes Zmölnig from IEM (https://iem.kug.ac.at/) of Graz (AT).

The idea was to develop a small framework that allows composers to work on different aspects of Live Electronics and 3D audio in Pure Data.

For the realization of the project various external open source libraries were used that can be integrated with Pure Data, such as:
1) - https://puredata.info/downloads/cyclone - A set of Pure Data objects cloned from Max/MSP
2) - https://github.com/porres/pd-else - ELSE is a big library for Pure Data that provides a cohesive system for computer music, it also serves as a basis for an Live Electronics Tutorial by the same author, Alexandre Torres Porres. This tutorial is also found as part of the download of the ELSE library
3) - https://github.com/TheTechnobear/Mi4Pd - Library for Pure Data that contains some generative sound modules developed like "Mutable Instruments" eurorack modules
4) - https://puredata.info/downloads/zexy - Zexy is a lose collection of objects that provide functionality missing in plain Pure Data


The framework, currently, consists of the following modules related to sound generation: 

• Two "Braids" macro-oscillators which have been modified to my liking and which derive from the codes given free by Emilie Gillet of Mutable Instruments [https://mutable- instruments.net/].

• Two modules that make granular synthesis to different audio samples

• One module that make wavetable synthesis
     
• One module that allow the user to perform a physical model synthesis of an input signal

These 6 sound generation modules in turn can be sent, through send/receive objects, to other 6 modules that act more as FX. At the moment we have a total of 6 modules for sound generation and 6 modules for processing the generated signal and all these send/receive objects are managed by an audio matrix.
Furthermore, in the audio matrix, we have the 16 outputs that are sent to the Panoramix software that takes care of the Ambisonics spatialization of the sound.

At the moment the modules that deal with the FX are the following six:

• Three granular audio processors 

• One digital reverb

• One feedback delay

• One "Freeze" algorithm

**How to use it**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
Open the file containing the main_patch named "main_5_Ambisonics__JULY" in Pure Data.
All abstractions of the main_patch are in the folder "abs" together with samples and stavesave (yet to be implemented).

To connect PureData to Panoramix you need to do a routing via a virtual sound card (e.g. Loopback, Jack) and send the output of PD to the input of Panoramix.
For the project I always used the sample rate set to 48 Khz.
For the realization of this first prototype I used a MacOS system and the virtual sound card "Loopback".
Always make sure that the output of the Pure Data project is set up like this screenshot of "Loopback" on your virtual sound card (bypassing "ZoomAudioDevice"):

![Screenshot_LoopBack](https://user-images.githubusercontent.com/79996126/146686544-ab594126-0a7a-421a-b37a-e7b59542859a.png)

Fireface UFX is my output, but you will have your own sound card there.
Now open Panoramix and load the file "PD_Panoramix_0.3.txt" into Panoramix.
The sound should already be set with Ambisonics encoding (5th order) and binaural decoding.

For any other information or bug please email me at matteotomasetti@libero.it


**Contributors**
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
• Francesco Casanova

