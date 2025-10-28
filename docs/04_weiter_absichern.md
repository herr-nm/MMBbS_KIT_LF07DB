# Kapitel 4: Netzwerk in einer Büroumgebung weiter absichern

![Kapitelbild](bilder/04_kapitelbild.png)

In diesem Kapitel werden Sie ...

- ... Methoden zur Absicherung des Netzwerks vergleichen,
- ... sich über Network Access Control mit MAC-Filter informieren,
- ... einen MAC-Filter auf einem Switch realisieren.

## Handlungssituation

Der Einbau der wichtigsten Komponenten beim Kunden ist durch die ChangeIT GmbH erfolgt. Im Rahmen des Installationsprozesses und der kontinuierlichen Abstimmung mit dem Kunden haben sich noch einige neue Hinweise ergeben, die ebenfalls berücksichtigt werden müssen.

Einige Kabel verlassen die Gebäudehülle bzw. einige Netzwerkdosen werden im Wartebereich des Steuerberaters genutzt. Diese sind bisher für Angriffe quasi ungeschützt, da die Verbindungen direkt in die entsprechenden Netze führen. 

## Kompetenz 4.0: Erweiterung der Sicherheit um Network Access Control prüfen

Im Gespräch mit dem Kunden nach der Ersteinrichtung der Komponenten sollen die konkreten Anforderungen hinsichtlich der Sicherheit im Konzept ergänzt werden:

- Verhinderung der Fehlnutzung von Netwerkkabeln und Dosen in exponierten Bereichen
- ggf. Einführung eines Systems zur Erkennung von Angriffen im Netzwerk

### A|4.0: Recherche zu Intrusion-Detection-/Prevention-Systemen

Informieren Sie sich im Informationsmaterial M|4.0: HERDT-AYCR Intrusion-Detection-/Prevention-Systeme über die verschiedenen Optionen zur Erkennung und Prävention von Angriffen auf ein Netzwerk. Stellen Sie Ihre Erkenntnisse in einer Infografik (bspw. mit M|4.1: Tool-Tipp - Canva) zusammen.

### M|4.0: HERDT-AYCR Intrusion-Detection-/Prevention-Systeme

Direktlink zum Material: https://herdt-campus.com/product/NWSI_2024

Sie können das Skript über mm-bbs.de und die Blase "HERDT AYCR" aufrufen. Dort einfach im Katalog oder über die Suche nach Netzwerke Sicherheit (2024) suchen.

![HERDT AYCR Netzwerke Sicherheit](bilder/04_HERDT_Netzwerke_Sicherheit.png)

### M|4.1: Tool-Tipp - Canva

https://www.canva.com/de_de/

### A|4.1: Recherche zu Network Access Control

Informieren Sie sich im Informationsmaterial M|4.2: Network Access Control (NAC) über das Themengebiet der Network Access Control. Stellen Sie Ihre Erkenntnisse in einer Infografik (bspw. mit M|4.1: Tool-Tipp - Canva) zusammen.

### M|4.2: Network Access Control (NAC)

Network Access Control (NAC) ist ein entscheidendes Konzept in der IT-Sicherheit, das Organisationen ermöglicht, den Zugriff auf Netzwerke zu kontrollieren und zu überwachen. Mit der zunehmenden Vernetzung von Geräten und der wachsenden Bedrohung durch Cyberangriffe ist NAC zu einer unverzichtbaren Komponente für die Sicherung von IT-Infrastrukturen geworden. Dieser Text beleuchtet die verschiedenen Aspekte von NAC, darunter seine Funktionsweise, die verschiedenen Implementierungsmethoden, Herausforderungen sowie spezifische Techniken wie MAC-Filter, die eine zentrale Rolle im NAC spielen.

#### Einführung in Network Access Control

NAC umfasst eine Reihe von Technologien und Prozessen, die dafür sorgen, dass nur autorisierte Geräte und Benutzer auf ein Netzwerk zugreifen können. Der Hauptzweck von NAC besteht darin, den Zugang zu Netzwerken auf der Grundlage von Sicherheitsrichtlinien zu steuern, die vom Netzwerkadministrator definiert wurden. Diese Richtlinien können auf einer Vielzahl von Faktoren basieren, einschließlich der Identität des Benutzers, der Art des Geräts, des Standorts und der Sicherheitslage des Geräts.

