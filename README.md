# string-deobfuscator

An extension for [jadx-emu](https://github.com/FlyPhantomFly/jadx-emu) that decrypts strings by emulating the app's decryptor and writes the result back into the decompiled code.

Before:

![before](sample/lsparanoid-before.png)

After:

![after](sample/lsparanoid-after.png)

## Build and install

You need the jadx-emu 0.2.0 engine installed and published to `~/.m2`. See its README.

```
./gradlew jar
cp build/libs/string-deobfuscator-0.0.4.jar ~/.config/jadx/plugins-data/jadx-emu/extensions/
```

## Use

This one runs on every project, so jadx-emu keeps it off until you enable it by its id, `strings`. On the command line:

```
jadx -P"jadx-emu.extensions.enabled=strings" -d out app.apk
```

The log should say `extension 'strings' (AUTO) initialized`.

## Settings

Pass these the same way, as `-P"jadx-emu.strings.<name>=<value>"`.

| name | default | what it does |
|---|---|---|
| rewrite | true | replace decryptor calls with the decrypted string |
| comment | false | add a comment listing the decrypted strings of each method |
| log | true | log each decrypted string |

## Credits and license

Forked from nitanmarcel's jadx-emu-string-deobfuscator. GPLv2, see `LICENSE` and `NOTICE`.
