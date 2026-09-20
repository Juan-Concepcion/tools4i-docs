# Installing Tools4i

[Requirements](#requirements) ·
[From the VS Code Marketplace](#from-the-vs-code-marketplace) ·
[From Open VSX](#from-open-vsx-and-ibm-bob) ·
[From a packaged file](#from-a-packaged-vsix-file) ·
[Updating](#updating) ·
[Removing it](#removing-it) ·
[If something does not work](#if-something-does-not-work) ·
[Español](#instalación-en-español)

## Requirements

| What | Why |
|---|---|
| **Visual Studio Code 1.118 or later**, or an IBM Bob built on that version or a newer one (the Bob 2.1 line is) | The extension is built against that API level and will not install on an older editor. |
| **[Code for IBM i](https://marketplace.visualstudio.com/items?itemName=HalcyonTechLtd.code-for-ibmi)** | Tools4i is built on top of it and declares it as a required dependency, so the editor installs it for you. |
| **An active IBM i connection** | Tools4i works through the connection Code for IBM i already holds. It never opens a connection of its own, and it will not activate without that extension present. |

Nothing else is needed. No account, no licence key, no server-side installation.

## From the VS Code Marketplace

The usual way, and the one that keeps you up to date.

1. Open the **Extensions** view (**Ctrl+Shift+X**, or **Shift+Cmd+X** on macOS).
2. Search for **Tools4i** and click **Install**.
3. Code for IBM i is installed with it if it isn't there already.

New versions arrive from there automatically, like any other extension.

Direct link:
<https://marketplace.visualstudio.com/items?itemName=tools4i.tools4i>

The package published on the Marketplace is signed, and VS Code verifies that
signature when it installs the extension.

## From Open VSX, and IBM Bob

Editors that do not use Microsoft's Marketplace read from
[Open VSX](https://open-vsx.org/extension/tools4i/tools4i) instead. That includes
**IBM Bob**, IBM's own build of VS Code, along with VSCodium and similar builds.

1. Open the **Extensions** view.
2. Search for **Tools4i** and install it.

If your editor's Extensions view is not pointed at Open VSX, download the file
from the Open VSX page and install it as described in the next section.

## From a packaged .vsix file

This is the way to install on a machine that cannot reach an editor marketplace,
and the way to put a particular version on a machine that already has another.

**Where to download it.** Both marketplaces hand out the packaged file, and both
keep the older versions as well:

- **[Open VSX](https://open-vsx.org/extension/tools4i/tools4i)** offers the
  current build on the extension page. Any published version can be fetched
  directly, by putting the version number into this address twice:

  ```
  https://open-vsx.org/api/tools4i/tools4i/<version>/file/tools4i.tools4i-<version>.vsix
  ```

  The same page also publishes a signature file beside each build.
- **[The Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=tools4i.tools4i)**
  offers the current build from the extension page, and its **Version History**
  tab lists the earlier ones, each with its own download.

If what you need is not there, ask at tools4i.support@gmail.com.

**From the editor**

1. Download the `.vsix` file.
2. Open the **Extensions** view.
3. Click the **...** (More Actions) menu at the top, then **Install from VSIX**.
4. Select the file you downloaded.
5. Reload the window if you are asked to.

**From the command line**

```sh
code --install-extension tools4i-<version>.vsix
```

**If the machine has no internet access**, install **Code for IBM i** first, from
its own `.vsix`. It has to be present for Tools4i to activate, and an offline
editor cannot fetch it on its own.

## Updating

- Installed from a marketplace: nothing to do. VS Code updates it like any other
  extension.
- Installed from a file: download the newer `.vsix` and install it the same way.
  It replaces the previous version in place.

What changed in each version is in [CHANGELOG.md](CHANGELOG.md).

## Removing it

Use **Uninstall** in the Extensions view, or:

```sh
code --uninstall-extension tools4i.tools4i
```

Uninstalling removes the extension. Your settings stay in VS Code, ready for the
next time you install it, and nothing is left behind on the IBM i.

## If something does not work

**The Tools4i view is not in the Activity Bar.** Check that Code for IBM i is
installed and enabled. Without it, Tools4i does not activate. The view can also be
reached from the Command Palette by running any Tools4i command by name.

**A tool says there is no connection.** Tools4i uses the connection Code for IBM i
holds. Connect from the Code for IBM i view first, then run the tool again.

**The editor refuses to install the package.** That is usually the editor version.
Tools4i needs VS Code 1.118 or later; check **Help**, then **About**.

**Still stuck?** Open an issue at
<https://github.com/Juan-Concepcion/tools4i-docs/issues> with your editor version,
your Code for IBM i version, the Tools4i version and what you saw. Or write to
tools4i.support@gmail.com.

---

## Instalación en español

**Requisitos:** Visual Studio Code 1.118 o posterior, o un IBM Bob construido
sobre esa versión o una más reciente (la línea Bob 2.1 lo está), la extensión
[Code for IBM i](https://marketplace.visualstudio.com/items?itemName=HalcyonTechLtd.code-for-ibmi)
(se instala sola como dependencia obligatoria) y una conexión activa a su IBM i.
Tools4i trabaja a través de esa conexión y nunca abre una propia. No hace falta
cuenta, ni clave de licencia, ni instalar nada en el servidor.

**Desde el Marketplace de VS Code**, que es la vía habitual y la que lo mantiene
actualizado:

1. Abra la vista **Extensiones** (**Ctrl+Shift+X**, o **Shift+Cmd+X** en macOS).
2. Busque **Tools4i** y pulse **Instalar**.

Las versiones nuevas llegan solas desde ahí. El paquete publicado en el
Marketplace está firmado, y VS Code comprueba esa firma al instalarlo.

**Desde Open VSX**, que es de donde leen los editores que no usan el Marketplace
de Microsoft, **IBM Bob** entre ellos: busque **Tools4i** en la vista de
Extensiones, o descargue el archivo desde
<https://open-vsx.org/extension/tools4i/tools4i>.

**Desde un archivo `.vsix`**, que es la vía para una máquina que no alcanza ningún
marketplace, y también para poner una versión concreta en una que ya tiene otra.
Los dos marketplaces entregan el archivo y conservan las versiones anteriores:

- **[Open VSX](https://open-vsx.org/extension/tools4i/tools4i)** ofrece la
  compilación actual en la página de la extensión, y cualquier versión publicada
  se descarga directamente poniendo su número dos veces en esta dirección:

  ```
  https://open-vsx.org/api/tools4i/tools4i/<versión>/file/tools4i.tools4i-<versión>.vsix
  ```

- **[El Marketplace de Visual Studio](https://marketplace.visualstudio.com/items?itemName=tools4i.tools4i)**
  ofrece la actual en la página de la extensión, y lista las anteriores en su
  pestaña **Version History**, cada una con su propia descarga.

Si lo que necesita no está ahí, escriba a tools4i.support@gmail.com. Con el
archivo ya en su equipo, use el menú **...** de la vista de Extensiones, opción
**Instalar desde VSIX**, o bien:

```sh
code --install-extension tools4i-<versión>.vsix
```

Si la máquina no tiene acceso a internet, instale antes **Code for IBM i** desde su
propio `.vsix`: tiene que estar presente para que Tools4i se active.

**Para actualizar**, instale un `.vsix` más reciente de la misma forma, o deje que
el marketplace lo haga. **Para desinstalar**, use **Desinstalar** en la vista de
Extensiones. No queda nada en el IBM i.

**¿Problemas?** Si la vista Tools4i no aparece, compruebe que Code for IBM i está
instalada y activada. Si una herramienta dice que no hay conexión, conéctese
primero desde la vista de Code for IBM i. Y si sigue atascado, abra una issue en
<https://github.com/Juan-Concepcion/tools4i-docs/issues> o escriba a
tools4i.support@gmail.com. Puede hacerlo en español.
