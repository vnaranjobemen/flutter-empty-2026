# flutter-empty-2026

Plantilla de flux de treball per recrear una estructura neta de projecte Flutter només amb:

- Plataforma Web
- Plataforma Android

Aquest README està pensat perquè puguis reiniciar el repositori a un estat mínim i regenerar els fitxers de plataforma necessaris de manera reproduïble.

Aquest document s'ha fet amb l'ajuda de Copilot

## 1) Prerequisits

- Flutter SDK instal·lat i disponible al PATH
- Comprova la instal·lació de Flutter:

```bash
flutter doctor
```

## 2) Comença des d’un estat net del repositori

Si vols descartar els canvis locals i tornar a l’últim estat confirmat al repositori:

```bash
git reset --hard
git clean -fd
```

## 3) Genera només l’estructura de plataforma Web + Android

Des de l’arrel del projecte:

```bash
flutter create --platforms=web,android .
```

Què fa aquesta comanda:

- Regenera els fitxers d’esquelet de Flutter que faltin
- Crea/actualitza les carpetes de plataforma `web/` i `android/`
- Manté el codi Dart existent de l’app sempre que sigui possible

Opcions disponibles per `--platforms`:

- `android`
- `ios`
- `web`
- `windows`
- `macos`
- `linux`

Exemple amb totes les plataformes:

```bash
flutter create --platforms=android,ios,web,windows,macos,linux .
```

Pots combinar només les que necessitis, separades per comes.

## 4) Comandes de compilació

Compila només l’app web:

```bash
flutter build web
```

Compila l’APK d’Android:

```bash
flutter build apk
```

Android App Bundle opcional (Play Store):

```bash
flutter build appbundle
```

## 5) Comandes d’execució (opcional)

Executa al navegador:

```bash
flutter run -d chrome
```

Executa en dispositiu/emulador Android:

```bash
flutter run -d android
```

## 6) Comportament esperat de Git

- Hauries de veure fitxers de codi/configuració dins de `web/` i `android/` versionats a Git.
- No hauries de pujar sortides de compilació generades dins de `build/`.
- No hauries de pujar fitxers locals d’IDE (`.idea/`, `.vscode/`, `*.iml`).

Si cal, mantén aquestes regles a `.gitignore`:

```gitignore
build/
.idea/
.vscode/
*.iml
```

Nota:

- No ignoris tota la carpeta `web/` si web és una plataforma suportada.
- No ignoris tota la carpeta `android/` si Android és una plataforma suportada.

## 7) Checklist ràpid de verificació

Després de regenerar, comprova:

```bash
flutter analyze
flutter test
flutter build web
flutter build apk
```

Si totes les comandes passen, el teu flux de plantilla neta és correcte.
