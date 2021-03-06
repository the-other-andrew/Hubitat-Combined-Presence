# Combined Presence app for Hubitat
An app for Hubitat to combine two or more presence sensors to control an output Virtual Presence Sensor.  The basic bindings use a boolean-OR to combine them.  The advanced bindings can do more complicated combinations.

## Use Case 1
I want to make an output sensor that will be more reliable than either of the input sensors alone.  It uses a boolean-OR to combine them.  This means it will work great if:

- Your input sensors only give false negatives, but do not give false positives.

I can verify that presence from the Alexa app or from HomeKit satisfies this.  I can also verify that my iPhone WiFi Presence Sensor (https://github.com/joelwetzel/Hubitat-iPhone-Presence-Sensor) satisfies this.

However, if your input sensors ever give false positives, then I do not recommend this app.

## Use Case 2
If you have presence sensors for two people, you can use this to set a third Virtual Presence sensor for "Somebody is home", then use the departed event from it in Rule Machine to trigger events for when the last person has left the house.

## Use Case 3
I have documented the advanced bindings here: (https://community.hubitat.com/t/release-combined-presence/9186/35?u=jwetzel1492)

## Daisychaining
This app is entirely virtual and on the Hubitat hub, so it runs very fast.  This means you can daisychain multiple combinations.

An example with 3 combiners:
- "My iPhone Alexa" + "My iPhone WiFi" --> "My combined, reliable presence"
- "My wife's iPhone Alexa" + "My wife's iPhone Wifi" --> "My wife's combined, reliable presence"
- "My combined presence" + "My wife's combined presence" --> "Somebody is home"

Now I can make RM rules based on individual people arriving. And if I want a rule for when the last person leaves the house, I just trigger on "Somebody is home" changing to "not present".

It's nice because it keeps the combination logic outside of Rule Machine.

## Installation

Prerequisites:
- Input sensors already exist
- You've added a Virtual Presence sensor to be the output

1. On your Hubitat hub, go to the "Apps Code" page
2. Click "+ New App"
3. Paste in the contents of combinedPresence.groovy and click "Save"
4. Go back to the "Apps Code" page
5. Click "+ New App"
6. Paste in the contents of combinedPresenceInstance.groovy and click "Save"
7. Click "+ New App"
8. Paste in the contents of advancedCombinedPresenceInstance.groovy and click "Save"
9. Go to the "Apps" page
10. Click "+ Add User App"
11. Choose "Combined Presence"
12. Click "Done"
13. Click on "Combined Presence" in your apps list
14. Click on "Add a new combined presence instance"
15. Choose your input presence sensors
16. Choose your Virtual Presence sensor as the output
15. Click "Done"
