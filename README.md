# Metin2 Client: Neuer Pet-Pfad (npc_pet)

Dieses HowTo beschreibt, wie man den neuen `npc_pet`-Pfad im Client verwendet, um zusätzliche Konfiguration und redundante Dateipfade zu vermeiden. Ursprünglich veröffentlicht auf elitepvpers am [02.09.2015, 15:13](https://www.elitepvpers.com/forum/metin2-pserver-guides-strategies/3851887-c-client-apply-new-pet-path-new-pets.html)

## Vorteile

Wenn ihr diesen Pfad **nicht** nutzt, müsst ihr jede Pet-Resource **zweimal** hinzufügen:
- Modelle in `npc` oder `npc2`
- Texturen in `npc_pet`

Mit dieser Anpassung genügt es, **alles** in `npc_pet` zu speichern.

## Schritt-für-Schritt Anleitung

1. Öffne `RaceManager.cpp` im Client-Source (`GameLib`)
2. Suche nach:

```cpp
else if (__IsNPCRace(race))
```

   innerhalb der Funktion:

```cpp
void __GetRaceResourcePathes(unsigned race, std::vector <std::string>& vec_stPathes)
```

3. Ersetze den Block durch:

```cpp
else if (__IsNPCRace(race))
{
    if (race >= 34001 && race <= 34200)
    {
        vec_stPathes.push_back("d:/ymir work/npc_pet/");
        vec_stPathes.push_back("d:/ymir work/npc/");
        vec_stPathes.push_back("d:/ymir work/npc2/");
    }
    else if (race >= 30000)
    {
        vec_stPathes.push_back ("d:/ymir work/npc2/");
        vec_stPathes.push_back ("d:/ymir work/npc/");
        vec_stPathes.push_back ("d:/ymir work/monster/");
        vec_stPathes.push_back ("d:/ymir work/monster2/");
        vec_stPathes.push_back ("d:/ymir work/guild/");
    } 
    else
    {
        vec_stPathes.push_back ("d:/ymir work/npc/");
        vec_stPathes.push_back ("d:/ymir work/npc2/");
        vec_stPathes.push_back ("d:/ymir work/monster/");
        vec_stPathes.push_back ("d:/ymir work/monster2/");
        vec_stPathes.push_back ("d:/ymir work/guild/");
    }
}
```

## Quelle

- Elitepvpers Post: [C++ Client: Apply new pet path for new pets](https://www.elitepvpers.com/forum/metin2-pserver-guides-strategies/3851887-c-client-apply-new-pet-path-new-pets.html)
- Autor: Mr. Avenue ([weitere Releases & How-To's](http://www.elitepvpers.com/forum/blogs/4818277-mr-avenue/15723-releases-how-tos-von-mr-avenue.html))

## Lizenz

Nur für private Projekte und Bildungszwecke. Keine offizielle Lizenz enthalten.
