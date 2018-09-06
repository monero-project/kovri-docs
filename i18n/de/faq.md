# Häufig gestellte Fragen

## Inhaltsverzeichnis
- Allgemeine Fragen
  - Was ist Kovri?
  - Wer entwickelt Kovri?
  - Wie wird Kovri Monero helfen?
  - Warum sollte ich mir Kovri anstelle von I2P holen?
  - Was bietet dir Kovri (nicht)?
  - Was ist der aktuelle Stand von Kovri?
  - Wann gibt es die Alpha-Version?
  - Worauf richtet das Entwicklerteam momentan sein Augenmerk?
  - Wie einsatzfähig sind Kovri und die Privatsphäre, die es bietet, zurzeit?
  - Wie kann ich die Kovri-Entwickler erreichen?
- Kovri vs i2pd
  - Warum sollte ich Kovri anstelle von i2pd verwenden?
  - Was sind die größten Unterschiede zwischen Kovri und i2pd?
  - Warum gab es den Fork von i2pd?
  - Was waren die Wendepunkte, die zum Forken von i2pd geführt haben (und warum gibt es zwei i2pd-Repositories: eines auf Bitbucket und eines auf GitHub)?
- Kovri benutzen
  - Ich habe eine Schwachstelle gefunden! Ich habe einen Bug gefunden! Was soll ich tun?
  - Warum zeigt mein Protokoll (log) ein anderes Datum/eine andere Uhrzeit als meine Zeitzone?

## Allgemeine Fragen

### Was ist Kovri?

