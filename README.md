# HP-Spectre-x360-ch_fr-fix
Corrige le bug du clavier du HP Spectre x360 15ap07nz qui rend les touches &lt;, > et \ inutilisables

## Mise en place
Modifier dans linux avec les fichiers fournis ou appliquer les différences fournies à la fin.

Une fois la modification effectuée il suffit de lancer la commande suivante:
```bash
$> setxkbmap ch fr_x360
```

Pour plus d'infos sur xkb: https://medium.com/@damko/a-simple-humble-but-comprehensive-guide-to-xkb-for-linux-6f1ad5e13450

## Différences

### base.lst
/usr/share/X11/xkb/rules/base.lst

Après la ligne : "fr_sundeadkeys  ch: French (Switzerland, with Sun dead keys)"

```
fr_x360         ch: French (Switzerland, x360)
```

### base.xml
/usr/share/X11/xkb/rules/base.xml

Après la variant fr_mac
```xml
        <variant>
          <configItem>
            <name>fr_x360</name>
            
            <shortDescription>fr</shortDescription>
            <description>French (Switzerland, x360)</description>
            <languageList>
              <iso639Id>fra</iso639Id>
            </languageList>
          </configItem>
        </variant>
```

### ch

/usr/share/X11/xkb/symbols/ch

Ajouter à la fin
```
xkb_symbols "fr_x360" {
 name[Group1] = "French (Switzerland, x360)";
    include "ch(fr)"
    key <RCTL> { [       less,    greater,    backslash, brokenbar  ] };
 // add here below whatever customization you like
};
```
