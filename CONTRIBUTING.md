# Contributing

Tools4i is maintained by one person, and it got where it is because IBM i
developers said what was slowing them down. So there is plenty to contribute
here, even though the extension's source code is not published.

Quick version: [report a bug](#report-a-bug), [suggest an
idea](#suggest-an-idea), [fix the documentation](#fix-the-documentation),
[test a build](#test-a-build). Write in English or in Spanish, whichever you
think in.

## What this repository is

This repository holds the documentation: what the extension does, how to install
it, what changed in each version, and the issue tracker. The extension's source
code is not published, so there are no pull requests to the extension itself.

Everything else is open: the bugs you find, the tools you wish existed, the
sentence in these pages that reads badly, and the release you tried on a system
nobody else has.

## Report a bug

Open a
[bug report](https://github.com/Juan-Concepcion/tools4i-docs/issues/new/choose)
and fill in the template. It asks for the Tools4i version, the Code for IBM i
version, your editor and its version, your operating system and your IBM i
release, because almost every "works here, not there" turns out to be one of
those.

Two things make a report land faster:

- **Say what you expected**, not only what happened. Sometimes the tool is doing
  what it was built to do and the disagreement is about what it should do, which
  is a different fix.
- **Give the steps from the start**, meaning from opening the tool, including
  what you typed in the boxes.

**Please keep real data out of it.** Replace library, object, member, user and
file names with invented ones, and crop screenshots. Everything in an issue is
public, and a bug can be understood perfectly well with made-up names.

## Suggest an idea

Open a
[feature request](https://github.com/Juan-Concepcion/tools4i-docs/issues/new/choose).
The template asks for the problem before the solution on purpose: the tool that
gets built is often not the one first asked for, but it solves the same problem.

What moves an idea up the list:

- **How often the task comes up.** Something you do every week beats something
  you did once.
- **How many people it affects**, in your shop and in general.
- **What you do today instead**, especially if the answer is leaving the editor
  for another tool, or doing by hand what a machine could count.

Ideas that need a specific IBM i release, or a licensed program not everybody
has, are still welcome. Just say so, because it changes who can use the result.

## Fix the documentation

Pull requests are welcome in this repository, for the documentation itself:
typos, broken links, a paragraph that reads badly, an example that does not help,
a missing step in the installation notes, and improvements to the Spanish
translation.

Four rules, which are the same ones the existing pages follow:

1. **No real data.** Invented names in every example. Standard IBM i names are of
   course fine.
2. **No internals.** These pages are written for the person using the extension,
   so they describe what a tool does, not how it is built, and carry no code
   identifiers, no queries and no file-format detail.
3. **Keep both README files in step.** If you change one, change the other, or
   say in the pull request that you could not and which one is now behind.
4. **No em dash.** Use a colon, a comma, brackets or a new sentence. It is a house
   style thing, and the whole repository is written that way.

Keep a pull request to one subject. Two unrelated fixes are easier to read, and
to accept, as two pull requests.

## Test a build

The most useful thing somebody with a different system can do. If you are willing
to try a build before it is published, say so in an issue and you will be pointed
at the file.

What to report back is short: your IBM i release, your editor, your operating
system, what you exercised, and anything that behaved differently from the
version you were on. A system with a different release, a different character set
or simply a much larger library finds things that no amount of testing on one
machine will.

## What to expect

This is a one-person project, so a reply can take a few days. What happens after
that:

- A bug that can be reproduced gets fixed in a later version. The fix is published
  to both marketplaces and described in [CHANGELOG.md](CHANGELOG.md), and the
  issue is closed pointing at the version that carries it.
- A bug that cannot be reproduced stays open while there is something left to try,
  and you will be asked for whatever is missing rather than left guessing.
- An idea that fits gets built when it reaches the top of the list, which can take
  a while. An idea that does not fit is said so plainly, with the reason.
- A documentation pull request is usually the quickest of all.

Nothing is closed silently.

## Security

Please report anything security related **privately**, by email to
tools4i.support@gmail.com, rather than in a public issue. The details are in
[SECURITY.md](SECURITY.md).

## Being civil

Say what is wrong as directly as you like. Aim it at the software, not at the
person, and assume the other side is trying to help. That is the whole code of
conduct.

---

## Cómo contribuir, en español

El código fuente de la extensión no es público, así que aquí no hay pull requests
del código. Todo lo demás sí: los fallos que encuentre, las herramientas que echa
de menos, la documentación que se lee mal y las pruebas en un sistema que nadie
más tiene. Puede escribir en español en cualquier issue.

**Reportar un fallo.** Use la
[plantilla](https://github.com/Juan-Concepcion/tools4i-docs/issues/new/choose) y
rellénela entera: versión de Tools4i, de Code for IBM i, editor, SO y release
del IBM i, porque casi todo «a mí me funciona» sale de ahí. Cuente también qué
esperaba que pasara, no solo qué pasó, y los pasos desde que abrió la herramienta.
**Y sustituya los datos reales**: nombres inventados de bibliotecas, objetos,
miembros y usuarios, y recorte las capturas. Una issue la lee cualquiera.

**Proponer una idea.** La plantilla pide el problema antes que la solución a
propósito. Lo que hace que una idea suba en la lista es con qué frecuencia aparece
esa tarea, a cuánta gente afecta, y qué hace usted hoy en su lugar, sobre todo si
la respuesta es salir del editor.

**Corregir la documentación.** Los pull requests a este repositorio son
bienvenidos: erratas, enlaces rotos, párrafos confusos, pasos que faltan y mejoras
a la traducción. Con cuatro reglas: nada de datos reales, nada de detalles
internos de implementación, los dos README se mantienen a la par, y no se usa el
guion largo en ningún sitio. Un pull request, un asunto.

**Probar una compilación** antes de que se publique es lo más valioso que puede
hacer quien tenga un release, un juego de caracteres o una biblioteca muy distinta
a la del autor. Dígalo en una issue y se le indica el archivo.

**Qué esperar.** Esto lo mantiene una sola persona, así que una respuesta puede
tardar unos días. Los fallos reproducibles se arreglan en una versión posterior,
que se publica en los dos marketplaces y queda anotada en el
[CHANGELOG](CHANGELOG.md). Nada se cierra en silencio.

**Seguridad:** en privado, por correo a tools4i.support@gmail.com, nunca en una
issue pública. Vea [SECURITY.md](SECURITY.md).
