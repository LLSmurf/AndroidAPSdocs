# Troubleshooting

You can find troubleshooting info on many pages in the wiki. This page is a collection of links to help you find the information to solve your problem.

Additional useful information might also be available in the [FAQ](../Getting-Started/FAQ.html).

## AndroidAPS app

### Building & updating

* [Lost keystore](../Installing-AndroidAPS/troubleshooting_androidstudio.md#lost-keystore)
* [Troubleshooting AndroidStudio](../Installing-AndroidAPS/troubleshooting_androidstudio.html)

### Settings
* [Profile](../Usage/Profiles.md#troubleshooting-profile-errors)

  ![Error: Basal not aligned to hours](../images/Screen_DifferentPump.png)

* [Pump - data from different pump](../Installing-AndroidAPS/update3_0.html#failure-message-data-from-different-pump)

  ![Failure message: Data from different pump](../images/BasalNotAlignedToHours2.png)

* [Nightscout Client](../Usage/Troubleshooting-NSClient.html)

### Usage
* [Wrong carb values](../Usage/COB-calculation.md#detection-of-wrong-cob-values)

   ![Error: Slow carb absorption](../images/Calculator_SlowCarbAbsorption.png)

* [SMS commands](../Children/SMS-Commands.md#troubleshooting)

### Frequent bluetooth connection problems

This can happen with various pumps. Apart from excluding AAPS from any battery optimization, you can also exclude the system bluetooth app from battery optimization. This can help in some cases.
Depending on the phone you use, you will find the bluetooth app differently. 

Here are examples how to find them on specific android phones.


#### Pixel phones (stock android)

* Go to the android settings, select "Apps".
  
  ![Android Settings¦Apps](../images/troubleshooting/pixel/01_androidsettings.png)
  
* Select "See all apps"
  
  ![See all apps](../images/troubleshooting/pixel/02_apps.png)
  
* On the menu on the right, select "Show system" apps.
  
  ![Show system apps](../images/troubleshooting/pixel/03_allapps.png)
  
* Now search and select the app "Bluetooth".
  
  ![Bluetooth app](../images/troubleshooting/pixel/03_bluetooth.png)
  
* Click the "App battery usage" and select "Not optimized".
  
  ![BT Battery optimization](../images/troubleshooting/pixel/04_btunrestricted.png)


#### Samsung phones

* Go to the android settings, select "Apps"

* On the icon that supposedly changes the sorting algorithm (1), select "Show system apps" (2).

  ![App Filter](../images/troubleshooting/samsung/Samsung01_Apps.png)
  
  ![Show system apps](../images/troubleshooting/samsung/Samsung02_ShowSystemApps.png)
  
* Now search the bluetooth app and select it to see its settings.
  
  ![Bluetooth App](../images/troubleshooting/samsung/Samsung03_BtApp.png)
  
* Select "battery".
  
  ![Battery](../images/troubleshooting/samsung/Samsung04_Battery.png)
  
* Set it to "Not optimized"
  
  ![Not optimized](../images/troubleshooting/samsung/Samsung05_NotOptimized.png)
  

## CGM

* [General](../Hardware/GeneralCGMRecommendation.md#troubleshooting)
* [Dexcom G6](../Hardware/DexcomG6.html#troubleshooting-g6)
* [Libre 3](../Hardware/Libre3.html#experiences-and-troubleshooting)
* [Libre 2](../Hardware/Libre2.html#experiences-and-troubleshooting)
* [xDrip - no CGM data](../Configuration/xdrip.md#identify-receiver)
* [xDrip - Dexcom troubleshooting](../Configuration/xdrip.md#troubleshooting-dexcom-g5-g6-and-xdrip)

## Pumps

* [DanaRS](../Configuration/DanaRS-Insulin-Pump.md#dana-rs-specific-errors)
* [Accu-Chek Combo general](../Usage/Accu-Chek-Combo-Tips-for-Basic-usage.html)
* [Accu-Chek Combo + Ruffy](../Configuration/Accu-Chek-Combo-Pump.md#why-pairing-with-the-pump-does-not-work-with-the-app-ruffy)
* [Accu-Chek Insight](../Configuration/Accu-Chek-Insight-Pump.md#insight-specific-errors)
* [Medtronic + RileyLink](../Configuration/MedtronicPump.md#what-to-do-if-i-loose-connection-to-rileylink-and-or-pump)

## Phones

* [Jelly](../Usage/jelly.html)
* [Huawei bluetooth & battery optimization](../Usage/huawei.html)

## Smartwatches

* [Troubleshooting Wear app](../Configuration/Watchfaces.md#troubleshooting-the-wear-app)
* [Sony Smartwatch 3](../Usage/SonySW3.html)
