# Qualitätssicherung

Das Folgende ist ein Modellvorschlag für den QS-Arbeitsablauf. Obwohl der Ablauf grundsätzlich linear ist, kann jede Phase, falls nötig, einzeln bearbeitet werden - solange letztendlich alle Phasen behandelt werden.

## Phase 1: Grundlegende Überprüfung

- Sehen Sie sich die offenen Probleme über unseren [Issue-Tracker](https://github.com/monero-project/kovri/issues/) an
- Lesen Sie unseren [Vulnerability Response Process](https://github.com/anonimal/meta/blob/master/VULNERABILITY_RESPONSE_PROCESS.md)
- Der gesamte Code muss unseren Beitragsrichtlinien entsprechen
- Notieren Sie Bereiche, die Verbesserung bedürfen (gedanklich oder im Code)
- Erstellen Sie To-dos und weisen Sie sie, wenn möglich, zu

## Phase 2: Spezifikationsüberprüfung / Implementierung / Code-Dokumentation

- Komplette Spezifikationsüberprüfung pro Modul, z.B.: Streaming, I2PControl, etc.
  - Der Code muss mit den wesentlichen Teilen der Spezifikation übereinstimmen, die dasselbe (oder ein besseres) Anonymitätsniveau wahren, wie es Java-I2P bietet
  - Refaktorieren/implementieren/patchen Sie, wann/wo nötig
- Stellen Sie eine C++11/14-konforme Implementierung sicher
  - Gehen Sie bei Bedarf Phase 2 nochmals durch
- Erledigen Sie alle zugehörigen To-dos
- Dokumentieren Sie Code so ausführlich wie möglich mit Inline-Kommentaren und Doxygen
  - Code sollte sowohl von Anfängern als auch erfahrenen Programmieren zu verstehen sein
  - Code sollte den Leser zu einem besseren Verständnis von I2P führen
    - I2P ist sehr komplex, daher sollte unser Code als eigenständiger Ersatz der Spezifikationsdokumentation fungieren und nicht nur als eine Ergänzung (dies kann ein mühsames Ziel sein, ist aber sehr lohnend in Bezug auf Wartung und Software-Lebensdauer)

## Phase 3: Überprüfung der Kryptographie / Sicherheitsaudit

- Stellen Sie sicher, dass die Kryptographie auf dem neuesten Stand und korrekt implementiert ist
- Ermitteln Sie jeden Vektor für bekannte Exploits
  - Beachten Sie diese Vektoren beim Schreiben von Tests
- Attackieren Sie Kovri auf jede mögliche Weise
  - Beheben Sie das, was Sie kaputt gemacht haben
- Verwenden Sie, wenn möglich, immer vertrauenswürdige, gut geschriebene Bibliotheken
  - Vermeiden Sie Code der Sorte: *homebrewed*, ad-hoc, *Ich bin mir sicher, dass ich es besser als die Community weiß*
- Holen Sie sich eine zweite (oder mehr) Meinung(en) von Kollegen ein, bevor Sie mit der nächsten Phase fortfahren

## Phase 4: Beseitigung von Bugs / Tests / Profiling

- Resolve priority bugs/issues
- Schreiben Sie Unittests für jedes Modul
  - Führen Sie Tests durch. Führen Sie sie nochmals durch
  - Vollständige Überprüfung der Testergebnisse. Patchen, wenn nötig. Refaktorieren nach Bedarf
- Stellen Sie sicher, dass die Automatisierung regelmäßig läuft
  - valgrind, doxygen, clang-format
  - Patchen, wenn nötig. Refaktorieren nach Bedarf

## Phase 5: Rücksprache

- Halten Sie Rücksprache mit Kollegen und der Community
  - Die Diskussionen sollten öffentlich über Tickets, Meetings und/oder IRC erfolgen.
- Akzeptieren Sie alle Rückmeldungen und produzieren Sie als Antwort greifbare Ergebnisse
- Wenn Sie zufrieden sind, gehen Sie zur nächsten Phase über, andernfalls wiederholen Sie diese Phase (oder beginnen Sie von einer vorherigen Phase aus)

## Phase 6: Wiederholen Sie den Zyklus von Anfang an