Ein typisches NAC-System überprüft zunächst die Identität eines Benutzers oder Geräts, bevor es den Zugriff auf das Netzwerk gewährt. Wenn die Identität erfolgreich verifiziert wird und das Gerät alle festgelegten Sicherheitsanforderungen erfüllt, wird der Zugriff gestattet. Andernfalls wird der Zugriff verweigert oder das Gerät in ein Quarantäne-Netzwerk verschoben, wo es nur eingeschränkten Zugriff hat, bis die erforderlichen Sicherheitsmaßnahmen ergriffen wurden.

#### Funktionsweise von Network Access Control

NAC-Systeme bestehen in der Regel aus drei Hauptkomponenten:

- Prüfungsmechanismus: Dieser überprüft die Identität und den Sicherheitsstatus eines Geräts, das versucht, auf das Netzwerk zuzugreifen. Dies kann durch verschiedene Methoden geschehen, einschließlich Authentifizierung über Benutzername und Passwort, Zwei-Faktor-Authentifizierung oder Zertifikate.
- Durchsetzungsmechanismus: Nach der Überprüfung entscheidet der Durchsetzungsmechanismus, ob das Gerät auf das Netzwerk zugreifen darf, und wenn ja, auf welche Teile des Netzwerks. Der Zugriff kann basierend auf vordefinierten Sicherheitsrichtlinien gestattet oder verweigert werden.
- Remediation: Falls ein Gerät nicht den Sicherheitsanforderungen entspricht, bietet die NAC-Lösung eine Möglichkeit zur Remediation. Dies kann bedeuten, dass das Gerät in ein isoliertes Netzwerk verschoben wird, wo es aufgerüstet oder repariert werden kann, um die Sicherheitsanforderungen zu erfüllen.

#### Implementierungsmethoden von NAC

NAC kann auf verschiedene Arten implementiert werden, je nach den spezifischen Bedürfnissen und der Infrastruktur einer Organisation. Die gängigsten Implementierungsmethoden umfassen:

- Inline-NAC: Hierbei wird das NAC-System direkt in den Netzwerkpfad integriert, wodurch es den gesamten Verkehr überwachen und bei Bedarf eingreifen kann. Diese Methode bietet eine hohe Sicherheitsstufe, da sie direkten Zugriff auf den gesamten Datenverkehr hat. Allerdings kann sie auch zu Engpässen führen, insbesondere in großen Netzwerken.
- Out-of-Band-NAC: Bei dieser Methode ist das NAC-System nicht direkt in den Netzwerkpfad integriert, sondern arbeitet parallel dazu. Es sammelt Informationen über den Netzwerkverkehr und trifft auf Basis dieser Daten Entscheidungen. Diese Methode ist flexibler und skalierbarer als Inline-NAC, allerdings kann sie auch weniger effektiv sein, da sie nicht den gesamten Verkehr in Echtzeit überwacht.
- Agent-basierte NAC: Diese Implementierung erfordert, dass auf jedem Gerät, das auf das Netzwerk zugreifen möchte, ein Software-Agent installiert wird. Der Agent überwacht den Sicherheitsstatus des Geräts und kommuniziert mit dem NAC-System, um den Zugriff zu ermöglichen oder zu verweigern. Diese Methode bietet detaillierte Kontrolle und ermöglicht es, Sicherheitsrichtlinien auf Geräteebene durchzusetzen.
- Agentenlose NAC: Im Gegensatz zur agentenbasierten Methode benötigt diese Implementierung keine Software-Installation auf den Endgeräten. Stattdessen verwendet sie Methoden wie SNMP, DHCP-Snooping oder 802.1X, um Informationen über die Geräte zu sammeln und Entscheidungen zu treffen. Diese Methode ist einfacher zu implementieren, aber möglicherweise weniger effektiv bei der Durchsetzung von Sicherheitsrichtlinien.

####  Herausforderungen bei der Implementierung von NAC

Obwohl NAC eine leistungsstarke Technologie ist, gibt es verschiedene Herausforderungen bei der Implementierung, die berücksichtigt werden müssen:

