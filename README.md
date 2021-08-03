
# Øvelsesvejledning til øvelse 6 - Styling

#### Slut resultat

## Mappeopsætning

1.   Start med at oprette et nyt projekt.
2.   Installér følgende dependencies;
     - @react-navigation/drawer
     - @react-navigation/native 
     - expo-app-loading 
     - react-native-gesture-handler
     - react-native-reanimated
     - react-native-screens
     - @expo-google-fonts/inter
     - @expo/vector-icons<br/> Et skærmklip af package.json filen til den endelige løsning er vedlagt i bilag A. Din package.json bør være ens med denne efter installeringen         <br/>KOPIER linjen herunder til installering.

        `npm install --save @react-navigation/drawer @react-navigation/native expo-app-loading expo-app-loading react-native-gesture-handler react-native-reanimated react-native-screens @expo-google-fonts/inter @expo/vector-icons`

3. Opret en components-mappe 
4. I mappen oprettes fire js-filer<br/>`Header`<br/>`HomeScreen`<br/>`PlatformScreen`<br/>`ProfileScreen`
5. Der arbejdes udelukkende med funktionelle komponenter.  

## Drawer Navigator - App.js
Man kan med fordel bruge den officielle dokumentation som inspiration:<br/>https://reactnavigation.org/docs/drawer-based-navigation/

1. Opret en instans(en const) af createDrawerNavigator() - `const Drawer = createDrawerNavigator()`<br/>HUSK at createDrawerNavigator() skal importeres.
2. I `return()` oprettes en `<NavigationContainer/>` komponent, der indkapsler `<Drawer.Navigator/>`. 
3. Endeligt oprettes tre `<Drawer.Screen/>` 
4. Importér komponeterne fra components mappen og placer disse i deres respektive `<Drawer.Screen/>`
  - HUSK: referencenavn i `name` og placering af importerede komponenter i `component`
  - Header komponenten skal ikke tages i brug endnu. Den bliver aktuel senere i øvelsen.  
5. Start din app og naviger mellem Home-, platform,- og profilescreen ved brug af din drawer navigator.

## HomeScreen.js
Denne Screen skal indeholde en knap, som skifter farve og titel ved tryk

1. Opret to state variabler ved brug af `useState`<br/>HUSK at importere `useState`
- Variabel 1: Skal registrere knappens aktuelle tilstand - boolean(true/false).
- Variabel 2: Skal dynamisk ændre knappens titel
2. Opret en en button komponent, som i onPress aktiverer en metode, der sætter knappens titel på baggrund af knappens tilstand.
3. Opret nu en styling, som på baggrund af knapvaraiblens tilstand ændrer farve
   - HINT: Anvend en Tenary operator - se eksempel herunder: <br/> https://www.codegrepper.com/code-examples/javascript/ternary+operator+in+style+tag+html

## PlatformScreen.js
Denne komponent skal ændre baggrundsfarve ud fra den enhed, som kører app'en 
I den endelige løsning, vil baggrundsfarven være rød ved anvendelse af en ios-enhed, blå ved anvendelse af en android enhed og grøn, hvis app'en kører i browseren. 

1. Opret en styling, der definerer baggrundsfarven for komponenten.
2. Importér `Platform` fra 'react-native' og benyt denne til at skræddersy baggrundsfarven til den pågælende enhed
    HINT: Se dokumentation her:<br/>https://reactnative.dev/docs/platform-specific-code

## ProfileScreen.js
1. I denne komponent skal der fremvises et vilkårligt billede. Derudover skal der oprettes en knap, ligesom i `HomeScreen`, der kontrollerer skriftstørrelsen og skrifttypen for indholdet af en `<Text><--Indhold-></Text>`, der er placeret lige over knappen. 
Du kan finde forskellige fonts igennem den dependency, som du installerede i første del af øvelsen. For inspiration se følgende dokumentation: <br/>https://docs.expo.dev/guides/using-custom-fonts/

2. Du bør nu være i stand til at slide Drawer Navigatoren ind fra siden og navigere mellem de forskellige screens. I HomeScreen skal den fremviste knap ændre farve og titel ved tryk. I PlatformScreen skal baggrundsfarven ændrer sig afhængigt enheden. I ProfileScreen skal der være fremvist et billede, hvortil der skal være en knap, som ændrer tekstens skriftstørrelse og teksttype. 

## Header.js
Denne komponent skal fungere som en fixed header. Headeren skal være et ikon i venstre hjørne, som ved tryk trækker Drawer Navigatoren ud. 

1. I `return()` skal der oprettes en `<TouchableOpacity/>` komponent. 
2. Header komponenten skal tage props med som argument. 
3. Find det ikon, du vil have fremvist som fast header<br/>Liste med ikoner kan findes her: https://icons.expo.fyi/
4. Placer ikonet i `<TouchableOpacity/>`
5. `<TouchableOpacity/>` skal i `onPress` aktivere en metode, som åbner Drawer Navigatore. Find hjælp i dokumentationen, som blev nævnt i afsnittet om "Drawer Navigator - App.js". 
    - Opret metoden `handleNavigation` og overfør `navigation` som argument til metoden.
    - Syntaks: `const handleNavigation = ({navigation}) => {}`
6. Brug nu den prædefinerede metode, `openDrawer()`, som åbner drwaernavigatoren.
7. Nu skal Headeren importeres i alle komponenter; `HomeScreen`, `PlatformScreen` og `ProfileScreen`.<br/>
    HUSK at placering- og styling af Headeren skal være lavet korrekt, således at ikonet fremvises øverst i venstre hjørne.
    HUSK: at navigation skal overføres til Header komponenten som argument.  
8.Opgaven er hermed løst. Du skal kunne trykke på ikonet i venstre hjørne. Trykket skal åbne drawer navigatoren og tillade dig at navigere mellem de forskellige screens. 

## Bilag

## Bilag A - Package.json - Fra Endelig Løsning 
![img](https://user-images.githubusercontent.com/55731954/128084235-5cc39535-bf44-47f2-9752-8a7e9ba4fe0e.png)


