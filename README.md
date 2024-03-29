
# Øvelsesvejledning til øvelse 6 - Styling

#### Slut resultat

https://user-images.githubusercontent.com/48329669/128594345-6bae5a1e-2612-4154-855b-e565303df7c2.mp4

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
     - @expo/vector-icons<br/> Et skærmklip af package.json filen til den endelige løsning er vedlagt i bilag A. Din package.json bør være ens med denne efter installeringen blot med nyere versioner         <br/>KOPIER linjen herunder til installering.

        `npx expo install @react-navigation/drawer @react-navigation/native expo-app-loading expo-app-loading react-native-gesture-handler react-native-reanimated react-native-screens @expo-google-fonts/inter @expo/vector-icons`

3. Opret en components-mappe 
4. I mappen oprettes tre js-filer<br/>`HomeScreen`<br/>`PlatformScreen`<br/>`ProfileScreen`.
5. Ydeligere oprettes en mappe, der kades globalStyles, som indeholder js-filen, `GlobalStyles`. <br/>Heri kan der defineres en række styles, som er fælles for alle komponenter. Denne mappe skal IKKE ligge i components mappen, men være en isoleret mappe ligesom components mappen - se mappestruktur i bilag B.
6. I `GlobalStyles` oprettes et StylesSheet; <br/>
`const GlobalStyles = StyleSheet.create({
    container: {
        flex: 1,
        width: '100%'
    },
})
export default GlobalStyles
`
7. For at benytte stylingen, skal du importere `Globalstyles` i den aktuelle komponet, hvorefter denne kan benyttes - se følgende;<br/> `<View style={GlobalStyles.container}></View>`
8. Husk på at global styling giver mening for de komponenter, hvor man ønsker et ensartet udtryk. Der vil stadig blive anvendt lokal- & inline styling de steder, hvor det giver mening. 

## Drawer Navigator - App.js
OBS: der er sket ændringer i React Native, så det kan være nødvendigt for jer, at indsætte følgende kode i Drawer.Navigator: `<Drawer.Navigator useLegacyImplementation={true}>`<br/>
Ændringen kræver også, at du indsætter følgende i din babel.config: `plugins: ['react-native-reanminated/plugin']`
Man kan med fordel bruge den officielle dokumentation som inspiration:<br/>https://reactnavigation.org/docs/drawer-based-navigation/

1. Opret en instans(en const) af createDrawerNavigator() - `const Drawer = createDrawerNavigator()`<br/>HUSK at createDrawerNavigator() skal importeres.
2. I `return()` oprettes en `<NavigationContainer/>`, der indkapsler `<Drawer.Navigator/>`. 
3. Endeligt oprettes tre `<Drawer.Screen/>` komponenter. 
4. Importér komponeterne fra components mappen og placer disse i deres respektive `<Drawer.Screen/>`
  - HUSK: referencenavn i `name` og placering af importerede komponenter i `component`
5. Start din app og navigér mellem Home-, platform,- og profilescreen ved brug af din drawer navigator.
6. HVIS DU HAR FEJL " tried to register two views with the same name" : SÅ INSTALLER SAFE AREA CONTEXT `expo install react-native-safe-area-context`

## Til Mac brugere:

Hvis i oplever fejl ved pga. Drawer Navigation, kan en løsning være at køre nedenstående kommando ind i starter appen:<br>
```npx pod-install ios```

## HomeScreen.js
Denne Screen skal indeholde en knap, som skifter farve og titel ved tryk

1. Opret én state variabel ved brug af `useState`<br/>HUSK at importere `useState`
- Variabel 1: Skal registrere knappens aktuelle tilstand - boolean(true/false).
- HINT: `const [clicked, setClicked] = useState(false)`
2. Opret en en TouchableOpacity komponent, som i onPress aktiverer en metode, der ændrer knappens tilstand ved tryk. For eksempel, hvis knappen aktuelt holder tilstanden false, skal metoden sikre at knappens tilstand bliver true og omvendt.
- Læs dokumentation om knapper hvis i skal bruge inspi: https://reactnative.dev/docs/button
- HINT: ``` <TouchableOpacity
                    style={[GlobalStyles.btn, clicked ? GlobalStyles.color : GlobalStyles.color]}
                    onPress={() => setClicked(!clicked)} >
                </TouchableOpacity> ```
3. Opret nu en styling, som på baggrund af knapvariablens tilstand ændrer farve
   - HINT: Anvend en Tenary operator - se eksempel herunder: <br/> https://www.codegrepper.com/code-examples/javascript/ternary+operator+in+style+tag+html
4. TouchableOpacity skal wrappe et Text element, hvis værdi skal ændre sig afhængigt clicked-variablens tilstand(nøjagtig som farven).

## PlatformScreen.js
Denne komponent skal ændre baggrundsfarve ud fra den enhed, som appen kører på.
I den endelige løsning, vil baggrundsfarven være rød ved anvendelse af en ios-enhed, blå ved anvendelse af en android enhed og grøn, hvis appen kører i browseren. 

1. Opret en styling, der definerer baggrundsfarven for komponenten.
2. Importér `Platform` fra 'react-native' og benyt denne til at skræddersy baggrundsfarven til den pågældende enhed
    HINT: Se dokumentation her:<br/>https://reactnative.dev/docs/platform-specific-code

## ProfileScreen.js
1. I denne komponent skal der fremvises et vilkårligt billede. Derudover skal der oprettes en knap, ligesom i `HomeScreen`, der kontrollerer skriftstørrelsen og skrifttypen for indholdet af en `<Text><--Indhold-></Text>`, der er placeret lige over knappen. 
Du kan finde forskellige fonts igennem den dependency, som du installerede i første del af øvelsen. For inspiration se følgende dokumentation: <br/>https://docs.expo.dev/guides/using-custom-fonts/

2. Du bør nu være i stand til at trække Drawer Navigatoren ind fra siden og navigere mellem de forskellige screens. I HomeScreen skal den fremviste knap ændre farve og tekstindhold ved tryk. I PlatformScreen skal baggrundsfarven ændre sig afhængigt af enheden. I ProfileScreen skal der være fremvist et billede, hvortil der skal være en knap, som ændrer tekstens skriftstørrelse og teksttype. 

8. Opgaven er hermed løst. Du skal kunne trykke på ikonet i venstre hjørne. Trykket skal åbne drawer navigatoren og tillade dig at navigere mellem de forskellige screens. 

## Nice link

https://coolors.co/

Heri kan I danne super nice farve kombinationer som gør jer applikation virkelig lækker at se på!

## Bilag

## Bilag A - Package.json - Fra Endelig Løsning 
![img](https://user-images.githubusercontent.com/55731954/128084235-5cc39535-bf44-47f2-9752-8a7e9ba4fe0e.png)

## Bilag B - mappestruktur
<img width="350" alt="mappestruktur" src="https://user-images.githubusercontent.com/55731954/136088670-f3ba9f91-d257-4677-b12f-a68e1d8f42eb.PNG">


