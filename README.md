# Purple Honeycomb Wood (Fabric mod, MC 1.21.11)

Ye mod 2 cheezein karta hai:

1. **Honeycomb Stairs** naam ka naya block add karta hai (Honeycomb Block se craft hota hai, jaise normal stairs).
2. **Oak wood ko purple** kar deta hai (resource-pack style texture override) — planks, log, stripped log, door, trapdoor, wood block — sab ka texture wahi wood-grain pattern hai, bas color purple. Inn se craft hone wali cheezein (stairs, doors, trapdoors, fences) automatically purple dikhengi kyunki wo texture reuse karti hain.

> Agar aap chahte ho ki sirf ek naya "Purple Wood" wood-type bane (oak alag rahe, purple wood alag ho) to bata dena — abhi is version mein maine seedha **oak** ko purple kar diya hai kyunki request mein specific wood type mention nahi tha.

## Folder structure
```
src/main/java/com/example/purplehoney/PurpleHoneyMod.java   -> block/item register karta hai
src/main/resources/fabric.mod.json                          -> mod manifest
src/main/resources/assets/purplehoney/...                   -> honeycomb stairs textures/models
src/main/resources/assets/minecraft/textures/block/...       -> purple oak wood texture overrides
src/main/resources/data/purplehoney/recipe/...                -> crafting recipe
src/main/resources/data/purplehoney/loot_table/...            -> block loot table
```

## GitHub par build kaise karo

`.github/workflows/build.yml` already included hai is zip mein — bas ye karo:

1. Is poore folder ko ek naye GitHub repo mein push kar do (`.github` folder bhi saath jaye, wahi Actions workflow hai).
2. Push hote hi **Actions** tab mein "build" workflow apne aap chalega.
   - Isme `gradlew` use nahi kiya gaya (wrapper jar is zip mein nahi hai kyunki mujhe yaha internet access nahi tha) — iske bajaye `gradle/actions/setup-gradle` action khud Gradle install karke `gradle build` chalata hai. Isliye local machine pe bhi kuch extra setup ki zarurat nahi, bas GitHub pe push karo.
3. Workflow finish hone ke baad, Actions run ke "Artifacts" section mein `purplehoney-mod` naam se zip milega — usme `build/libs/purplehoney-1.0.0.jar` hoga. Wahi apka final mod jar hai — usko mods folder mein daal do (Fabric Loader + Fabric API 1.21.11 ke saath, Minecraft 1.21.11 par).
4. **Local build** karna ho (apni machine par) to Gradle khud install karo aur `gradle build` chala do usi folder mein — wrapper na hone se `./gradlew` kaam nahi karega, seedha `gradle` command use karna.

## Versions check kar lena
`gradle.properties` mein maine Yarn mappings / Fabric API ke jo version daale hain (1.21.11 ke liye), wo build se pehle ek baar [fabricmc.net/develop](https://fabricmc.net/develop) par confirm kar lena — kabhi kabhi exact build numbers change ho jaate hain.
