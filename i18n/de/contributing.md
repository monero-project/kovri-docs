## Qualitätssicherung
- Sehen Sie sich unseren Leitfaden zur [Qualitätssicherung](https://github.com/monero-project/kovri-docs/blob/master/i18n/de/quality.md) an, um eine Vorstellung vom vorgeschlagenen Workflow zu bekommen.

## Compliance
- Wir streben die vollständige Einhaltung von C++11/14 an. Sie können dies gerne zu Ihrem Vorteil bei Ihrer Arbeit nutzen.
- Es wird außerdem nachdrücklich empfohlen, wenn möglich, die Standardbibliothek und die standardmäßigen Abhängigkeitsbibliotheken zu verwenden.

## Ihre Arbeit einreichen
Um Ihre Arbeit beizusteuern, gehen Sie bitte wie folgt vor:

1. Forken Sie Kovri
2. Lesen Sie unseren [Stilleitfaden](https://github.com/monero-project/kovri-docs/blob/master/i18n/de/style.md)
3. Erstellen Sie einen [themenspezifischen Branch](https://git-scm.com/book/de/v1/Git-Branching-Einfaches-Branching-und-Merging)
4. [**Signieren**](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work) Sie Ihre(n) Commit(s)
5. Schicken Sie einen Pull-Request an den Branch ```master```
   - Wir haben momentan keine Tags, da wir uns noch im Pre-Alpha-Stadium befinden. Sie können Ihre Arbeit fürs Erste auf dem master-Branch aufbauen.
   - Commit-Nachrichten sollten standardmäßig ausführlich sein und eine kurze Betreffzeile (höchstens 50 Zeichen), eine Leerzeile sowie einen detaillierten Erklärungstext mit getrennten Absätzen enthalten - es sei denn, der Titel alleine ist bereits selbsterklärend.
   - Commit-Titel sollten die Klasse oder den Aspekt des jeweiligen Projekts voranstellen. Zum Beispiel: „HTTPProxy: implement User-Agent scrubber. Fixes #193.“ oder „Garlic: fix uninitialized padding in ElGamalBlock“.
   - Wenn ein bestimmter Commit auf ein anderes Issue verweist, fügen Sie bitte eine Referenz hinzu. Zum Beispiel: „See #123“, oder „Fixes #123“. Das wird uns dabei helfen, Tickets aufzulösen, wenn wir in den ```master``` mergen.
   - Generell sollten Commits [atomar (*atomic*)](https://en.wikipedia.org/wiki/Atomic_commit#Atomic_commit_convention) und Diffs einfach zu lesen sein. Versuchen Sie daher bitte, keine Ausbesserungen der Formatierung mit Nicht-Formatierungs-Commits zu vermischen.
   - Der Hauptteil des Pull-Requests sollte eine genaue Beschreibung dessen enthalten, was der Patch macht, und (gegebenenfalls) eine Rechtfertigung/Begründung des Patches liefern. Sie sollten Verweise auf jegliche Diskussionen, wie etwa andere Tickets oder Chats auf IRC, beifügen.

## Vorschläge
Um einen Vorschlag einzubringen, sehen Sie bitte zunächst unsere [offenen Issues](https://github.com/monero-project/kovri/issues) nach bestehenden Vorschlägen durch. Falls das, was Sie vorschlagen, nicht enthalten ist, [öffnen Sie ein neues Issue](https://github.com/monero-project/kovri/issues/new).

Obwohl unser C4 vorschreibt, dass wir alles mergen, bitten wir darum, dass Sie aus den folgenden Gründen einen Vorschlag eröffnen:

1. Ein Vorschlag stößt Kommunikation an.
2. Ein Vorschlag zeigt, dass der Mitwirkende die Diskussionsbeiträge aller Projektmitarbeiter respektiert.
3. Ein Vorschlag ermöglicht, dass Mitarbeiter nahtlos ihre Diskussionsbeiträge in einem offenen Forum äußern können.
4. Ein Vorschlag spart Zeit, falls ein Mitarbeiter gerade an einem ähnlichen Feature/Problem arbeitet.
5. Ein Vorschlag verhindert Katastrophen und Missgeschicke bzw. erlaubt es den Mitarbeitern, sich auf Katastrophen und Missgeschicke vorzubereiten.

Einen Vorschlag *nicht* einzureichen, wird Sie *nicht* daran hindern, etwas beizutragen. Wir werden Ihre PRs mergen - ein Vorschlag wird dennoch nachdrücklich empfohlen.

## TODOs
- Führen Sie in der Codebase eine Schnellsuche nach ```TODO(unassigned):``` durch und/oder wählen Sie ein Ticket und beginnen Sie zu patchen!
- Falls Sie ein TODO erstellen, weisen Sie es sich selbst zu oder schreiben Sie es in ```TODO(unassigned):```

# [Verhaltenskodex (22/C4.1)](http://rfc.zeromq.org/spec:22)

## Lizenz

Copyright (c) 2009-2015 Pieter Hintjens.

Diese Spezifikation ist freie Software. Sie können sie weiter verbreiten und/oder verändern unter den Bedingungen der GNU General Public License, wie von der Free Software Foundation veröffentlicht; entweder Version 3 der Lizenz oder (nach Ihrer Wahl) jede neuere Version.

Diese Spezifikation wird in der Hoffnung verbreitet, dass sie von Nutzen ist, aber OHNE JEDE GEWÄHRLEISTUNG, sogar ohne stillschweigende Gewährleistung der MARKTGÄNGIGKEIT oder der VERWENDBARKEIT FÜR EINEN BESTIMMTEN ZWECK. Weitere Details finden Sie in der GNU General Public License.

Sie sollten zusammen mit diesem Programm eine Kopie der GNU General Public License erhalten haben; falls nicht, sehen Sie unter <http://www.gnu.org/licenses>.

## Sprache

Die Schlüsselwörter „MUSS/MÜSSEN“, „DARF NICHT/DÜRFEN NICHT“, „ERFORDERLICH“, „SOLL/SOLLEN“, „SOLL NICHT/SOLLEN NICHT“, „SOLLTE“, „SOLLTE NICHT/SOLLTEN NICHT“, „EMPFOHLEN“, „KANN/KÖNNEN“ und „OPTIONAL“ in diesem Dokument sind wie in RFC 2119 beschrieben zu interpretieren. [Eine Interpretation von RFC 2119 für Deutschsprachige findet sich [hier](https://github.com/adfinis-sygroup/2119/blob/master/2119de.rst).]

## Ziele

C4 ist dazu gedacht, ein wiederverwendbares optimales Modell der Zusammenarbeit für Open-Source-Softwareprojekte zur Verfügung zu stellen. Es hat diese konkreten Ziele:

- Die Größe und Vielfalt der Gemeinschaft im Umfeld eines Projekts zu maximieren, indem die Reibung für neue Mitwirkende verringert wird und ein skaliertes Beteiligungsmodell mit starken positiven Rückkopplungen (Feedbacks) erzeugt wird;
- Abhängigkeiten von Schlüsselfiguren zu reduzieren durch die Trennung unterschiedlicher Fähigkeiten, sodass es einen weiteren Kreis an kompetenten Mitwirkenden in jedem erforderlichen Bereich gibt;
- Eine schnellere und zielgerichtetere Entwicklung des Projekts zu erlauben, indem die Vielfalt des Entscheidungsprozesses erhöht wird;
- Den natürlichen Lebenszyklus von Projektversionen, von experimentell bis zu stabil, zu unterstützen, indem sicheres Experimentieren, schnelles Scheitern und die Isolation stabilen Codes ermöglicht wird;
- Die interne Komplexität von Projekt-Repositories zu reduzieren und es folglich einfacher für Mitwirkende zu machen, sich zu beteiligen, und Fehlerquellen zu minimieren;
- Gemeinschaftliches Eigentum am Projekt durchzusetzen, was die wirtschaftlichen Anreize der Mitwirkenden erhöht und das Risiko der Übernahme durch feindliche Einheiten reduziert.

## Design

### Einleitung

- Das Projekt SOLL das verteilte Revisionskontrollsystem git verwenden.
- Das Projekt SOLL auf github.com oder Vergleichbarem gehostet werden, nachstehend die „Plattform“ genannt.
- Das Projekt SOLL den Issue-Tracker der Plattform nutzen.
- Das Projekt SOLLTE klar dokumentierte Richtlinien zum Programmierstil haben.
- Ein „Mitwirkender“ ist eine Person, die einen Patch beitragen möchte, eine Reihe an Commits, die ein klar identifiziertes Problem lösen.
- Ein „Maintainer“ ist eine Person, die Patches in das Projekt mergt. Maintainer sind keine Entwickler; ihre Aufgabe ist es, den Prozess zu vollstrecken.
- Mitwirkende SOLLEN NICHT Commit-Zugriff zum Repository haben, es sei denn, sie sind auch Maintainer.
- Maintainer SOLLEN Commit-Zugriff zum Repository haben.
- Jeder, ohne Unterscheidung oder Diskriminierung, SOLL unter den Bedinungen dieses Vertrags ein gleiches Recht darauf haben, ein Mitwirkender zu werden.

### Lizensierung und Eigentum

- Das Projekt SOLL eine Share-Alike-Lizenz verwenden, wie etwa die GPLv3 oder eine Variante davon (LGPL, AGPL) oder die MPLv2.
- Alle Beiträge zum Quellcode des Projekts („Patches“) SOLLEN dieselbe Lizenz wie das Projekt verwenden.
- Alle Patches sind Eigentum der Autoren. Ein Urheberrechtsabtretungsprozess SOLL NICHT stattfinden.
- Die Urheberrechte im Projekt SOLLEN gemeinschaftliches Eigentum aller seiner Mitwirkenden sein.
- Jeder Mitwirkende SOLL verantwortlich dafür sein, sich selbst in der Mitwirkendenliste des Projekts auszuweisen.

### Patchanforderungen

- Maintainer und Mitwirkende MÜSSEN einen Plattform-Account haben und SOLLTEN ihre echten Namen oder einen bekannten Alias-Namen verwenden.
- Ein Patch SOLLTE eine minimale und präzise Antwort auf genau ein identifiziertes und vereinbartes Problem sein.
- Ein Patch MUSS die Projektrichtlinien bezüglich des Programmierstils einhalten, wenn diese festgelegt sind.
- Ein Patch MUSS die unten definierten Richtlinien zur „Entwicklung Öffentlicher Verträge“ einhalten.
- Ein Patch SOLL NICHT bedeutsamen Code anderer Projekte enthalten, es sei denn, der Mitwirkende ist der ursprüngliche Autor jenes Codes.
- Ein Patch MUSS sauber kompilieren und zumindest auf der Hauptzielplattform projektbezogene Selbsttests bestehen.
- Eine Patch-Commit-Nachricht SOLLTE aus einer einzelnen kurzen Zeile (weniger als 50 Zeichen) bestehen, welche die Änderung zusammenfasst, optional gefolgt von einer Leerzeile und anschließend einer genaueren Beschreibung.
- Ein „korrekter Patch“ ist einer, der die obigen Anforderungen erfüllt.

### Entwicklungsprozess

- Veränderungen am Projekt SOLLEN durch das Schema geregelt sein, Probleme genau zu identifizieren und minimale, genaue Lösungen dieser Probleme anzuwenden.
- Um Änderungen zu beantragen, SOLLTE ein Benutzer das Issue auf dem Issue-Tracker der Projektplattform protokollieren.
- Der Benutzer oder Mitwirkende SOLLTE das Issue schreiben, indem er das Problem beschreibt, dem er sich gegenübersieht bzw. das er beobachtet.
- Der Benutzer oder Mitwirkende SOLLTE Konsens hinsichtlich der Richtigkeit seiner Beobachtung und des Wertes der Lösung dieses Problems suchen.
- Benutzer SOLLEN NICHT Feature-Requests, Ideen, Vorschläge oder Problemlösungen, die nicht explizit dokumentiert und nachweisbar sind, protokollieren.
- Die Versionsgeschichte des Projekts SOLL demnach eine Liste aussagekräftiger Issues sein, die protokolliert und gelöst werden.
- Um an einem Issue zu arbeiten, SOLL ein Mitwirkender das Projekt-Repository forken und danach an seinem geforkten Repository arbeiten.
- Um einen Patch einzureichen, SOLL ein Mitwirkender auf der Plattform einen Pull-Request zurück zum Projekt erstellen.
- Ein Mitwirkender SOLL NICHT Änderungen direkt zum Projekt committen.
- Falls die Plattform Pull-Requests als Issues einsetzt, KANN ein Mitwirkender direkt einen Pull-Request senden, ohne ein separates Issue zu protokollieren.
- Um einen Patch zu diskutieren, KANN auf der Plattform auf dem Pull-Request, dem Commit oder anderswo kommentiert werden.
- Um einen Patch zu akzeptieren oder abzulehnen, SOLL ein Maintainer die Oberfläche der Plattform verwenden.
- Maintainer SOLLTEN NICHT ihre eigenen Patches mergen, außer in außergewöhnlichen Fällen, etwa ausbleibender Antworten von anderen Maintainern über einen längeren Zeitraum (mehr als 1-2 Tage). 
- Maintainer SOLLEN NICHT Werturteile über korrekte Patches abgeben.
- Maintainer SOLLEN korrekte Patches anderer Mitwirkender rasch mergen.
- Der Mitwirkende KANN ein Issue als „Ready“ („Fertig“) taggen, nachdem er einen Pull-Request für dieses Issue durchgeführt hat.
- Der Benutzer, der ein Issue erstellt hat, SOLLTE das Issue schließen, nachdem er überprüft hat, dass der Patch erfolgreich ist.
- Maintainer SOLLTEN um Verbesserungen für fehlerhafte Patches bitten und SOLLTEN fehlerhafte Patches ablehnen, wenn der Mitwirkende nicht konstruktiv antwortet.
- Jeder Mitwirkende, der Werturteile über einen korrekten Patch hat, SOLLTE diese mittels eigener Patches ausdrücken.
- Maintainer KÖNNEN Änderungen an der Dokumentation, die nicht den Quellcode betreffen, direkt zum Projekt committen.

### Erzeugung stabiler Versionen

- Das Projekt SOLL einen Branch („master“) haben, der immer die aktuelle in Arbeit befindliche Version enthält und immer Build-Status haben SOLLTE.
- Das Projekt SOLL NICHT themenspezifische Branches aus welchem Grund auch immer nutzen. Persönliche Forks KÖNNEN themenspezifische Branches nutzen.
- Um eine stabile Version zu erstellen, SOLL jemand das Repository forken, indem er es kopiert und dadurch Maintainer dieses Repositorys wird.
- Ein Projekt KANN aus Stabilitätsgründen einseitig und ohne Zustimmung der Projekt-Maintainer geforkt werden.
- Ein Stabilitätsprojekt SOLLTE durch denselben Prozess wie das Hauptprojekt unterhalten werden.
- Ein Patch eines Stabilitätsprojekts, der als „stabil“ („*stable*“) bezeichnet wird, SOLL mit einem reproduzierbaren Testfall einhergehen.

### Entwicklung Öffentlicher Verträge

- Alle Öffentlichen Verträge (APIs oder Protokolle) SOLLEN dokumentiert werden.
- Alle Öffentlichen Verträge SOLLTEN Raum für Erweiterungen und Experimente haben.
- Ein Patch, der einen stabilen Öffentlichen Vertrag ändert, SOLLTE keine bestehenden Anwendungen zerstören, es sei denn, es besteht ein vorrangiger Konsens über den Wert einer solchen Aktion.
- Ein Patch, der neue Funktionen in einen Öffentlichen Vertrag einbringt, SOLLTE dafür neue Bezeichnungen verwenden.
- Alte Bezeichnungen SOLLTEN systematisch überholt werden, indem neue Bezeichnungen als „*experimental*“ („experimentell“) gekennzeichnet werden, bis sie stabil sind, woraufhin die alten Bezeichnungen als „*deprecated*“ („überholt“) deklariert werden.
- Sobald ausreichend Zeit vergangen ist, SOLLTEN alte überholte Bezeichnungen als „*legacy*“ („veraltet“) markiert und schließlich entfernt werden.
- Alte Bezeichnungen SOLLEN NICHT von neuen Funktionen wiederverwendet werden.
- Sobald alte Bezeichnungen entfernt werden, MÜSSEN ihre Implementierungen eine Exception (Assertion) auslösen, falls sie von Anwendungen genutzt werden.

### Projektverwaltung

- Die Projektgründer SOLLEN als Administratoren fungieren, um die Gruppe an Projektmaintainern zu leiten.
- Die Administratoren SOLLEN im Laufe der Zeit ihre eigene Nachfolge sicherstellen, indem sie die effektivsten Maintainer befördern.
- Ein neuer Mitwirkender, der einen korrekten Patch macht, SOLL eingeladen werden, ein Maintainer zu werden.
- Administratoren KÖNNEN Maintainer abberufen, die über einen längeren Zeitraum inaktiv sind oder es wiederholt versäumen, diesen Prozess sorgfältig anzuwenden.
- Administratoren SOLLTEN „schlechte Akteure“, die bei anderen Projektmitwirkenden Stress und Schmerzen verursachen, blockieren oder sperren. Dies sollte nach einer öffentlichen Diskussion vollzogen werden, in der allen Parteien die Möglichkeit eingeräumt wird, sich zu äußern. Ein schlechter Akteur ist jemand, der wiederholt die Regeln und die Kultur des Projekts ignoriert, der unnötig streitlustig oder feindselig ist oder beleidigend agiert und der nicht in der Lage ist, sein Verhalten selbst zu korrigieren, wenn er von anderen darum gebeten wird.

# Governanceprozess

![Governanceprozess](https://getmonero.org/blog/assets/2015-year-in-review/governance-process.jpg)
