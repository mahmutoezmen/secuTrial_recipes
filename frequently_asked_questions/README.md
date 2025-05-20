# secuTrial Frequently Asked Questions

# Overview

The following topics are covered by this documentation:

- [Formular ist im DataCapture nicht zu sehen](#formulardatacapture)
- [Unvollständige Datumsangaben importieren](#unvollstaendigedatumsangabenimport)
- [Problem beim Import von Wiederholgruppen](#problemimportwiederholgruppen)
- [SAS Export-Datei nicht in SAS einlesbar](#sasexportdateinichtinsaseinlesbar)
- [Daten über einen Formularidentifikator importieren](#datenuebereinenformularidentifikatorimportieren)
- [Formular kann nicht gespeichert werden](#formularkannnichtgespeichertwerden)
- [Patientenselbsteingabe (PSD) funktioniert nicht](#psdfunktioniertnicht)
- [Session Time-Out](#sessiontimeout)
- [Projekt kann nicht freigegeben werden](#projektkannnichtfreigegebenwerden)
- [Zeitdifferenz berechnen und für weitere Score-berechnung nutzen](#zeitdifferenzberechnenundfürweiterescoreberechnungnutzen)
  
<a name="formulardatacapture" />

# Formular ist im DataCapture nicht zu sehen

Sie haben im FormBuilder ein neues Formular implementiert und um es im DataCapture sichtbar zu machen, muss Folgendes erledigt werden: im FormBuilder muss das Formular im Visitenplan mindestens einer Visite zugeordnet werden. Zusätzlich muss im AdminTool dass Formular für die jeweilige Rolle freigegeben werden.

<a name="unvollständigedatumsangabenimport" />

# Unvollständige Datumsangaben importieren

In secuTrial sind auch unvollständige Datumsangaben möglich, wenn als Itemtyp z.B. Datum (tt.mm.jjj) gewählt wurde. Um Datensätze mit Datumsangaben, bei denen nur das Jahr (z.B. 2007) oder nur Monat und Jahr (z.B. 03.2007) bekannt sind, importieren zu können, müssen die entsprechenden fehlenden Stellen durch Blanks bzw. Punkte aufgefüllt werden. Statt '2007' muss im entsprechenden Feld' . .2007' bzw. statt '03.2007' muss' .03.2007' stehen. Es können auch Datumsangaben wie '1.7.2007' importiert werden, diese werden dann als '01.07.2007' in der Datenbank gespeichert.


<a name="problemimportwiederholgruppen" />

# Problem beim Import von Wiederholgruppen

Wenn Daten in eine Wiederholgruppe importiert werden sollen, kann dies auch spaltenweise erfolgen. Dann muss in der Import-Konfiguration eine Kennung der externen Variablen angegeben werden, z.B. _<Nr>. Im Datensatz sind dann die Spalten entsprechend gekennzeichnet, z.B. Datum_1, Datum 2, Datum_3,..... Dann darf diese Kennung aber bei keiner der anderen Variablen vorkommen, die nicht zu einer Wiederholgruppe gehören, z.B. var_1,var_2, var_3,... Die Namen der externen Variablen sollten im Mapping in der Import-Konfiguration umbenannt werden, z.B. in var1,var2,var3,....

<a name="sasexportdateinichtinsaseinlesbar" />

# SAS Export-Datei nicht in SAS einlesbar

Beim Export von Daten aus secuTrial nach SAS kann es insbesondere beim Export einer Rechteckdatei passieren, dass das Einleseskript für SAS mit Fehlern gestoppt wird. Das liegt meistens daran, dass es Variablennamen gibt, die länger als 32 Zeichen sind, was von SAS nicht toleriert wird. Diese langen Variablennamen werden dadurch erzeugt, dass bei einer Rechteckdatei die Kennung der Visite und eventuelle Kennungen für eine Wiederholgruppe dem ursprünglichen Variablennamen vorangestellt werden. Daher sollte man darauf achten - wenn ein SAS-Export als Recheckdatei geplant ist - die Variablennamen in secuTrial nicht zu lang zu wählen. Alternativ muss das Einleseskript für SAS händisch geändert und die entsprechenden Variablennamen gekürzt werden.

<a name="datenuebereinenformularidentifikatorimportieren" />

# Daten über einen Formularidentifikator importieren

Wenn beispielsweise Labordaten importiert werden sollen, die über eine Labor-Id verfügen und nicht die Pat-Id aus secuTrial verwenden, dann kann dazu der Formular-Identifikator im Import-Format des Formulars angegeben werden. Dazu muss die Labor-ID im Textformat im selben Formular wie die Labordaten implementiert und erhoben werden. Im Import-Format kann dann statt bei Datensatzidentifikator statt "über Patienten-Variable" die Option "über Formularfeld" gewählt und die entsprechende externe und interne Variable (die Labor-ID) angegeben werden. Die Labor-ID muss eindeutig sein, sonst funktioniert der Import der Daten nicht.

<a name="formularkannnichtgespeichertwerden" />

# Formular kann nicht gespeichert werden

Es liegt eine Warnung oder ein Fehler vor, da die Dateneingabebedingungen nicht erfüllt sind. Im Formularkopf erscheint eine entsprechende Meldung.
1) Warnung: "Formular kann nicht gespeichert werden. Bitte bestätigen Sie Ihre Eingabe durch erneutes Speichern."
Das entsprechende Datenfeld ist hervorgehoben. Bitte prüfen Sie die Einfabe und korrigieren Sie gegebenfalls. Ist die Eingabe bereits fehlerfrei, speichern Sie das Formular erneut ab.
Warnungen werden bei möglichen fehlerhaften Angaben ausgelöst, beispielsweise wenn das Probandenalter überschritten ist.
2) Fehler: "Formular kann nicht gespeichert werden. Bitte korrigieren Sie die Einträge."
Das fehlerhafte Datenfeld ist rot hervorgehoben. Bitte korrigieren Sie die Eingabe und Speichen Sie das Formular erneut.
Beispiel für ein Fehler: Das Geburtsdatum liegt nach dem Aufnahmedatum.


<a name="psdfunktioniertnicht" />

# Patientenselbsteingabe (PSD) funktioniert nicht

1) Bitte überprüfen Sie, ob im FormBuilder die Patientenselbsteingabe (PSD) aktiviert ist.
2) Bitte überprüfen Sie, ob dem Probanden eine Probandenrolle mit entsprechenden Rechten (Formular anzeigen, lesen, bearbeiten) zugeordnet ist und ob die Formulare der Rolle zugeordnet sind.
3) Bitte prüfen Sie die Gültigkeit des Tokens.

<a name="sessiontimeout" />

# Session Time-Out

Bei längerer Inaktivität im DataCapture in secuTrial werden Sie automatisch
ausgeloggt. Das Session-Timout beträgt regulär 20min. Wünschen Sie aus
bestimmten Gründen eine Verlängerung des Session-Timouts, dann melden Sie sich bitte in der MIT.

<a name="projektkannnichtfreigegebenwerden" />

# Projekt kann nicht freigegeben werden

Der Button "Projekt freigeben" wird im FormBuilder nicht angezeigt, obwohl das Recht dazu in der entsprechenden Rolle angegeben ist. Das kann daran liegen, dass im Visitenplan keine Visite angegeben wurde. Es muss mindestens eine Visite angelegt sein, dann kann das projekt freigeschaltet werden.

<a name="zeitdifferenzberechnenundfürweiterescoreberechnungnutzen" />

# Zeitdifferenz berechnen und für weitere Score-berechnung nutzen

Wenn eine Zeitdifferenz berechnet und dann für weitere Scores numerisch zur Verfügung stehen soll, darf bei der Implementation als Typ nicht "Datumsintervall" bzw. "Zeitintervall" gewählt werden, sondern es muss der Typ "Jahre J (nur berechnet)" bzw. eine der anderen Zeiteinheiten ausgewählt werden. Hierbei wird dann eine numerische Variable erstellt, die dann für weitere Score-Berechnungen genutzt werden kann.
Der Button "Projekt freigeben" wird im FormBuilder nicht angezeigt, obwohl das Recht dazu in der entsprechenden Rolle angegeben ist. Das kann daran liegen, dass im Visitenplan keine Visite angegeben wurde. Es muss mindestens eine Visite angelegt sein, dann kann das projekt freigeschaltet werden.

This recipe was tested under secuTrial version 5.5.1.10

