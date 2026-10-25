# Übungsblatt 1 – Aufgabe 1.2
## Aufgabe 1.2

### a)

Mein Anwendungsfall ist meine IHK-Projektarbeit: ein MCP-Server (Model Context Protocol) für die Unreal Engine, über den ein KI-Agent eine 3D-Welt steuern kann. Der Agent läuft als NPC in der Welt und startet beim Start der 3D-Anwendung automatisch den MCP-Server `[prüfen]`. Der Server sucht in einer Schleife alle verfügbaren Blueprint-Funktionen der Welt, registriert sie als Tools und gibt sie an den Agenten weiter. Mitarbeiter, die die Welten als virtuelle Produktionsumgebung für Simulationen nutzen, schreiben oder sprechen mit dem Agenten. Der ruft über die interne LLM-API passende Tools auf und verändert so die Welt. Die Anwendungen werden über einen internen 3D-AppStore gestreamt und laufen in einer internen AWS-Cloud. Weil die Tools direkt aus den Blueprint-Funktionen entstehen, funktioniert das System in jeder Welt des AppStores ohne eigene Anbindung. Der KI-Anteil ist der Agent (Sprachmodell), der über den MCP-Server in die Unreal-Anwendung eingebettet ist.

### b)

**Blueprint-Funktionen (Tools).Autorisierung :**

- **Annahmen:** Alle Blueprint-Funktionen werden ohne Filter als Tools registriert. Der Agent darf sie für jeden Nutzer aufrufen, auch zerstörerische (z. B. Objekte löschen oder die Anwendung beenden), und fragt vorher nicht nach.
- **Bedrohung:** Ein Mitarbeiter bringt den Agenten dazu, Funktionen auszuführen, die für Nutzer nie gedacht waren.
- **Begründung:**  Hier kann  jeder, der mit dem Agenten spricht, indirekt alles auslösen. Rechte werden also nicht durchgesetzt.

**Tool-Beschreibungen.Integrität :**

- **Annahmen:** Funktionsnamen und -beschreibungen gehen automatisch an das Sprachmodell. Die Welten im AppStore kommen von verschiedenen Teams und werden vorher nicht auf Manipulation geprüft.
- **Bedrohung:** Ein Innentäter oder der Ersteller einer manipulierten Welt versteckt Anweisungen in einem Funktionsnamen oder einer Beschreibung. Der Agent führt sie aus, ohne dass Nutzer oder Betreiber es wollen.
- **Begründung:** Die Beschreibungen steuern das Verhalten des Agenten. Werden sie unberechtigt verändert, lenkt der Angreifer den Agenten indirekt, ohne selbst mit ihm zu sprechen. Da die Tools automatisch aus beliebigen Welten entstehen, ist die Angriffsfläche groß. Die Integrität ist verletzt.



**3D-Anwendung / MCP-Server.Verfügbarkeit :**

- **Annahmen:** Die Anwendung läuft als Stream auf begrenzten, ggf. geteilten AWS-Ressourcen. Es gibt kein Limit für Tool-Aufrufe.
- **Bedrohung:** Ein Nutzer oder ein manipulierter Agent löst viele aufwendige Aufrufe aus (z. B. massenhaft Objekte erzeugen, Endlosschleifen) oder ruft eine Funktion auf, die die Anwendung beendet.
- **Begründung:** Die Simulation wird langsam oder bricht ab, Mitarbeiter können nicht arbeiten, und es entstehen zusätzliche Cloud- und LLM-Kosten. Die Verfügbarkeit ist verletzt.
