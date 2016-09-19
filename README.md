================
EG23 Calculation
================

Requirement
===========

this calculation run using : 
- cyclus branch: develop -- commit e94a5a3b10131d39c88e77a21dfc36074b0d29d6

- cycamore fork: https://github.com/jlittell/cycamore.git -- branch:cleanstore
  -- commit bc2eade822fce9f51464324b607ab4227bc7150a

the Output.xlsm file have been filled using the CYCLUS2FCO tool:
- https://github.com/Baaaaam/CYCLUS2FCO, branch: master -- commit
  4ab084587538af7b2bad4bf7da05bba3b7610748

this should be working with the last cyclus version.

Calculation description
=======================

the present simulation includes :

Bo-Feng - ANL - EG23 deployement schedule for all reactors.  the lifetime of
each reactor have been set to 80y.

Separation of the LWR fuel are made in a commun facility (R.Carlsen number
https://github.com/rwcarlsen/eg23-sim), 3 are deployed : 2 in 2030, 1 in 2040.

Separation for FBR are greedy... (throughput 5e6, Pu output buffer 5e6 so about
1000 batch of MOX)

SFR fuel Fabrication are not gready : 1 fab for 10 SFR reactor deployement
schedule, the internal parameters allow a little bit more than 10 MOX batch/y

The main difference between SFR & LWR is the 2 SFR type (A or B) did not share
the same FAB and SEPARATION, when the LWR do.


each fuel type (UOX-A/B and SFR-A/B) have they own dedicated cooling storage
(7y) and storage.

I have try to put all communs archetypes and recipes in the recycle.xml file,
and each reactor type dedicaced ones in the other xml file...

this version is suppose to improve 2015_LWR-group-SEP_SFR-Dedi-SEP version,
pinclude a dedicated storage for Recyled Uranium and depleted uranium..



2 cases are available in 3 differents declinations:
  
  - EG01-23_unlimited_reprocessing
  - EG01-23_limited-scheduled_reprocessing

the differences between the 2 cases are the way reprocessing for used fuel are
handled: the ``unlimited_reprocessing`` allows almost unlimited reprocessing
capacity for FBR MOX fuel (UOX fuel preprocessing use limited constant capacity
taken from rcarlsen), the ``limited-scheduled_reprocessing`` do a join
reprocessing (for all used fuels)  the reprocessing capacity is supposed to be
deployed following the plutonium demand.

the 3 differents declinaisions are:
  - basic (no label)
  - sfr_batched
  - sfr_batch_ShotCooling

ithe difference between the first and the last 2 are in the modlisation of the
reactors, their are batched differently, (the 2 second have a batching closer to
the EG23 specifications). The differences between sfr_batched and
sfr_batch_ShotCooling declinaisons are located on the cooling time to include
the time steps require to move materials from a facilities to an other (allowing
to have exactly 7y out of reactor time -- at minimum, if to much reprocessed
fuel the material can be pilled up...).
