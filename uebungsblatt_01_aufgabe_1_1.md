# Übungsblatt 1 – Lösung

## Aufgabe 1.1 Sicherheitsziele identifizieren

### a)

**Patientendaten.Vertraulichkeit :**

- **Annahmen**
  - Die Patientendaten enthalten personenbezogene Informationen wie Namen, Geburtsdaten und Adressen sowie medizinische Diagnosen und Befunde.
  - Die Daten sind im vorliegenden Szenario auf einem zentralen Server gespeichert.
  - Der Zugriff ist grundsätzlich nur autorisierten Personen (Ärzten, Pflegekräften etc.) gestattet bzw. ermöglicht.
- **Bedrohung:** Ein Angreifer erlangt beispielsweise durch gestohlene Zugangsdaten oder das Ausnutzen einer Sicherheitslücke des Servers unberechtigt Zugriff auf die Daten und kann so die Patientendaten einsehen.
- **Begründung:** Dies stellt eine Bedrohung dar, da die medizinischen Informationen sowie die persönlichen Daten einzelne Personen eindeutig identifizieren können und Rückschlüsse auf deren Gesundheitszustand ermöglichen. Ein Angreifer hat somit die Möglichkeit, diese vertraulichen Informationen offenzulegen. Dadurch ist die Vertraulichkeit der Patientendaten verletzt.

**Trainingsdaten.Integrität :**

- **Annahmen**
  - Das KI-Modell wird mit einem Trainingsdatensatz aus CT-Aufnahmen und den zugehörigen Labels trainiert. Die Labels geben an, welcher Befund auf der Aufnahme zu erkennen ist, also beispielsweise ein Tumor, andere Erkrankungen oder kein Befund.
  - Schreibzugriff auf die Daten und die Labels ist möglich.
  - Die Zuordnung von Labels zu Aufnahmen wird vor dem Training des Modells nicht regelmäßig überprüft.
- **Bedrohung:** Ein Angreifer manipuliert die Trainingsdaten gezielt, indem er beispielsweise Labels fälscht oder anders zuordnet, wodurch positive Befunde fälschlicherweise als negativ, also gesund, gekennzeichnet werden.
- **Begründung:** Das KI-Modell kann dadurch falsche Zusammenhänge lernen und in der Anwendung keine zuverlässigen Prognosen bzw. Diagnosen liefern. Da die Trainingsdaten gezielt durch einen Angreifer verändert werden können und dadurch das Verhalten des KI-Modells beeinflusst werden kann, stellt dieses Szenario eine Bedrohung der Integrität des Trainingsdatensatzes dar.

**Modellergebnisse.Integrität :**

- **Annahmen**
  - Das KI-Modell wird nach dem Training im alltäglichen Betrieb in einem Krankenhaus eingesetzt, damit CT-Aufnahmen automatisch analysiert und Ärzte bei der Diagnose von Patienten unterstützt werden.
  - Die Modellergebnisse sowie die CT-Aufnahme werden digital gespeichert und dem Krankenhaus über einen zentralen Server zur Verfügung gestellt.
  - Ein Angreifer hat aufgrund einer Sicherheitslücke die Möglichkeit, auf die gespeicherten Ergebnisse des Modells zuzugreifen und diese zu verändern.
- **Bedrohung:** Der Angreifer ersetzt einen auffälligen Befund durch einen unauffälligen und verfälscht somit die Ergebnisse des Modells.
- **Begründung:** Die Ärzte würden falsche Informationen erhalten und falsche Entscheidungen in Bezug auf die Versorgung der Patienten treffen. Die Integrität der Modellergebnisse ist verletzt, da die ursprünglichen Ergebnisse des KI-Modells nachträglich manipuliert wurden und nicht gewährleistet wurde, dass die Daten nur von autorisierten Personen geändert/gelöscht werden dürfen.

### b)

**Trainingsdaten.Authentizität :**

- **Annahmen**
  - Das KI-Modell wird mit frei verfügbaren Datensätzen aus dem Internet trainiert.
  - Diese Datensätze werden von verschiedenen externen Anbietern veröffentlicht.
  - Die verwendeten Datensätze werden vom Unternehmen nicht zuverlässig auf ihre Herkunft geprüft.
