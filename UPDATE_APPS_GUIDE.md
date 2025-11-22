# 🔗 Privacy Policy URLs in Apps integrieren

Nach dem Upload auf GitHub Pages musst du die Privacy Policy URLs in beiden Apps hinzufügen, damit Nutzer darauf zugreifen können.

---

## 📱 MyClinic Android - URL hinzufügen

### Schritt 1: Privacy Policy Screen aktualisieren

**Datei:** `MyClinic Android Flutter/lib/screens/privacy_policy_screen.dart`

Füge am Ende des Privacy Policy Screens einen "Online ansehen" Button hinzu:

```dart
// Füge nach Zeile 170 (am Ende des ListView) ein:

const SizedBox(height: 24),

// Online Privacy Policy Button
Container(
  width: double.infinity,
  padding: const EdgeInsets.all(20),
  decoration: BoxDecoration(
    gradient: LinearGradient(
      colors: [
        AppColors.primaryBlue.withOpacity(0.1),
        AppColors.primaryBlue.withOpacity(0.05),
      ],
    ),
    borderRadius: BorderRadius.circular(15),
    border: Border.all(
      color: AppColors.primaryBlue.withOpacity(0.3),
      width: 1,
    ),
  ),
  child: Column(
    children: [
      Icon(
        Icons.open_in_browser,
        size: 48,
        color: AppColors.primaryBlue,
      ),
      const SizedBox(height: 12),
      const Text(
        'Version Complète en Ligne',
        style: TextStyle(
          fontSize: 18,
          fontWeight: FontWeight.bold,
          color: AppColors.textPrimary,
        ),
      ),
      const SizedBox(height: 8),
      Text(
        'Consultez la version complète de notre politique de confidentialité sur notre site web',
        textAlign: TextAlign.center,
        style: TextStyle(
          fontSize: 14,
          color: Colors.grey.shade700,
        ),
      ),
      const SizedBox(height: 16),
      ElevatedButton.icon(
        onPressed: () async {
          const url = 'https://VOTRE-USERNAME.github.io/privacy-policies/myclinic-privacy.html';
          final uri = Uri.parse(url);
          if (await canLaunchUrl(uri)) {
            await launchUrl(uri, mode: LaunchMode.externalApplication);
          } else {
            ScaffoldMessenger.of(context).showSnackBar(
              const SnackBar(
                content: Text('Impossible d\'ouvrir le lien'),
                backgroundColor: Colors.red,
              ),
            );
          }
        },
        icon: const Icon(Icons.arrow_forward),
        label: const Text('Ouvrir dans le Navigateur'),
        style: ElevatedButton.styleFrom(
          backgroundColor: AppColors.primaryBlue,
          foregroundColor: Colors.white,
          padding: const EdgeInsets.symmetric(horizontal: 24, vertical: 12),
        ),
      ),
    ],
  ),
),
```

### Schritt 2: Import hinzufügen

Füge am Anfang der Datei (Zeile 1-3) hinzu:

```dart
import 'package:url_launcher/url_launcher.dart';
```

### Schritt 3: URL ersetzen

⚠️ **WICHTIG:** Ersetze `VOTRE-USERNAME` mit deinem echten GitHub Username!

```dart
const url = 'https://VOTRE-USERNAME.github.io/privacy-policies/myclinic-privacy.html';
```

**Beispiel:** Wenn dein GitHub Username `ahmeddoctor` ist:
```dart
const url = 'https://ahmeddoctor.github.io/privacy-policies/myclinic-privacy.html';
```

---

## 💚 SihaPlus Android - URL hinzufügen

### Schritt 1: Privacy Policy Screen aktualisieren

**Datei:** `Siha Plus Android Flutter/sihaplus_flutter/lib/screens/privacy_policy_screen.dart`

Füge am Ende des Privacy Policy Screens einen "Online ansehen" Button hinzu:

```dart
// Füge nach Zeile 189 (am Ende des ListView) ein:

const SizedBox(height: 24),

// Online Privacy Policy Button
Container(
  width: double.infinity,
  padding: const EdgeInsets.all(20),
  decoration: BoxDecoration(
    gradient: LinearGradient(
      colors: [
        AppColors.primaryBlue.withOpacity(0.1),
        AppColors.primaryBlue.withOpacity(0.05),
      ],
    ),
    borderRadius: BorderRadius.circular(15),
    border: Border.all(
      color: AppColors.primaryBlue.withOpacity(0.3),
      width: 1,
    ),
  ),
  child: Column(
    children: [
      Icon(
        Icons.open_in_browser,
        size: 48,
        color: AppColors.primaryBlue,
      ),
      const SizedBox(height: 12),
      const Text(
        'Version Complète en Ligne',
        style: TextStyle(
          fontSize: 18,
          fontWeight: FontWeight.bold,
          color: AppColors.textPrimary,
        ),
      ),
      const SizedBox(height: 8),
      Text(
        'Consultez la version complète et détaillée de notre politique de confidentialité',
        textAlign: TextAlign.center,
        style: TextStyle(
          fontSize: 14,
          color: Colors.grey.shade700,
        ),
      ),
      const SizedBox(height: 16),
      ElevatedButton.icon(
        onPressed: () async {
          const url = 'https://VOTRE-USERNAME.github.io/privacy-policies/sihaplus-privacy.html';
          final uri = Uri.parse(url);
          if (await canLaunchUrl(uri)) {
            await launchUrl(uri, mode: LaunchMode.externalApplication);
          } else {
            ScaffoldMessenger.of(context).showSnackBar(
              const SnackBar(
                content: Text('Impossible d\'ouvrir le lien'),
                backgroundColor: Colors.red,
              ),
            );
          }
        },
        icon: const Icon(Icons.arrow_forward),
        label: const Text('Ouvrir dans le Navigateur'),
        style: ElevatedButton.styleFrom(
          backgroundColor: AppColors.primaryBlue,
          foregroundColor: Colors.white,
          padding: const EdgeInsets.symmetric(horizontal: 24, vertical: 12),
        ),
      ),
    ],
  ),
),
```

