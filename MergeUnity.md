# Merge Unity

## Agregar en C:/Users/¨username¨/.gitconfig el unityyamlmerge

Usando esto `git config --global -e`

```ps
[merge]
        tool = unityyamlmerge
[mergetool "vscode"]
        cmd = "code --wait --merge \"$REMOTE\" \"$LOCAL\" \"$BASE\" \"$MERGED\""
[merge "unityyamlmerge"]
        name = Unity Smart Merge
        driver = C:/Progra~1/Unity/Hub/Editor/6000.0.47f1/Editor/Data/Tools/UnityYAMLMerge.exe merge -p %O %A %B %A
[mergetool "unityyamlmerge"]
    cmd = C:/Progra~1/Unity/Hub/Editor/6000.0.47f1/Editor/Data/Tools/UnityYAMLMerge.exe merge -p "$BASE" "$LOCAL" "$REMOTE" "$MERGED"
```

## Verificación
`git config --global --get-all merge.unityyamlmerge.driver`

`git config --global --get-all mergetool.unityyamlmerge.cmd`

## Resolver conflictos

`git checkout --conflict=merge -- Assets/Scenes/ScanScene.unity`

`git mergetool --tool=unityyamlmerge Assets/Scenes/ScanScene.unity`

## Agregar .gitattributes

```txt
# .gitattributes
*.unity        text eol=lf merge=unityyamlmerge
*.prefab       text eol=lf merge=unityyamlmerge
*.asset        text eol=lf merge=unityyamlmerge
*.anim         text eol=lf merge=unityyamlmerge
*.controller   text eol=lf merge=unityyamlmerge

Packages/packages-lock.json merge=ours
```
