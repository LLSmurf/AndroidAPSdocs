# Funkce OpenAPS

(autosens)=

## Autosens

* Autosens je algoritmus, který sleduje odchylky glykémie (pozitivní/negativní/neutrální).
* Pokusí se zjistit, jak citlivý(-á)/rezistentní jste na základě těchto odchylek.
* Realizace algoritmu oref v ** OpenAPS ** pracuje s kombinací dat za 24 a 8 hodin. Používá ta, která jsou více senzitivní.
* Ve verzích předcházejících AAPS 2.7 si uživatel musel vybrat mezi 8 nebo 24 hodinami ručně.
* Od AAPS 2.7 Autosens nyní pro výpočet citlivosti přepíná mezi 24 a 8 hodinovým úsekem. Vybere, která z nich je citlivější. 
* Pokud uživatelé pocházejí z Oref1, pravděpodobně si všimnou toho, že systém může být méně dynamický na změny, v závislosti na citlivosti za 24 nebo 8 hodin.
* Changing a cannula or changing a profile will reset Autosens ratio back to 100% (a percentual profile switch with duration won't reset autosens).
* Autosens adjusts your basal and ISF (i.e.: mimicking what a Profile shift does).
* Pokud budete nepřetržitě po delší dobu jíst sacharidy, Autosense bude během této doby méně efektivní, protože období se sacharidy jsou vyloučena z výpočtů odchylek glykémie.

(super-micro-bolus-smb)=

## Super Micro Bolus (SMB)

SMB, the shortform of 'super micro bolus', is the latest OpenAPS feature (from 2018) within the Oref1 algorithm. In contrast to AMA, SMB does not use temporary basal rates to control glucose levels, but mainly **small super microboluses**. In situations where AMA would add 1.0 IU insulin using a temporary basal rate, SMB delivers several super microboluses in small steps at **5 minute intervals**, e.g. 0.4 IU, 0.3 IU, 0.2 IU and 0.1 IU. At the same time (for safety reasons) the actual basal rate is set to 0 IU/h for a certain period to prevent overdose (**'zero-temping'**). This allows the system adjust the blood glucose faster than with the temporary basal rate increase in AMA.

Thanks to SMB, it can basically be sufficient for low-carb meals to inform the system of the planned amount of carbohydrate and leave the rest to AAPS. However, this may lead to higher postprandial peaks because pre-bolusing isn’t possible. Or you give, if necessary with pre-bolusing, a **start bolus**, which **only partly** covers the carbohydrates (e.g. 2/3 of the estimated amount) and let SMB fill up the rest.

The SMB feature contains some safety mechanisms:

1. Největší jednotlivý mikrobolus může být pouze nejmenší hodnota z:
    
    * hodnota aktuálního bazálního inzulínu (upravená pomocí automatické detekce citlivosti) pro dobu přednastavenou ve volbě „Maximální počet minut bazálu, ke kterým se limituje SMB“, např. bazální dávka inzulínu pro následujících 30 minut, nebo
    * polovina aktuálně požadované dávky inzulínu, nebo
    * zbývající část nastavené hodnoty maxIOB.

2. Pravděpodobně bude často docházet ze strany AAPS k dočasnému snížení hodnoty bazálního inzulínu nebo bude dávkování bazálního inzulín vypnuto úplně. Dochází k tomu z bezpečnostních důvodů a při správném nastavení systému to nemá negativní vliv na hodnoty glykémie. Křivka IOB je pro vyhodnocení očekávaného vývoje důležitější než nastavení bazálního profilu.

3. Dodatečné kalkulace zaměřené na odhad vývoje glykémie pomocí funkce UAM (detekce neoznámených jídel). I bez zadání hodnoty sacharidů do systému detekuje UAM automaticky výrazný vzestup glykémie způsobené jídlem, adrenalinem nebo jinými vlivy a pomocí SMB na ně reaguje. V zájmu zachování bezpečnosti to funguje i opačně a deaktivuje SMB dříve, pokud dojde k neočekávanému poklesu glykémie. To je důvod, proč by funkce UAM měla být při používání SMB vždy aktivní.

**You must have started [objective 9](../Usage/Objectives.md#objective-9-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb) to use SMB.**

See also: [OpenAPS documentation for oref1 SMB](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html) and [Tim's info on SMB](https://www.diabettech.com/artificial-pancreas/understanding-smb-and-oref1/).

(max-u-h-a-temp-basal-can-be-set-to-openaps-max-basal)=

### Pro množství dočasné bazální dávky inzulínu U/h lze nastavit maximální hodnotu (OpenAPS "max-basal")

This safety setting determines the maximum temporary basal rate the insulin pump may deliver. The value should be the same in the pump and in AAPS and should be at least 3 times the highest single basal rate set.

Example:

Your basal profile’s highest basal rate during the day is 1.00 U/h. Then a max-basal value of at least 3 U/h is recommended.

But you cannot choose any value. AAPS limits the value as a 'hard limit' according to the patients age you have selected under settings. The lowest permitted value is for children and the highest for insulin-resistant adults.

AndroidAPS limits the value as follows:

* Děti: 2
* Dospívající: 5
* Dospělí: 10
* Dospělí s vyšší rezistencí na inzulín: 12
* Těhotná: 25

*See also [overview of hard-coded limits](../Usage/Open-APS-features.md#overview-of-hard-coded-limits).*

(maximum-total-iob-openaps-cant-go-over-openaps-max-iob)=

### Nastavenou maximální hodnotu IOB nelze překročit (OpenAPS "max-iob")

This value determines which maxIOB has to be considered by AAPS running in closed loop mode. If the current IOB (e.g. after a meal bolus) is above the defined value, the loop stops dosing insulin until the IOB limit is below the given value.

Using the OpenAPS SMB, max-IOB is calculated differently than in OpenAPS AMA. In AMA, maxIOB was just a safety-parameter for basal IOB, while in SMB-mode, it also includes bolus IOB. A good start is

    max IOB = průměrná hodnota bolusů podávaných před jídlem + 3násobek nejvyšší hodnoty v bazálním profilu
    

Be careful and patient and only change the settings step by step. It is different for anyone and also depends on the average total daily dose (TDD). For safety reason, there is a limit, which depends on the patient age . The 'hard limit' for maxIOB is higher than in [AMA](../Usage/Open-APS-features.md#max-u-hr-a-temp-basal-can-be-set-to-openaps-max-basal).

* Děti: 3
* Dospívající: 7
* Dospělí: 12
* Dospělí s vyšší rezistencí na inzulín: 25
* Těhotná: 40

*See also [overview of hard-coded limits](../Usage/Open-APS-features.md#overview-of-hard-coded-limits).*

See also [OpenAPS documentation for SMB](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html#understanding-super-micro-bolus-smb).

### Enable AMA Autosens

Here, you can choose if you want to use the [sensitivity detection](../Configuration/Sensitivity-detection-and-COB.md) 'autosens' or not.

(enable-smb)=

### Povolit SMB

Here you can enable or completely disable SMB feature.

### Povolit SMB se sacharidy

SMB is working when there is COB active.

### Povolit SMB s dočasnými cíli

SMB is working when there is a low or high temporary target active (eating soon, activity, hypo, custom)

### Povolit SMB s vysokými dočasnými cíli

SMB is working when there is a high temporary target active (activity, hypo). This option can limit other SMB Settings, i.e. if ‘SMB with temp targets’ is enabled and ‘SMB with high temp targets’ is deactivated, SMB just works with low and not with high temp targets. It is the same for enabled SMB with COB: if 'SMB with high temp target' is deactivated, there is no SMB with high temp target even if COB is active.

(enable-smb-always)=

### Vždy povolit SMB

SMB is working always (independent of COB, temp targets or boluses). For safety reasons, this option is just possibly for BG sources with a nice filtering system for noisy data. For now, it just works with a Dexcom G5 or G6, if using the ['Build your own Dexcom App'](../Hardware/DexcomG6.md#if-using-g6-with-build-your-own-dexcom-app) or “native mode” in xDrip+. If a BG value has a too large deviation, the G5/G6 doesn’t send it and waits for the next value in 5 minutes.

For other CGM/FGM like Freestyle Libre, ‘SMB always’ is deactivated until xDrip+ has a better noise smoothing plugin. You can find more [here](../Usage/Smoothing-Blood-Glucose-Data-in-xDrip.md).

### Povolit SMB po jídle

SMB is working for 6h after carbohydrates , even if COB is at 0. For safety reasons, this option is just possibly for BG sources with a nice filtering system for noisy data. For now, it just works with a Dexcom G5 or G6, if using the ['Build your own Dexcom App'](../Hardware/DexcomG6.md#if-using-g6-with-build-your-own-dexcom-app) or “native mode” in xDrip+. If a BG value has a too large deviation, the G5 doesn’t send it and waits for the next value in 5 minutes.

For other CGM/FGM like Freestyle Libre, 'Enable SMB after carbs' is deactivated until xDrip+ has a better noise smoothing plugin. You can find [more information here](../Usage/Smoothing-Blood-Glucose-Data-in-xDrip.md).

(ax-minutes-of-basal-to-limit-smb-to)=

### Maximální počet minut bazálu, ke kterým se limituje SMB

This is an important safety setting. This value determines how much SMB can be given based on the amount of basal insulin in a given time, when it is covered by COBs.

This makes the SMB more aggressive. For the beginning, you should start with the default value of 30 minutes. After some experience, you can increase the value with 15 minutes steps and watch how these changes are affecting.

It is recommended not to set the value higher than 90 minutes, as this would lead to a point where the algorithm might not be able to adjust a decreasing BG with 0 IE/h basal ('zero-temp'). You should also set alarms, especially if you are still testing new settings, which warns you before running into hypos.

Default value: 30 min.

### Povolit UAM

With this option enabled, the SMB algorithm can recognize unannounced meals. This is helpful, if you forget to tell AndroidAPS about your carbs or estimate your carbs wrong and the amount of entered carbs is wrong or if a meal with lots of fat and protein has a longer duration than expected. Without any carb entry, UAM can recognize fast glucose increasements caused by carbs, adrenaline, etc, and tries to adjust it with SMBs. This also works the opposite way: if there is a fast glucose decreasement, it can stop SMBs earlier.

**Therefore, UAM should always be activated when using SMB.**

### Vysoký dočasný cíl zvýší senzitivitu

If you have this option enabled, the insulin sensitivity will be increased while having a temporary target over 100 mg/dl or 5.6 mmol/l. This means, the ISF will rise while IC and basal will decrease.

### Nízký dočasný cíl sníží senzitivitu

If you have this option enabled, the insulin sensitivity will be decreased while having a temporary target lower than 100 mg/dl or 5.6 mmol/l. This means, the ISF will decrease while IC and basal will rise.

### Rozšířená nastavení

**Always use short average delta instead of simple data** If you enable this feature, AndroidAPS uses the short average delta/blood glucose from the last 15 minutes, which is usually the average of the last three values. This helps AndroidAPS to work more steady with noisy data sources like xDrip+ and Libre.

**Max daily safety multiplier** This is an important safety limit. The default setting (which is unlikely to need adjusting) is 3. This means that AndroidAPS will never be allowed to set a temporary basal rate that is more than 3x the highest hourly basal rate programmed in a user’s pump. Example: if your highest basal rate is 1.0 U/h and max daily safety multiplier is 3, then AndroidAPS can set a maximum temporary basal rate of 3.0 U/h (= 3 x 1.0 U/h).

Default value: 3 (shouldn’t be changed unless you really need to and know, what you are doing)

**Current Basal safety multiplier** This is another important safety limit. The default setting (which is also unlikely to need adjusting) is 4. This means that AndroidAPS will never be allowed to set a temporary basal rate that is more than 4x the current hourly basal rate programmed in a user’s pump.

Default value: 4 (shouldn’t be changed unless you really need to and know, what you are doing)

* * *

(advanced-meal-assist-ama)=

## Advanced Meal Assist (AMA)

AMA, the short form of "advanced meal assist" is an OpenAPS feature from 2017 (oref0). OpenAPS Advanced Meal Assist (AMA) allows the system to high-temp more quickly after a meal bolus if you enter carbs reliably.

You can find more information in the [OpenAPS documentation](https://newer-docs.readthedocs.io/en/latest/docs/walkthrough/phase-4/advanced-features.html#advanced-meal-assist-or-ama).

(max-u-hr-a-temp-basal-can-be-set-to-openaps-max-basal)=

### Max. povolený bazál U/h (OpenAPS "max-basal")

This safety setting helps AndroidAPS from ever being capable of giving a dangerously high basal rate and limits the temp basal rate to x U/h. It is advised to set this to something sensible. A good recommendation is to take the highest basal rate in your profile and multiply it by 4 and at least 3. For example, if the highest basal rate in your profile is 1.0 U/h you could multiply that by 4 to get a value of 4 U/h and set the 4 as your safety parameter.

You cannot chose any value: For safety reason, there is a 'hard limit', which depends on the patient age. The 'hard limit' for maxIOB is lower in AMA than in SMB. For children, the value is the lowest while for insulin resistant adults, it is the biggest.

The hardcoded parameters in AndroidAPS are:

* Děti: 2
* Dospívající: 5
* Dospělí: 10
* Dospělí s vyšší rezistencí na inzulín: 12
* Těhotná: 25

*See also [overview of hard-coded limits](../Usage/Open-APS-features.md#overview-of-hard-coded-limits).*

### Maximum basal IOB OpenAPS can deliver \[U\] (OpenAPS "max-iob")

This parameter limits the maximum of basal IOB where AndroidAPS still works. If the IOB is higher, it stops giving additional basal insulin until the basal IOB is under the limit.

The default value is 2, but you should be rise this parameter slowly to see how much it affects you and which value fits best. It is different for anyone and also depends on the average total daily dose (TDD). For safety reason, there is a limit, which depends on the patient age . The 'hard limit' for maxIOB is lower in AMA than in SMB.

* Děti: 3
* Dospívající: 5
* Dospělí: 7
* Dospělí s vyšší rezistencí na inzulín: 12
* Těhotná: 25

*See also [overview of hard-coded limits](../Usage/Open-APS-features.md#overview-of-hard-coded-limits).*

### Enable AMA Autosens

Here, you can chose, if you want to use the [sensitivity detection](../Configuration/Sensitivity-detection-and-COB.md) autosens or not.

### Autosens adjust temp targets too

If you have this option enabled, autosens can adjust targets (next to basal and ISF), too. This lets AndroidAPS work more 'aggressive' or not. The actual target might be reached faster with this.

### Rozšířená nastavení

**Always use short average delta instead of simple data** If you enable this feature, AndroidAPS uses the short average delta/blood glucose from the last 15 minutes, which is usually the average of the last three values. This helps AndroidAPS to work more steady with noisy data sources like xDrip+ and Libre.

**Max daily safety multiplier** This is an important safety limit. The default setting (which is unlikely to need adjusting) is 3. This means that AndroidAPS will never be allowed to set a temporary basal rate that is more than 3x the highest hourly basal rate programmed in a user’s pump. Example: if your highest basal rate is 1.0 U/h and max daily safety multiplier is 3, then AndroidAPS can set a maximum temporary basal rate of 3.0 U/h (= 3 x 1.0 U/h).

Default value: 3 (shouldn’t be changed unless you really need to and know, what you are doing)

**Current Basal safety multiplier** This is another important safety limit. The default setting (which is also unlikely to need adjusting) is 4. This means that AndroidAPS will never be allowed to set a temporary basal rate that is more than 4x the current hourly basal rate programmed in a user’s pump.

Default value: 4 (shouldn’t be changed unless you really need to and know, what you are doing)

**Bolus snooze dia divisor** The feature “bolus snooze” works after a meal bolus. AAPS doesn’t set low temporary basal rates after a meal in the period of the DIA divided by the “bolus snooze”-parameter. The default value is 2. That means with a DIA of 5h, the “bolus snooze” would be 5h : 2 = 2.5h long.

Default value: 2

(overview-of-hard-coded-limits)=

## Přehled pevně naprogramovaných limitů

<table border="1">
  
<thead>
  <tr>
    <th width="200"></th>
    <th width="75">Dítě</th>
    <th width="75">Dospívající</th>
    <th width="75">Dospělý</th>
    <th width="75">Dospělý s nízkou citlivostí</th>
    <th width="75">Těhotná</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>MAXBOLUS</td>
    <td>5,0</td>
    <td>10,0</td>
    <td>17,0</td>
    <td>25,0</td>
    <td>60,0</td>
  </tr>
  <tr>
    <td>MINDIA</td>
    <td>5,0</td>
    <td>5,0</td>
    <td>5,0</td>
    <td>5,0</td>
    <td>5,0</td>
  </tr>
  <tr>
    <td>MAXDIA</td>
    <td>7,0</td>
    <td>7,0</td>
    <td>7,0</td>
    <td>7,0</td>
    <td>10,0</td>
  </tr>
  <tr>
    <td>MINIC</td>
    <td>2,0</td>
    <td>2,0</td>
    <td>2,0</td>
    <td>2,0</td>
    <td>0,3</td>
  </tr>
  <tr>
    <td>MAXIC</td>
    <td>100,0</td>
    <td>100,0</td>
    <td>100,0</td>
    <td>100,0</td>
    <td>100,0</td>
  </tr>
  <tr>
    <td>MAXIOB_AMA</td>
    <td>3,0</td>
    <td>5,0</td>
    <td>7,0</td>
    <td>12,0</td>
    <td>25,0</td>
  </tr>
  <tr>
    <td>MAXIOB_SMB</td>
    <td>7,0</td>
    <td>13,0</td>
    <td>22,0</td>
    <td>30,0</td>
    <td>70,0</td>
  </tr>
  <tr>
    <td>MAXBASAL</td>
    <td>2,0</td>
    <td>5,0</td>
    <td>10,0</td>
    <td>12,0</td>
    <td>25,0</td>
  </tr>
</tbody>
</table>