[Kovri](https://getmonero.org/resources/moneropedia/kovri.html) ist eine freie, dezentrale Anonymitätstechnologie entwickelt von [Monero](https://getmonero.org).

Kovri basiert momentan auf den offenen Spezifikationen von [I2P](https://getmonero.org/resources/moneropedia/i2p.html) und nutzt sowohl [Garlic-Verschlüsselung](https://getmonero.org/resources/moneropedia/garlic-encryption.html) als auch [Garlic-Routing](https://getmonero.org/resources/moneropedia/garlic-routing.html), um ein privates, geschütztes Overlay-Netz über das Internet aufzubauen. Dieses Overlay-Netz ermöglicht es Benutzern, *wirksam* ihre geografische Lage und Internet-IP-Adresse zu verbergen.

Im Wesentlichen *ummantelt* Kovri den Internetverkehr einer Anwendung mit dem Ziel der Anonymität innerhalb des Netzwerks.

Als schlanker und sicherheitsorientierter Router ist Kovri vollständig mit dem I2P-Netzwerk kompatibel. Eine Alpha-Version von Kovri ist in Arbeit.

### Wer entwickelt Kovri?
Kovri ist ein Open-Source-Projekt, was heißt, dass es von Beiträgen der Community abhängt. Der Chefentwickler des Projekts ist [anonimal](https://github.com/anonimal), dem du über die Kovri-IRC-Channels [#kovri](irc://chat.freenode.net/#kovri), [#kovri-dev](irc://chat.freenode.net/#kovri-dev) und seinen [Twitter-Account](https://twitter.com/whoisanonimal) Fragen stellen kannst.

Kovri wird unter dem Dach des [Monero-Projekts](https://github.com/monero-project) entwickelt, ein weiteres Open-Source-Projekt, das den [Monero-Coin](https://getmonero.org) und [Open Alias](https://openalias.org) entwickelt. Die Beziehung zwischen dem Monero-Projekt und Kovri ist zum beiderseitigen Vorteil, dadurch dass einerseits Kovri ins Monero-Netzwerk integriert werden soll und andererseits Monero Kovris Entwicklung einen Zustrom an Entwicklern und Ressourcen verschafft.

### Wie wird Kovri Monero helfen?
Monero ist eine sichere, private, nicht nachverfolgbare und fungible Kryptowährung, die den Schutz der Privatsphäre voreingestellt hat und Technologien wie Tarnadressen (*Stealth Addresses*), RingCT und Ringsignaturen verwendet, um den Empfänger, die Summen und den Absender zu verbergen. Einige potentielle Schwachstellen Moneros bestehen im Leaken der IP-Adresse, die eine Transaktion sendet, und in Korrelationsangriffen.

Auftritt Kovri. Kovri wird in die offizielle Monero-Wallet implementiert, sodass alle Transaktionen über das anonyme Kovri-Netzwerk geroutet werden, wobei die IP-Adresse, von der die Transaktion ausging, ausgeblendet wird. In Zukunft werden alle Transaktionen standardmäßig über Kovri geroutet, wenngleich das Herunterladen der Blockchain aus Effizienzgründen immer noch über das Clearnet erfolgen wird.

### Warum sollte ich mir Kovri anstelle von I2P holen?
[I2P](https://geti2p.net) ist ein großartiges Projekt, aber es gab ein paar Dinge, die unserer Meinung nach kleinerer Änderungen bedurften, um die Technologie in Monero zu integrieren. Erstens, I2P wird in Java entwickelt, und wir dachten, dass die Entwicklung eines Routers in C++ dabei helfen würde, den Code schnell und schlank zu machen.

Zweitens, während die Java-Implementierung von I2P großartig ist, kommt sie mit einer Menge zusätzlicher Funktionen, die wir bei der Monero-Anwendung nicht für notwendig halten. Also haben wir uns entschieden, ganz von vorne anzufangen und einen Router zu erstellen, der NUR der Router ist. Dieser Minimalansatz ist perfekt für Monero und ist auch eine gute Nachricht für andere, die I2P-Anwendungen entwickeln wollen. Sie haben die Möglichkeit, einen schlanken Router ohne den aufgeblähten Überschuss zu nutzen, während andere Benutzer, die Verwendung für diese zusätzlichen Funktionen haben, die Java-Implementierung nutzen können. Es ist eine Win-win-Situation für alle.

### Was bietet Kovri jetzt schon?
- Ermöglicht dir, ein Knoten im I2P-Netzwerk zu werden
- Verbirgt deinen Standort vor den besuchten Websites
- Anonymisiert dich auf IRC und ermöglicht anonyme E-Mails
- Ermöglicht dir, anonyme Websites oder Dienste zu hosten
- Stellt Finanzierung für Entwickler, Hacker, Forscher via FFS und HackerOne bereit
- Strebt rigorose Codequalität und Entwicklungsstandards an

### Welche Entwicklungen hat Kovri für die Zukunft auf Lager?
- Überträgt Monero-Transaktionen über I2P
- GUI (Grafische Benutzeroberfläche) für verbesserte Konfigurierung und Benutzerfreundlichkeit
- Bibliotheks-API und -Bindungen für externe Apps/Bibliotheken
- Firefox-Erweiterung für einfachen Zugriff auf Eepsites
- Website-Entwicklung (getkovri.org / kovri.i2p)
- Umfangreiche Dokumentation von ELI5 bis Entwickler

### Was wird Kovri dir nicht bieten?
- Opferung deiner Sicherheit für irgendwelche Hintergedanken
- Bereitstellung einer komplizierten, unangenehmen Web-Benutzeroberfläche
- Notwendigkeit von Autoritäten für Netzwerk-Konsens
- Zugriff auf Internetseiten über einen Outproxy
- Notwendigkeit einer leistungsvernichtenden Java VM
- Ausführen deines Hundes oder Lieblingstieres, Zahlen deiner Steuern

### Was ist der aktuelle Stand von Kovri?
Kovri befindet sich in aktiver Entwicklung und ist derzeit in einem Alpha-Stadium. Es ist noch *nicht* in Monero integriert, aber neben einigen Kernfunktionen entwickeln wir eine [Client](https://github.com/monero-project/kovri/issues/351)- und eine [Core](https://github.com/monero-project/kovri/issues/350)-API, die Monero und andere Anwendungen nutzen können.

Aber nur weil wir in Alpha sind, bedeutet das nicht, dass man Kovri nicht nutzen kann. Derzeit kann man Kovri verwenden, um eine Verbindung mit dem I2P-Netzwerk herzustellen (und daran teilzunehmen), um auf Eepsites zu browsen, sich mit IRC zu verbinden sowie Client- und Server-Tunnel zu betreiben.

### Wann gibt es die Alpha-Version?
Eine Alpha-Version ist in Arbeit und wird (hoffentlich!!) vor Ende 2017 veröffentlicht. Sobald wir in der Alpha-Phase sind, beginnt sofort die Arbeit an der Beta-Version, die Folgendes erfordert: eine vollständig implementierte API, die Lösung wesentlicher Qualitätssicherungsprobleme und verschiedene Bugfixes.

### Worauf richtet das Entwicklerteam momentan sein Augenmerk?
Derzeit konzentrieren wir uns auf alles, was in unserem [Issue-Tracker](https://github.com/monero-project/kovri/issues/) aufgeführt ist. Das deckt einen Großteil dessen ab, was wir vor der offiziellen Alpha-Version fertigstellen müssen.

### Wie einsatzfähig sind Kovri und die Privatsphäre, die es bietet, zurzeit?
Kovri ist im Rahmen dessen, was `./kovri --help` zu bieten hat, verwendbar. Kovri hat gegenwärtig keine Interaktion mit Monero. Im Hinblick auf den Schutz der Privatsphäre haben wir seit der Einführung viele Sicherheitsprobleme behoben, aber wir möchten dich daran erinnern, dass wir uns noch immer in der Alpha-Phase befinden.

Es gibt immer noch viel Code zu schreiben, erwarte also keine starke Anonymitätsgarantie wie mit Tor oder selbst Java-I2P. Diese Projekte haben mehr als 10 Jahre Erfahrung in der Forschung und Implementierung, und wir fangen gerade erst an.

Du kannst gerne die Rolle des Entwicklers spielen und mit Kovri experimentieren, aber nur, wenn dich die Tatsache, dass du **nicht** anonym bist, nicht in Gefahr bringt, da immer das Risiko einer möglichen Deanonymisierung besteht, weil wir uns noch in Alpha befinden (das ist nicht Kovri-spezifisch).


### Wie kann ich die Kovri-Entwickler erreichen?
Siehe unser [README](https://github.com/monero-project/kovri/blob/master/README.md).

## Kovri vs. i2pd

### Warum sollte ich Kovri anstelle von i2pd verwenden?

- Sicherheit: Unser Fokus liegt auf der Sicherung unserer Software; nicht darauf, [überstürzt Dinge fertigzustellen](https://github.com/monero-project/kovri/issues/65), um einen Release zu haben.
- Qualität: Du unterstützt Bemühungen, eine qualitativ hochwertige Codebase, die langfristig Bestand hat, zu gewährleisten. Dies beinhaltet alle Aspekte der Wartbarkeit des Codes.
- Monero: Du unterstützt eine Kryptowährung, die sich mit der Wahrung der Privatsphäre und Anonymität rühmt und gleichzeitig deine Privatsphäre und Anonymität erhöht.

### Was sind die größten Unterschiede zwischen Kovri und i2pd?

- Wir stellen ein [Forum Funding System](https://forum.getmonero.org/8/funding-required) für Features/Entwicklung zur Verfügung.
- Wir konzentrieren uns auf die Erstellung eines I2P-Routers, der [„standardmäßig sicher“](http://www.openbsd.org/security.html) und einfach zu warten ist sowie gute Chancen hat, regelmäßig geprüft zu werden. Dies wird auf Kosten wenig genutzter Funktionen in den anderen Routern gehen, die Kernfunktionalität und eine API bleiben allerdings vollständig erhalten. Durch die Erstellung eines kleineren, effizienteren „Minimal“-Routers werden wir Entwicklern und Forschern mehr Zeit für Sicherheitsaudits und zum Hinterfragen des I2P-Designs und der Spezifikationen verschaffen.
- Wir konzentrieren uns auf die Implementierung einer intuitiven, entwicklerfreundlichen API, mit der sich jede Anwendung verbinden und das I2P-Netzwerk nutzen kann; dazu gehört auch Monero.
- Wir bieten sowohl Endbenutzern als auch Entwicklern eine [Qualitätssicherung](https://github.com/monero-project/kovri/issues/58) und ein [Entwicklungsmodell](https://github.com/monero-project/kovri-docs/blob/master/i18n/de/contributing.md), um bessere Software für jedermann bereitzustellen.
- Wir werden alternative Reseeding-Optionen implementieren, damit Benutzer [Pluggable Transports](https://www.torproject.org/docs/pluggable-transports.html.en) anstelle von HTTPS zum Reseeding verwenden können.
- Wir werden erweiterte Funktionen *(versteckter Modus + deaktiviertes Inbound)* implementieren, um Anonymität für diejenigen bereitszustellen, die in Ländern mit extremen Bedingungen leben oder sich hinter Firewalls mit Carrier-Grade-NAT oder DS-Lite befinden.
- Wir werden immer eine willkommene Umgebung für Zusammenarbeit schaffen.
- Wir werden immer auf dein Feedback hören und unser Bestes geben, um Kovri zu verbessern!

### Warum gab es den Fork von i2pd?

Wir haben aus mindestens mehreren Gründen geforkt:

- Wir wollten eine robuste, sichere und funktionsfähige C++-Implementierung des I2P-Netzwerks, und i2pd hat nicht geliefert
- Wir wollten eine positive Community, die Zusammenarbeit zur Verbesserung der Software fördert, nicht negativen, narzisstischen Ruhm
- Wir wollten einen Chefentwickler, der führen kann, nicht jemanden, der Anfragen nach verantwortungsvoller Offenlegung ignoriert oder vor Konflikten mit Mitarbeitern davonläuft

### Was waren die Wendepunkte, die zum Forken von i2pd geführt haben (und warum gibt es zwei i2pd-Repositories: eines auf Bitbucket und eines auf GitHub)?

*So begann das Drama von i2pd*.

Anfang/Mitte 2015 pushte einer der Entwickler mit Push-Rechten auf GitHub einen Commit, den der erste Autor von i2pd nicht mochte. Anstatt zusammenzuarbeiten, um das Problem zu lösen, nahm besagter Autor i2pd zu Bitbucket, löschte die **komplette** bestehende git-Historie und machte sich selbst zum alleinigen „Mitwirkenden“ der Software. Er schwor dann, niemals zu Irc2P zurückzukehren.

Diese Aktionen verärgerten viele in der I2P-Community, einschließlich der Entwickler, und beendeten beinahe das C++-Projekt.

Im Herbst 2015 kam dann anonimal, der nicht wollte, dass jedermanns Arbeit vergebens war und das Projekt durch eigene Beiträge und die Übernahme der Entwicklung wiederbelebte. Damals wurde eine offene Einladung an alle verbliebenen aktiven Entwickler ausgesprochen, sich zu treffen und i2pds Zukunft zu diskutieren. i2pds erster Autor zeigte sich nie, aber der Akt des Treffens brachte i2pds Federn offenbar derart zum Rascheln, dass er [zurückschlug](https://github.com/PurpleI2P/i2pd/issues/279) und begann wieder auf GitHub zu arbeiten - diesmal aber innerhalb eines ```openssl```-Branches (der sich als das Bitbucket-Repository herausstellte), anstelle des von der Community betriebenen ```master```-Branches.

Da die restlichen Entwickler erkannten, dass ein solch erratisches Verhalten nur dem I2P-Netzwerk und dem Projekt insgesamt schaden würde, ließen sie [mehrere wichtige Meetings](https://github.com/monero-project/kovri/issues/47) folgen und legten den Grundstein für das, was heute Kovri ist.

## Kovri benutzen

### Ich habe eine Schwachstelle gefunden! Ich habe einen Bug gefunden! Was soll ich tun?
- Schwachstellen: siehe unser [README](https://github.com/monero-project/kovri/blob/master/README.md)
- Bugs: siehe unser [Entwicklerhandbuch](https://github.com/monero-project/kovri-docs/blob/master/i18n/de/developer_guide.md)

### Warum zeigt mein Log ein anderes Datum/eine andere Uhrzeit als meine Zeitzone?
Logs werden in UTC aufgezeichnet, um deine Privatsphäre zu schützen. Durch die Verwendung von UTC kannst du Logs besser hochladen, um sie mit anderen Entwicklern oder der Community zu teilen, ohne deine Anonymität zu beeinträchtigen.
