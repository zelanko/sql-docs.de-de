---
title: Mssqlctl Hdfs-Referenz
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Hdfs-Befehlen.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9051c3630fce005572bc3b939ebef9ed8d111e07
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394212"
---
# <a name="mssqlctl-hdfs"></a>Mssqlctl hdfs

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Hdfs** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Mssqlctl Hdfs-shell](#mssqlctl-hdfs-shell) | Die HDFS-Shell ist eine einfache interaktive Befehlsshell für HDFS-Dateisystem.
[mssqlctl hdfs ls](#mssqlctl-hdfs-ls) | Listet den Status der angegebenen Datei bzw. des Verzeichnisses.
[Mssqlctl Hdfs vorhanden ist.](#mssqlctl-hdfs-exists) | Bestimmt, ob eine Datei oder ein Verzeichnis vorhanden ist.  Gibt True, wenn vorhanden ist und "false" andernfalls.
[mssqlctl hdfs mkdir](#mssqlctl-hdfs-mkdir) | Erstellen Sie ein Verzeichnis unter dem angegebenen Pfad.
[mssqlctl hdfs mv](#mssqlctl-hdfs-mv) | Verschieben Sie die angegebene Datei oder Pfad zu einem angegebenen Speicherort.
[Mssqlctl Hdfs zu erstellen.](#mssqlctl-hdfs-create) | Erstellen Sie die Textdatei, an der angegebenen Position.  Einfache Textinhalt kann über Data-Parameter hinzugefügt werden.
[Mssqlctl Hdfs lesen](#mssqlctl-hdfs-read) | Lesen von Inhalt einer Datei.  Offset und Länge in Bytes sind optionale Parameter.
[mssqlctl hdfs rm](#mssqlctl-hdfs-rm) | Entfernen Sie eine Datei oder ein Verzeichnis an.
[mssqlctl hdfs rmr](#mssqlctl-hdfs-rmr) | Eine Datei oder ein Verzeichnis rekursiv zu entfernen.
[mssqlctl hdfs chmod](#mssqlctl-hdfs-chmod) | Ändern Sie die Berechtigung für die angegebene Datei oder das Verzeichnis an.
[Mssqlctl Hdfs chown](#mssqlctl-hdfs-chown) | Ändern Sie den Besitzer oder die Gruppe der angegebenen Datei.
## <a name="mssqlctl-hdfs-shell"></a>Mssqlctl Hdfs-shell
Die HDFS-Shell ist eine einfache interaktive Befehlsshell für HDFS-Dateisystem.
```bash
mssqlctl hdfs shell 
```
### <a name="examples"></a>Beispiele
Starten Sie die Shell ein.
```bash
mssqlctl hdfs shell
```
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-hdfs-ls"></a>Mssqlctl Hdfs ls
Listet den Status der angegebenen Datei bzw. des Verzeichnisses.
```bash
mssqlctl hdfs ls --path -p 
                 
```
### <a name="examples"></a>Beispiele
Liste-Status
```bash
mssqlctl hdfs ls --path '/tmp'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Pfad zur Liste Status.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-hdfs-exists"></a>Mssqlctl Hdfs vorhanden ist.
Bestimmt, ob eine Datei oder ein Verzeichnis vorhanden ist.  Gibt True, wenn vorhanden ist und "false" andernfalls.
```bash
mssqlctl hdfs exists --path -p 
                     
```
### <a name="examples"></a>Beispiele
Suchen Sie nach der Datei oder Verzeichnis Existance.
```bash
mssqlctl hdfs exists --path '/tmp'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Pfad zur Prüfung der Existenz.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-hdfs-mkdir"></a>mssqlctl hdfs mkdir
Erstellen Sie ein Verzeichnis unter dem angegebenen Pfad.
```bash
mssqlctl hdfs mkdir --path -p 
                    
```
### <a name="examples"></a>Beispiele
Stellen Sie Verzeichnis.
```bash
mssqlctl hdfs mkdir --path '/tmp'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Name des Verzeichnisses, das erstellen.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-hdfs-mv"></a>Mssqlctl Hdfs mv
Verschieben Sie die angegebene Datei oder Pfad zu einem angegebenen Speicherort.
```bash
mssqlctl hdfs mv --source-path -s 
                 --target-path -t
```
### <a name="examples"></a>Beispiele
Verschieben Sie die Datei oder ein Verzeichnis.
```bash
mssqlctl hdfs mv --source-path '/tmp' --target-path '/dest'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--source-path -s`
Das Verzeichnis verschoben.
#### `--target-path -t`
Der Speicherort, zu verschieben.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-hdfs-create"></a>Mssqlctl Hdfs zu erstellen.
Erstellen Sie die Textdatei, an der angegebenen Position.  Einfache Textinhalt kann über Data-Parameter hinzugefügt werden.
```bash
mssqlctl hdfs create --path -p 
                     --data -d
```
### <a name="examples"></a>Beispiele
Erstellen Sie die Datei.
```bash
mssqlctl hdfs create --path '/tmp/test.txt' --data "This is a test."
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Name des zu erstellenden Datei.
#### `--data -d`
Der Inhalt der Datei.  Vorgesehen für einfachen Text-Inhalt.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-hdfs-read"></a>Mssqlctl Hdfs lesen
Lesen von Inhalt einer Datei.  Offset und Länge in Bytes sind optionale Parameter.
```bash
mssqlctl hdfs read --path -p 
                   --offset  
                   --length -l
```
### <a name="examples"></a>Beispiele
Lesen Sie die Datei.
```bash
mssqlctl hdfs read --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Name des zu lesenden Datei.
#### `--offset`
Anzahl der Bytes, der offset in der Datei zum Lesen.
#### `--length -l`
Die Länge der Daten zu lesen.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-hdfs-rm"></a>mssqlctl hdfs rm
Entfernen Sie eine Datei oder ein Verzeichnis an.
```bash
mssqlctl hdfs rm --path -p 
                 
```
### <a name="examples"></a>Beispiele
Entfernen Sie eine Datei oder ein Verzeichnis an.
```bash
mssqlctl hdfs rm --path '/tmp'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Name der Datei zu entfernen.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-hdfs-rmr"></a>mssqlctl hdfs rmr
Eine Datei oder ein Verzeichnis rekursiv zu entfernen.
```bash
mssqlctl hdfs rmr --path -p 
                  
```
### <a name="examples"></a>Beispiele
Verzeichnis für rekursive entfernen.
```bash
mssqlctl hdfs rmr --path '/tmp'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Name der Datei, die rekursiv zu entfernen.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-hdfs-chmod"></a>Mssqlctl Hdfs chmod
Ändern Sie die Berechtigung für die angegebene Datei oder das Verzeichnis an.
```bash
mssqlctl hdfs chmod --path -p 
                    --permission
```
### <a name="examples"></a>Beispiele
Ändern Sie die Datei oder eines Verzeichnisses-Berechtigung.
```bash
mssqlctl hdfs chmod --permission 775 --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Name der Datei oder des Verzeichnisses zum Festlegen von Berechtigungen auf.
#### `--permission`
Berechtigung Oktette festlegen.  Beispiel: "775".
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-hdfs-chown"></a>Mssqlctl Hdfs chown
Ändern Sie den Besitzer oder die Gruppe der angegebenen Datei.
```bash
mssqlctl hdfs chown --path -p 
                    --owner  
                    --group -g
```
### <a name="examples"></a>Beispiele
Ändern Sie den Besitzer und die Gruppe ein.
```bash
mssqlctl hdfs chown --owner hdfs --group superusergroup --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Name der Datei oder des Verzeichnisses, Besitzer ändern.
#### `--owner`
Der Name des Besitzers festgelegt werden soll.
#### `--group -g`
Der Gruppenname festgelegt werden soll.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).