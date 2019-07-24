---
title: azdata BDC HDFS-Referenz
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu azdata BDC-HDFS-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8e892c2d501902ef915a297440ae5a6ffda83bce
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426180"
---
# <a name="azdata-bdc-hdfs"></a>azdata-BDC-HDFS

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält einen Verweis auf die **BDC-HDFS** -Befehle im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata BDC HDFS-Shell](#azdata-bdc-hdfs-shell) | Die HDFS-Shell ist eine einfache interaktive Befehlsshell für das HDFS-Dateisystem.
[azdata BDC HDFS-ls](#azdata-bdc-hdfs-ls) | Listet den Status der angegebenen Datei bzw. des angegebenen Verzeichnisses auf.
[azdata BDC HDFS vorhanden](#azdata-bdc-hdfs-exists) | Bestimmen Sie, ob eine Datei oder ein Verzeichnis vorhanden ist.  Gibt true zurück, wenn vorhanden, andernfalls false.
[azdata BDC HDFS-mkdir](#azdata-bdc-hdfs-mkdir) | Erstellen Sie ein Verzeichnis unter dem angegebenen Pfad.
[azdata BDC HDFS-MV](#azdata-bdc-hdfs-mv) | Verschiebt die angegebene Datei bzw. den angegebenen Pfad an den angegebenen Speicherort.
[azdata BDC HDFS-Erstellung](#azdata-bdc-hdfs-create) | Erstellen Sie die Textdatei am angegebenen Speicherort.  Einfacher Text Inhalt kann über den Daten Parameter hinzugefügt werden.
[azdata BDC HDFS Cat](#azdata-bdc-hdfs-cat) | Lesen Sie den Inhalt einer Datei.  Offset und Länge in Bytes sind optionale Parameter.
[azdata BDC HDFS RM](#azdata-bdc-hdfs-rm) | Entfernen Sie eine Datei oder ein Verzeichnis.
[azdata BDC HDFS RMR](#azdata-bdc-hdfs-rmr) | Entfernen Sie eine Datei oder ein Verzeichnis rekursiv.
[azdata BDC HDFS chmod](#azdata-bdc-hdfs-chmod) | Ändern Sie die-Berechtigung für die angegebene Datei oder das angegebene Verzeichnis.
[azdata BDC HDFS-Besitzer](#azdata-bdc-hdfs-chown) | Ändern Sie den Besitzer oder die Gruppe der angegebenen Datei.
[azdata BDC-HDFS-einbinden](reference-azdata-bdc-hdfs-mount.md) | Verwalten der Bereitstellung von Remote speichern in HDFS.
## <a name="azdata-bdc-hdfs-shell"></a>azdata BDC HDFS-Shell
Die HDFS-Shell ist eine einfache interaktive Befehlsshell für das HDFS-Dateisystem.
```bash
azdata bdc hdfs shell 
```
### <a name="examples"></a>Beispiele
Starten Sie die Shell.
```bash
azdata bdc hdfs shell
```
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-hdfs-ls"></a>azdata BDC HDFS-ls
Listet den Status der angegebenen Datei bzw. des angegebenen Verzeichnisses auf.
```bash
azdata bdc hdfs ls --path -p 
                   
```
### <a name="examples"></a>Beispiele
Listen Status
```bash
azdata bdc hdfs ls --path '/tmp'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Pfad zum Auflisten des Status.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-hdfs-exists"></a>azdata BDC HDFS vorhanden
Bestimmen Sie, ob eine Datei oder ein Verzeichnis vorhanden ist.  Gibt true zurück, wenn vorhanden, andernfalls false.
```bash
azdata bdc hdfs exists --path -p 
                       
```
### <a name="examples"></a>Beispiele
Prüfen Sie, ob die Datei oder das Verzeichnis vorhanden ist.
```bash
azdata bdc hdfs exists --path '/tmp'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Pfad zum Überprüfen auf das vorhanden sein.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-hdfs-mkdir"></a>azdata BDC HDFS-mkdir
Erstellen Sie ein Verzeichnis unter dem angegebenen Pfad.
```bash
azdata bdc hdfs mkdir --path -p 
                      
```
### <a name="examples"></a>Beispiele
Erstellen Sie das Verzeichnis.
```bash
azdata bdc hdfs mkdir --path '/tmp'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Name des zu erstellenden Verzeichnisses.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-hdfs-mv"></a>azdata BDC HDFS-MV
Verschiebt die angegebene Datei bzw. den angegebenen Pfad an den angegebenen Speicherort.
```bash
azdata bdc hdfs mv --source-path -s 
                   --target-path -t
```
### <a name="examples"></a>Beispiele
Verschieben Sie die Datei oder das Verzeichnis.
```bash
azdata bdc hdfs mv --source-path '/tmp' --target-path '/dest'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--source-path -s`
Das Verzeichnis, das verschoben werden soll.
#### `--target-path -t`
Der Speicherort, zu dem gewechselt werden soll.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-hdfs-create"></a>azdata BDC HDFS-Erstellung
Erstellen Sie die Textdatei am angegebenen Speicherort.  Einfacher Text Inhalt kann über den Daten Parameter hinzugefügt werden.
```bash
azdata bdc hdfs create --path -p 
                       --data -d
```
### <a name="examples"></a>Beispiele
Datei erstellen.
```bash
azdata bdc hdfs create --path '/tmp/test.txt' --data "This is a test."
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Name der zu erstellenden Datei.
#### `--data -d`
Inhalt der Datei.  Für einfachen Text Inhalt vorgesehen.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-hdfs-cat"></a>azdata BDC HDFS Cat
Lesen Sie den Inhalt einer Datei.  Offset und Länge in Bytes sind optionale Parameter.
```bash
azdata bdc hdfs cat --path -p 
                    --offset  
                    --length -l
```
### <a name="examples"></a>Beispiele
Datei lesen.
```bash
azdata bdc hdfs cat --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Name der zu lesenden Datei.
#### `--offset`
Anzahl der Bytes in der zu lesenden Datei.
#### `--length -l`
Länge der zu lesenden Daten.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-hdfs-rm"></a>azdata BDC HDFS RM
Entfernen Sie eine Datei oder ein Verzeichnis.
```bash
azdata bdc hdfs rm --path -p 
                   
```
### <a name="examples"></a>Beispiele
Entfernen Sie eine Datei oder ein Verzeichnis.
```bash
azdata bdc hdfs rm --path '/tmp'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Name der zu entfernenden Datei.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-hdfs-rmr"></a>azdata BDC HDFS RMR
Entfernen Sie eine Datei oder ein Verzeichnis rekursiv.
```bash
azdata bdc hdfs rmr --path -p 
                    
```
### <a name="examples"></a>Beispiele
Rekursives Entfernungs Verzeichnis.
```bash
azdata bdc hdfs rmr --path '/tmp'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Name der Datei, die rekursiv entfernt werden soll.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-hdfs-chmod"></a>azdata BDC HDFS chmod
Ändern Sie die-Berechtigung für die angegebene Datei oder das angegebene Verzeichnis.
```bash
azdata bdc hdfs chmod --path -p 
                      --permission
```
### <a name="examples"></a>Beispiele
Ändern Sie die Datei-oder Verzeichnis Berechtigung.
```bash
azdata bdc hdfs chmod --permission 775 --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Name der Datei oder des Verzeichnisses, für die Berechtigungen festgelegt werden sollen.
#### `--permission`
Berechtigungs-Oktette festlegen.  Beispiel: "775".
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-hdfs-chown"></a>azdata BDC HDFS-Besitzer
Ändern Sie den Besitzer oder die Gruppe der angegebenen Datei.
```bash
azdata bdc hdfs chown --path -p 
                      --owner  
                      --group -g
```
### <a name="examples"></a>Beispiele
Ändern Sie den Besitzer und die Gruppe.
```bash
azdata bdc hdfs chown --owner hdfs --group superusergroup --path '/tmp/test.txt'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Der Name der Datei oder des Verzeichnisses, für die der Besitzer geändert werden soll.
#### `--owner`
Der Name des Besitzers, auf den festgelegt werden soll.
#### `--group -g`
Der Gruppenname, der auf festgelegt wird.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md). Weitere Informationen zum Installieren des Tools **azdata** finden [Sie unter Install azdata to Manage SQL Server 2019 Big Data Clusters](deploy-install-azdata.md).
