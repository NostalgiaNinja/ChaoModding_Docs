# Chao Data Structure

Below, you'll find some useful values of the `ChaoDataBase` Struct which is used in the fruit stat function to modify the Chao's attributes accordingly. Please make sure to **[clamp](https://en.wikipedia.org/wiki/Clamping_(graphics))** your values as anything outside of the value scope will provide unintended consequences to the game and/or the Chao.

|Data Type|Variable|Description|
|--------|---------|-----------|
|char[7]|Name|Name of the Chao|
|char[8]|StatGrades|Stat grades from D to S|
|char[8]|StatLevels|Stat levels from 0 to 99|
|int16[8]|StatPoints|Stat points from 0 to 9999|
|ChaoType|Type|Type of Chao - View SA2Structs.h for more info|
|char|Garden|Garden the Chao is in|
|int16|Happiness|Chao Happiness|
|int16|InKindergarten|Is the Chao in Kindergarten?|
|int16|lifespan|Lifespan 1|
|int16|lifespan2|Lifespan 2|
|int16|Reincarnations|How many reincarnations a Chao had|
|float|PowerRun|Power/Run Stat Influence, - for Power, + for Run|
|float|FlySwim|Fly/Swim Stat Influence, - for Fly, + for Swim|
|float|Alignment|Chao Alignment, -1 for Dark, 0 for Normal, 1 for Hero|
|float|EvolutionProgress|Magnitude|
|char|HideFeet|Hide the feet of the Chao?|
|ChaoDNA|DNA|Chao DNA struct - view SA2Structs.h for more info|

Some useful data structures to look at in `SA2Structs.h`:

* ChaoType
* ChaoEmotions
* ChaoCharacterBond
* ChaoDNA