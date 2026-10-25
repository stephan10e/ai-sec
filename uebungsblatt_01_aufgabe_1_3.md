# Übungsblatt 1 – Aufgabe 1.3

## Primärquellen

1. **OpenAI:** [OpenAI und Hugging Face reagieren gemeinsam auf Sicherheitsvorfall bei Modellevaluation](https://openai.com/de-DE/index/hugging-face-model-evaluation-security-incident/) – veröffentlicht am 21. Juli 2026, einschließlich des Updates vom 28. Juli 2026.
2. **Hugging Face:** [Security incident disclosure — July 2026](https://huggingface.co/blog/security-incident-july-2026) – veröffentlicht am 16. Juli 2026.
3. **Hugging Face, ergänzender technischer Bericht:** [Anatomy of a Frontier Lab Agent Intrusion](https://huggingface.co/blog/agent-intrusion-technical-timeline) – veröffentlicht am 27. Juli 2026.

Die erste Mitteilung von Hugging Face kannte die verwendeten Modelle noch nicht. Die spätere Zuordnung zu OpenAI und die konkretisierten Auswirkungen werden deshalb anhand der nachfolgenden Berichte berücksichtigt. Abruf der Quellen: 24. Oktober 2026.

### a) Was sollten die involvierten IT/KI-Systeme tun?

OpenAI wollte testen, wie gut seine KI Sicherheitslücken finden und ausnutzen kann. Das sollte in einer abgeschotteten Testumgebung passieren. Hugging Face stellt Modelle und Datensätze bereit und verarbeitet hochgeladene Daten.

### b) Was tat vor allem das KI-System tatsächlich?

Die KI verschaffte sich über eine Sicherheitslücke Internetzugang und drang in interne Systeme von Hugging Face ein. Laut den Berichten suchte sie dort nach fertigen Lösungen für den Test, statt die Aufgaben selbst zu lösen. Dabei stahl sie auch Zugangsdaten. 
### c) Wie autonom handelte das KI-System?

Menschen hatten das Testziel vorgegeben und bestimmte Schutzmechanismen für den Test ausgeschaltet. Die einzelnen Angriffsschritte führte die KI laut den Berichten selbstständig aus. Eine menschliche Anweisung, Hugging Face anzugreifen, ist darin nicht dokumentiert. 

### d) Auf welche Ressourcen konnte das System zugreifen?

Anfangs hatte die KI Rechenleistung und eine Testumgebung, deren Netzwerkzugang auf die Installation von Softwarepaketen beschränkt war. Durch den Angriff erlangte sie zusätzlich Internetzugang und Zugriff auf interne Server, Daten und Zugangsdaten von Hugging Face. 

### e) Welche Grenze wurde überschritten?

Die KI verließ die abgeschottete Testumgebung und griff auf fremde Systeme zu, für die sie keine Erlaubnis hatte. Damit wurde aus einem internen Test ein echter Angriff auf ein anderes Unternehmen. 

### f) Was daran erachte ich als besonders problematisch?

Ich finde besonders problematisch, dass die KI für ein vorgegebenes Testziel selbstständig fremde Systeme angriff. Die vorgesehene Abschottung konnte das nicht verhindern. Das zeigt für mich, dass man neben der Leistung auch prüfen muss, welche Wege eine KI zum Ziel nimmt. 

### g) Gab es einen realen Schaden?

Ja. Interne Systeme und Zugangsdaten wurden tatsächlich kompromittiert; es entstanden Aufwände für Untersuchung, Wiederaufbau und Austausch von Geheimnissen. Der technische Bericht nennt als abgerufene Kundeninhalte fünf Datensätze mit vermutetem Benchmark-Bezug. Andere Kundenmodelle, Datensätze, Spaces oder veröffentlichte Pakete waren demnach nicht betroffen. Eine Manipulation ausgelieferter Software wurde nicht festgestellt. Ein konkreter finanzieller Schaden wird nicht beziffert.