- **Bedrohung:** Ein Angreifer imitiert eine grundsätzlich vertrauenswürdige Quelle und stellt dadurch gefälschte Datensätze zur Verfügung. Das Unternehmen geht fälschlicherweise davon aus, dass die Trainingsdaten aus einer vertrauenswürdigen Quelle stammen, und verwendet sie für das Training des KI-Modells.
- **Begründung:** Wenn die tatsächliche Herkunft der Daten nicht mit der angegebenen Herkunft übereinstimmt, kann die Echtheit nicht gewährleistet bzw. die Daten können nicht eindeutig zugeordnet werden. Damit wird das Sicherheitsziel der Authentizität verletzt.

**Verkehrsschilderkennung.Verfügbarkeit :**

- **Annahmen**
  - Das autonome Fahrzeug verwendet das KI-Modell bereits zur Verkehrsschilderkennung.
  - Das Modell läuft auf einem entsprechenden Rechner im Fahrzeug, der nur begrenzte Rechenkapazität besitzt.
  - Bei Überlastung kann das Erkennungssystem zeitweise nicht verwendet werden bzw. fällt vollständig aus.
- **Bedrohung:** Ein Angreifer greift auf bestimmte Prozesse des Fahrzeugrechners zu und überlastet dessen Rechenkapazität. Folglich werden Verkehrsschilder nicht mehr rechtzeitig erkannt oder das System fällt vollständig aus.
- **Begründung:** Die Erkennung der Verkehrsschilder ist ein essentieller Teil der Funktionsweise eines autonomen Fahrzeugs. Ein Ausfall dieses Systems stellt eine Gefahr für den Verkehr und die Sicherheit anderer Verkehrsteilnehmer dar. Weil die Verkehrsschilderkennung nicht mehr zur Nutzung zur Verfügung steht, ist das Sicherheitsziel der Verfügbarkeit verletzt.

**Kameradaten.Schutz der Privatsphäre :**

- **Annahmen**
  - Die öffentlich verfügbaren Trainingsdatensätze enthalten nicht nur reine Verkehrsschilder, sondern auch tatsächliche Verkehrs- und Straßenaufnahmen, auf denen zusätzlich Personen, Fahrzeuge und Kennzeichen zu erkennen sind. Personen sind anhand dieser Merkmale und Informationen eindeutig identifizierbar.
  - Das Unternehmen lädt diese Datensätze herunter und verwendet die vollständigen Aufnahmen für das Training seines KI-Modells, ohne sie vorher zu anonymisieren, obwohl die Erkennung der Merkmale von Fahrzeugen und Personen für die eigentliche Verkehrsschilderkennung nicht nötig ist.
  - Das Unternehmen speichert die heruntergeladenen Dateien auf eigenen Servern, wo sie auch nach dem Training noch zur Verfügung stehen.
  - Es besteht keine Zustimmung der Personen auf den Aufnahmen zur Verarbeitung ihrer Daten.
- **Bedrohung:** Das Unternehmen verwendet die Daten für andere Zwecke oder Mitarbeiter des Unternehmens greifen auf diese Informationen zu.
- **Begründung:** Das Unternehmen verarbeitet und speichert personenbezogene Daten, die für den eigentlichen Trainingszweck des Modells nicht benötigt werden. Der Schutz der Privatsphäre der betroffenen Personen ist dadurch gefährdet.

### c)

**Mitarbeiterfotos.Vertraulichkeit :**

- **Annahmen**
  - Das Unternehmen speichert die Gesichtsfotos seiner Mitarbeiter in einer zentralen Datenbank, verwendet sie für das Training des KI-Modells und löscht sie anschließend nicht wieder.
  - Die gespeicherten Bilder sind den einzelnen Mitarbeitern eindeutig zugeordnet, wodurch eine Identifizierung möglich ist.
  - Die Datenbank ist über die Systeme des Unternehmens erreichbar. Der Zugriff ist grundsätzlich nur autorisierten Personen gestattet.