### Schritt 2: Import hinzufügen

Füge am Anfang der Datei (Zeile 1-3) hinzu:

```dart
import 'package:url_launcher/url_launcher.dart';
```

### Schritt 3: URL ersetzen

⚠️ **WICHTIG:** Ersetze `VOTRE-USERNAME` mit deinem echten GitHub Username!

```dart
const url = 'https://VOTRE-USERNAME.github.io/privacy-policies/sihaplus-privacy.html';
```

---

## ✅ Testen

Nach den Änderungen:

1. **Flutter hot reload** oder App neu starten
2. Navigiere zu Einstellungen → Datenschutz
3. Scrolle nach unten
4. Klicke auf "Ouvrir dans le Navigateur"
5. Der Browser sollte sich öffnen und die Privacy Policy anzeigen

---

## 🔄 Alternative: Als Konstante speichern

Für bessere Code-Organisation kannst du die URLs in einer Konstanten-Datei speichern:

### Neue Datei erstellen: `lib/utils/constants.dart`

```dart
class AppConstants {
  // Privacy Policy URLs
  static const String privacyPolicyUrl = 'https://VOTRE-USERNAME.github.io/privacy-policies/myclinic-privacy.html'; // oder sihaplus-privacy.html

  // Andere Konstanten
  static const String termsOfServiceUrl = '...';
  static const String supportEmail = 'support@yourcompany.dz';
}
```

### Dann in privacy_policy_screen.dart:

```dart
import '../utils/constants.dart';

// ...

onPressed: () async {
  final uri = Uri.parse(AppConstants.privacyPolicyUrl);
  if (await canLaunchUrl(uri)) {
    await launchUrl(uri, mode: LaunchMode.externalApplication);
  }
}
```

---

## 📋 Checklist

**MyClinic:**
- [ ] `url_launcher` Import hinzugefügt
- [ ] Button-Code eingefügt
- [ ] GitHub Pages URL eingetragen
- [ ] Getestet (Button funktioniert, öffnet Browser)

**SihaPlus:**
- [ ] `url_launcher` Import hinzugefügt
- [ ] Button-Code eingefügt
- [ ] GitHub Pages URL eingetragen
- [ ] Getestet (Button funktioniert, öffnet Browser)

---

## ⚠️ Häufige Fehler

### Fehler: "Could not launch URL"

**Ursache:** `url_launcher` Package fehlt oder URL ist falsch

**Lösung:**
```bash
flutter pub add url_launcher
flutter pub get
```

Und stelle sicher, dass die URL korrekt ist (mit `https://`).

### Fehler: Import kann nicht gefunden werden

**Ursache:** Package nicht in `pubspec.yaml`

**Lösung:**
Überprüfe `pubspec.yaml` - `url_launcher` sollte bei beiden Apps bereits vorhanden sein:
- MyClinic: `url_launcher: ^6.2.4` (Zeile 32)
- SihaPlus: `url_launcher: ^6.2.2` (Zeile 61)

Falls nicht:
```yaml
dependencies:
  url_launcher: ^6.2.4
```

### Fehler: Button wird nicht angezeigt

**Ursache:** Code an falscher Stelle eingefügt

**Lösung:**
- Stelle sicher, dass der Code innerhalb des `ListView` (children: [...]) ist
- Nicht innerhalb eines anderen Widgets
- Am besten vor dem letzten `SizedBox` oder `_buildAcceptanceCard()`

---

## 🎯 Zusätzliche Verbesserungen (Optional)

### In-App WebView statt Browser:

Falls du die Privacy Policy in der App selbst anzeigen möchtest:

1. Package hinzufügen:
   ```bash
   flutter pub add webview_flutter
   ```

2. Neue Screen erstellen: `web_view_screen.dart`

3. Launch Mode ändern:
   ```dart
   await launchUrl(uri, mode: LaunchMode.inAppWebView);
   ```

### Deep Link zur Privacy Policy:

Füge einen Deep Link hinzu, damit Google Play direkt zur Privacy Policy navigieren kann:

**AndroidManifest.xml:**
```xml
<intent-filter>
    <action android:name="android.intent.action.VIEW" />
    <category android:name="android.intent.category.DEFAULT" />
    <category android:name="android.intent.category.BROWSABLE" />
    <data
        android:scheme="https"
        android:host="VOTRE-USERNAME.github.io"
        android:pathPrefix="/privacy-policies/myclinic-privacy.html" />
</intent-filter>
```

---

**Fertig!** Die Privacy Policy URLs sind jetzt in beiden Apps integriert und Nutzer können die vollständige Version im Browser öffnen.
