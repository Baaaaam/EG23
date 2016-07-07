this calculation run using : 
- cyclus branch: develop -- commit e94a5a3b10131d39c88e77a21dfc36074b0d29d6

- cycamore fork: https://github.com/jlittell/cycamore.git -- branch:cleanstore -- commit bc2eade822fce9f51464324b607ab4227bc7150a


the present simulation includes :

Bo-Feng - ANL - EG23 deployement schedule for all reactors.
the lifetime of each reactor have been set to 80y.

Separation of the LWR fuel are made in a commun facility (R.Carlsen number https://github.com/rwcarlsen/eg23-sim), 3 are deployed : 2 in 2030, 1 in 2040.

Separation for FBR are greedy... (throughput 5e6, Pu output buffer 5e6 so about 1000 batch of MOX)

SFR fuel Fabrication are not gready : 1 fab for 10 SFR reactor deployement schedule, the internal parameters allow a little bit more than 10 MOX batch/y

The main difference between SFR & LWR is the 2 SFR type (A or B) did not share the same FAB and SEPARATION, when the LWR do.


each fuel type (UOX-A/B and SFR-A/B) have they own dedicated cooling storage (7y) and storage.

I have try to put all communs archetypes and recipes in the recycle.xml file, and each reactor type dedicaced ones in the other xml file...

this version is suppose to improve 2015_LWR-group-SEP_SFR-Dedi-SEP version, include a dedicated storage for Recyled Uranium and depleted uranium..