- Komplexität: Die Implementierung eines NAC-Systems kann sehr komplex sein, insbesondere in großen und heterogenen Netzwerken. Es erfordert eine sorgfältige Planung und Konfiguration, um sicherzustellen, dass alle Geräte und Benutzer nahtlos integriert werden können.
- Kompatibilität: In vielen Organisationen gibt es eine Vielzahl von Geräten und Betriebssystemen, die alle unterschiedlich auf NAC-Richtlinien reagieren können. Es ist wichtig, sicherzustellen, dass das NAC-System mit allen diesen Geräten kompatibel ist.
- Benutzerfreundlichkeit: NAC kann den Zugang zum Netzwerk für legitime Benutzer erschweren, insbesondere wenn die Sicherheitsrichtlinien zu strikt sind. Es ist wichtig, ein Gleichgewicht zwischen Sicherheit und Benutzerfreundlichkeit zu finden.
- Wartung: NAC-Systeme erfordern regelmäßige Wartung und Aktualisierungen, um mit den sich ständig ändernden Sicherheitsbedrohungen und Netzwerkumgebungen Schritt zu halten.

####  Der MAC-Filter als Teil der NAC

Eine der spezifischen Methoden zur Steuerung des Zugriffs auf Netzwerke im Rahmen von NAC ist der Einsatz von MAC-Filtern. Die MAC-Adresse (Media Access Control) ist eine eindeutige Kennung, die jedem Netzwerkgerät zugewiesen wird. Durch die Verwendung von MAC-Filtern kann ein Netzwerkadministrator festlegen, welche Geräte basierend auf ihrer MAC-Adresse auf das Netzwerk zugreifen dürfen.

##### Funktionsweise von MAC-Filtern

Ein MAC-Filter funktioniert, indem er eine Liste von erlaubten (oder in einigen Fällen verbotenen) MAC-Adressen erstellt. Wenn ein Gerät versucht, auf das Netzwerk zuzugreifen, überprüft der Netzwerkzugangspunkt (z. B. ein Router oder ein Switch) die MAC-Adresse des Geräts gegen diese Liste. Wenn die MAC-Adresse auf der Liste der erlaubten Adressen steht, wird der Zugriff gestattet; andernfalls wird er verweigert.

##### Vorteile des MAC-Filters

- Einfache Implementierung: MAC-Filter sind relativ einfach zu implementieren und erfordern keine komplexe Konfiguration oder zusätzliche Software auf den Endgeräten.
- Sicherheitsschicht: Obwohl MAC-Adressen gefälscht werden können, bieten MAC-Filter dennoch eine zusätzliche Sicherheitsschicht, die es einem Angreifer erschwert, unbemerkt auf das Netzwerk zuzugreifen.
- Geeignet für kleine Netzwerke: In kleinen Netzwerken, in denen die Anzahl der Geräte überschaubar ist, können MAC-Filter eine effektive Methode zur Zugangskontrolle sein.

#####  Nachteile und Einschränkungen des MAC-Filters

- Leicht zu umgehen: MAC-Adressen können relativ einfach gefälscht werden (Spoofing), wodurch ein Angreifer in der Lage sein könnte, den MAC-Filter zu umgehen.
- Skalierbarkeit: In großen Netzwerken mit vielen Geräten kann die Verwaltung von MAC-Filtern sehr aufwendig werden, da jede MAC-Adresse manuell hinzugefügt oder entfernt werden muss.
- Keine Authentifizierung: MAC-Filter bieten keine Möglichkeit zur Benutzer- oder Geräteauthentifizierung. Sie basieren ausschließlich auf der MAC-Adresse, was bedeutet, dass sie keine weiteren Informationen über das Gerät oder den Benutzer erhalten.

#####  Einsatzbereiche von MAC-Filtern

MAC-Filter werden häufig in kleineren Netzwerken eingesetzt, wo die Verwaltung überschaubar ist und wo sie als erste Verteidigungslinie dienen können. Sie sind oft in drahtlosen Netzwerken zu finden, wo sie als einfache Methode zur Verhinderung von unbefugtem Zugriff eingesetzt werden.

In größeren Netzwerken oder in Umgebungen mit hohen Sicherheitsanforderungen werden MAC-Filter in der Regel als eine von mehreren Sicherheitsschichten eingesetzt, kombiniert mit anderen NAC-Technologien wie 802.1X-Authentifizierung, um eine umfassendere Sicherheitslösung zu bieten.

##### Weitere NAC-Technologien und ihre Beziehung zu MAC-Filtern

Neben MAC-Filtern gibt es eine Vielzahl anderer Technologien, die im Rahmen von NAC eingesetzt werden können, um den Netzwerkzugang zu kontrollieren. Zu den wichtigsten gehören:

- 802.1X-Authentifizierung: Diese Methode basiert auf dem IEEE 802.1X-Standard und verwendet Port-basierte Zugangskontrolle, um den Zugriff auf das Netzwerk nur für authentifizierte Benutzer und Geräte zu erlauben. 802.1X arbeitet oft in Kombination mit einem RADIUS-Server, um eine zentrale Authentifizierungsstelle bereitzustellen.
- Captive Portals: Captive Portals werden häufig in öffentlichen WLAN-Netzwerken eingesetzt, um Benutzer zur Authentifizierung auf eine spezielle Webseite umzuleiten, bevor sie auf das Netzwerk zugreifen können. Diese Methode wird oft für Gäste oder temporäre Benutzer verwendet.
- VLANs: Virtuelle lokale Netzwerke (VLANs) können in Verbindung mit NAC eingesetzt werden, um den Netzwerkverkehr zu segmentieren und sicherzustellen, dass nur autorisierte Geräte auf bestimmte Teile des Netzwerks zugreifen können.
- Firewalls und Intrusion Prevention Systems (IPS): Diese Technologien können als zusätzliche Sicherheitsmaßnahme eingesetzt werden, um den Netzwerkverkehr zu überwachen und Angriffe zu verhindern.

Die Beziehung zwischen diesen Technologien und MAC-Filtern besteht darin, dass MAC-Filter als grundlegende Zugangskontrollmethode eingesetzt werden können, während die anderen Technologien zusätzliche Sicherheitsstufen bieten. In einem gut durchdachten NAC-Framework arbeiten diese Technologien zusammen, um eine robuste und mehrschichtige Sicherheitsstrategie zu gewährleisten.

#### Zukunftsperspektiven und Entwicklungen im Bereich NAC

Mit der fortschreitenden Digitalisierung und der zunehmenden Verbreitung des Internet of Things (IoT) werden die Anforderungen an NAC-Systeme weiter steigen. Neue Entwicklungen im Bereich der künstlichen Intelligenz und des maschinellen Lernens könnten NAC-Systeme in Zukunft noch effektiver machen, indem sie es ermöglichen, Anomalien im Netzwerkverkehr in Echtzeit zu erkennen und darauf zu reagieren.

Darüber hinaus wird die Integration von NAC in Cloud-Umgebungen eine wichtige Rolle spielen, da immer mehr Unternehmen auf Cloud-Dienste umsteigen. Cloud-basierte NAC-Lösungen könnten flexibler und skalierbarer sein als herkömmliche on-premises Lösungen.

#### Fazit

Network Access Control ist ein wesentliches Element moderner IT-Sicherheit. Es ermöglicht es Organisationen, den Zugang zu ihren Netzwerken streng zu kontrollieren und potenzielle Bedrohungen zu minimieren. MAC-Filter sind eine einfache, aber wirksame Methode, um den Netzwerkzugriff zu steuern, insbesondere in kleineren Netzwerken. In größeren und komplexeren Umgebungen sollten sie jedoch als Teil einer umfassenderen NAC-Strategie eingesetzt werden, die fortschrittlichere Technologien wie 802.1X, VLANs und Firewalls umfasst.

Die Zukunft von NAC wird von der Notwendigkeit bestimmt, mit der rasanten Entwicklung der Netzwerktechnologien Schritt zu halten und gleichzeitig die wachsenden Bedrohungen durch Cyberangriffe abzuwehren. Unternehmen, die in ihre NAC-Systeme investieren und sie kontinuierlich aktualisieren, werden besser in der Lage sein, ihre Netzwerke zu schützen und die Integrität ihrer Daten zu gewährleisten.

## Kompetenz 4.1: MAC-Filter auf Netzwerkports einrichten

Die Analyse der Network Access Control hat verschiedene Ansätze aufgezeigt, die ein Eindringen in das Kundennetzwerk erschweren oder aufdecken sollen. Nach Rücksprache mit dem Kunden soll vorerst auf den MAC-Filter in Bereichen, die unbeobachteten Zugang zu Netzwerkdosen sowie bei Kabeln, die die Gebäudehülle verlassen, zurückgegriffen werden.

### A|3.2: Einrichtung des Switches NetGear GS108Tv3 inkl. MAC-Filter

//TODO

### M|3.6: Konfiguration des NetGear GS108Tv3 Switches

//TODO

### M|3.7: Manual zum NetGear GS108Tv3 Switch

//TODO

{%
   include-markdown "inhalte/lizenzhinweis.md"
   start="<!--include-start-->"
   end="<!--include-end-->"
%}