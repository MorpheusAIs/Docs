# Vorschlag für einen Morpheus-Schutzfonds

## Einführung
Das Morpheus-Weißbuch sieht 4 % aller MOR-Emissionen für einen "Schutzfonds" vor und überträgt den Anbietern von Kodizes die Aufgabe, als Orakel zu fungieren, falls die Mittel benötigt werden.
Art der Maßnahmen:
- Zahlung von Bug Bounty zur Vermeidung von Angriffen.
- Zahlung von Audits, bevor neue Smart Contracts eingesetzt werden.
- Anhalten der Smart Contracts im Falle eines laufenden Angriffs.
- Signalisierung und Mechansim für die Auszahlung nach einem Angriff.
- Plan im Falle eines signifikanten Verlustes (Hard Fork Szenario)

## Vordefinierte Fälle, die geringfügige Auszahlungen auslösen
Bevor die Smart Contracts im Ethereum-Netzwerk live gehen, werden hier die Bedingungen definiert, unter denen der Schutzfonds MOR oder stETH auszahlt.

## Arten von Zahlungen:
1. Fehler, die entdeckt und den Entwicklern eines Morpheus Capital-, Code-, Berechnungs-, Gemeinschafts- oder Schutzfonds-Smart Contracts verantwortungsvoll mitgeteilt werden.
2. Zahlung von Audits, bevor neue Smart Contracts im Morpheus-Netzwerk eingesetzt werden.
3. Nutzerverluste von MOR oder stETH im Falle eines ausgenutzten Morpheus Smart Contracts.
4. Entschädigung von Anbietern, die keine MOR-Emissionen erhalten haben, im Falle eines Ausfalls des Morpheus-Smart-Contracts.

Die Höhe der Zahlungen aus dem Schutzfonds sollte im Verhältnis zu dem Fehler, dem Verlust oder der Emission stehen.

## Haltebedingungen für Smart Contracts
Bevor Zahlungen für Schäden in Betracht gezogen werden können, sollten Bedingungen festgelegt werden, die im Falle eines laufenden Angriffs einen Stopp der Smart Contracts auslösen.

## Signalisierung und Mechanismus der Auszahlung
Code-Anbieter werden sich an der Signalisierung beteiligen, wenn eine Zahlung ausgelöst werden soll. Zunächst wird ein Vorfall detailliert beschrieben und auf dem GitHub-Repository des betroffenen Smart Contracts veröffentlicht. Dazu gehört eine Liste der betroffenen Adressen und Beträge von MOR und/oder stETH.

Wenn eine Mehrheit der Anbieter von Codes (gemessen am Gewicht der von ihnen gehaltenen MOR-Tokens), die an der Signalisierungsperiode (nicht länger als 7 Tage) teilnehmen, den Bericht als WAHR bestätigt, wird eine Zahlung ausgelöst.

Sobald eine Zahlung ausgelöst wird, benachrichtigt das Programm die Entwickler, um eine Zahlung an die betroffenen Adressen in der angegebenen Höhe zu genehmigen.

## Plan für den Fall eines bedeutenden Schadensereignisses
Ein signifikantes Verlustereignis ist definiert als ein Ereignis, bei dem die MOR-Verluste die Gesamtressourcen des Schutzfonds übersteigen. In diesem Fall sollten die Anbieter von Code statt einer Auszahlung von MOR neue Smart Contracts einführen und die betroffenen MOR-Salden manuell korrigieren. Dies würde zu einem Hard Fork der Code-/MOR-Salden führen und alle Anbieter, Token-Hodler und andere Infrastrukturanbieter müssten ihren Code auf die neuen Smart Contracts aktualisieren.

Im Falle von StETH, das bei einem bedeutenden Schadensereignis verloren geht, zahlt der Schutzfonds so weit wie möglich anteilig zur Höhe der Verluste jeder Person aus.

## Schlussfolgerung
Bugs und Fehler in Programmen sind eine Realität und kennzeichnen die Geschichte von den beiden unbeabsichtigten Hard Forks von Bitcoin bis hin zu The DAO in den frühen Tagen von Ethereum. 

Daher ist es klug, verschiedene Szenarien und Fälle vorauszuplanen und zu wissen, wie damit umzugehen ist, um sich vor Risiken zu schützen und diese zu mindern. Glücklicherweise dürften die für den Schutz der Nutzer bereitgestellten Mittel mit der Zeit größer werden, da mit dem Schutzfonds im Voraus Mittel zurückgelegt wurden und ein Teil des Schutzfonds auch LP-Belohnungen in der AMM einbringt.