- **Bedrohung:** Ein Angreifer erlangt über Sicherheitslücken oder gestohlene Zugangsdaten Zugriff auf die Datenbank. Die gestohlenen Fotos könnten für Identitätsfälschung verwendet werden.
- **Begründung:** Bei den Fotos handelt es sich um personenbezogene und vor allem biometrische Daten, wodurch diese sehr sensibel sind, da sie sich im Gegensatz zu beispielsweise Passwörtern und Zugangsdaten nicht ändern lassen. Durch die unberechtigte Offenlegung der biometrischen Daten wäre deren Vertraulichkeit verletzt.

**Gesichtserkennung.Authentizität :**

- **Annahmen**
  - Der Zutritt zu den Bürogebäuden des Unternehmens wird per Gesichtserkennung gesteuert.
  - Das Terminal an der Eingangstür ist für alle frei erreichbar.
  - Das KI-Modell wertet bei der Kontrolle nur ein einfaches Bild aus, ohne eine Lebenderkennung. Es kann daher nicht wirklich zwischen einer lebenden Person, einem Handy-Bild oder einem Ausdruck des Bildes unterscheiden.
- **Bedrohung:** Ein Angreifer verwendet ein Foto eines Mitarbeiters, beispielsweise aus den sozialen Medien, und verschafft sich damit Zugang zu den Gebäuden, da das Modell eine hohe Ähnlichkeit zwischen dem vorgehaltenen Bild und dem hinterlegten Bild erkennt.
- **Begründung:** Dies stellt eine hohe Bedrohung dar, weil der Angriff theoretisch ohne große technische Vorkenntnisse durchgeführt werden kann und die Schwäche im KI-System liegt, da das Modell nur auf Ähnlichkeit prüft. Dadurch ist die Authentizität des Systems verletzt, da die Echtheit der angenommenen Identität nicht gewährleistet wäre.

**Zugangskontrolle.Autorisierung :**

- **Annahmen**
  - Das Unternehmen verwendet das System zur Gesichtserkennung nicht nur an den Haupteingängen, sondern auch innerhalb des Gebäudes für unterschiedliche Bereiche.
  - Unterschiedliche Mitarbeiter haben unterschiedliche Zutrittsberechtigungen. Das System muss neben der reinen Gesichtserkennung auch die Zutrittsberechtigungen der einzelnen Personen überprüfen.
- **Bedrohung:** Ist das System falsch konfiguriert oder ändert sich die Konfiguration unvorhergesehen, könnte die Prüfung der Zugangsberechtigung nicht mehr durchgeführt werden und es würde nur geprüft, ob die erkannte Person grundsätzlich ein Mitarbeiter ist. Dadurch könnten unberechtigte Personen Zugang zu nicht für sie freigegebenen Bereichen erlangen.
- **Begründung:** Das KI-Modell hat zwar eine Person korrekt identifiziert, aber ihre Zugangsberechtigung nicht überprüft. Damit wäre das Sicherheitsziel der Autorisierung verletzt.

## Aufgabe 1.4

### a)

Das Ziel von Technikfolgenabschätzung besteht darin, systematisch zu untersuchen und zu bewerten, welche Auswirkungen Technologien sowohl auf Menschen als auch auf Gesellschaft, Wirtschaft und Umwelt haben. Dabei sollen sowohl Chancen als auch Risiken frühzeitig identifiziert werden und als Orientierung für Entscheidungsträger dienen. Ziel ist es, durch die Technikfolgenabschätzung mögliche Gefahren in Zusammenhang mit technischen Innovationen und Systemen zu minimieren und zudem eine Grundlage für eine verantwortungsvolle Verwendung neuer Technologien zu entwickeln. Dabei werden nicht nur unmittelbare Auswirkungen analysiert, sondern auch langfristige Folgen berücksichtigt. Es geht im Grunde also darum, dass man die möglichen Konsequenzen von neuen oder auch bestehenden Technologien versteht und analysiert, bevor sie unkontrolliert eingesetzt werden.
