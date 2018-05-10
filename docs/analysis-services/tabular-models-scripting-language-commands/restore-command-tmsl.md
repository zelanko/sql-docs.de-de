---
title: RESTORE-Befehl (TMSL) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7ea9b29d5bf09b3aeb7584f77af8d6e3f8a684fe
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2018
---
# <a name="restore-command-tmsl"></a>RESTORE-Befehl (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Stellt eine Analysis Services-Datenbank aus einer Sicherungsdatei wieder her.  
  
## <a name="request"></a>Anforderung  
  
```  
    {  
"restore": {  
            "description": "Parameters of Restore command of Analysis Services JSON API",  
            "properties": {  
            "database": {  
                "type": "string"  
            },  
            "file": {  
                "type": "string"  
            },  
            "password": {  
                "type": "string"  
            },  
            "dbStorageLocation": {  
                "type": "string"  
            },  
            "allowOverwrite": {  
                "type":boolean  
            },  
            "readWriteMode": {  
                "enum": [  
                "readWrite",  
                "readOnly",  
                "readOnlyExclusive"  
                ]  
. . .   
```  
  
 **Wiederherstellen** verfügt über mehrere Eigenschaften.  
  
||||  
|-|-|-|  
|**Eigenschaft**|**Standardwert**|**Beschreibung**|  
|database|[Erforderlich]|Der Name des Datenbankobjekts wiederhergestellt werden.|  
|file|[Erforderlich]|Die Sicherungsdatei/Pfad.|  
|Kennwort|Empty|Das Kennwort zum Entschlüsseln der Sicherungsdatei verwendet werden soll.|  
|allowOverwrite|False|Ein boolescher Wert, der bei "true", gibt an, dass eine Sicherungsdatei, die bereits vorhanden ist, werden überschrieben; andernfalls "false".|  
|readWriteMode|ReadWrite|Ein Enumerationswert, der Zugriffsmodi darf die Datenbank angibt.<br /><br /> **Enumerationswerte werden wie folgt aus:**<br /><br /> ReadWrite – ist Lese-/ Schreib-Zugriff zulässig.<br /><br /> ReadOnly – ist nur-Lese-Zugriff zulässig.<br /><br /> ReadOnlyExclusive – ist nur-Lese exklusiver Zugriff zulässig.|  
|dbStorageLocation|Empty|Speicherort für die wiederhergestellte Datenbank.|  
  
## <a name="response"></a>Antwort  
 Gibt ein leeres Ergebnis zurück, wenn der Befehl erfolgreich abgeschlossen wurde. Andernfalls wird eine XMLA-Ausnahme zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 **Beispiel 1** -Wiederherstellen einer Datenbank aus einem lokalen Ordner.  
  
```  
{   
   "restore": {   
      "database":"AdventureWorksDW2014",  
      "file":"c:\\awdbdwfile.abf",  
      "security":"...",  
      "allowOverwrite":"true",  
      "password":"..",  
      "locations":"d:\\SQL Server Analysis Services\\data\\",  
      "storageLocation":".."  
   }  
}  
```  
  
## <a name="usage-endpoints"></a>Nutzung (Endpunkte)  
 Diese Command-Element wird in einer Anweisung verwendet die [Execute-Methode &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) Aufruf über einen XMLA-Endpunkt verfügbar gemacht werden auf folgende Weise:  
  
-   Als ein XMLA-Fenster in SQL Server Management Studio (SSMS)  
  
-   Als Eingabedatei für die **invoke-Ascmd** PowerShell-Cmdlet  
  
-   Als Eingabe für ein SSIS-Tasks oder SQL Server-Agent-Auftrag  
  
 Sie können ein vorgefertigtes Skript für diesen Befehl aus SSMS generieren, durch Klicken auf die Schaltfläche "Skript" im Dialogfeld "Wiederherstellen".  
  
 Die [ \[MS-SSAS-T\]: SQL Server Analysis Services-Tabellendatenbank (SQL Server Technische Protocol)](http://go.microsoft.com/fwlink/p/?LinkId=784855) Dokuments Abschnitt 3.1.5.2.2, die die Struktur der Befehle für JSON-tabellarischen Metadaten und Objekte beschreibt. Aktuell enthält dieses Dokument Befehle und Funktionen, die noch nicht im TMSL-Skript implementiert. Finden Sie unter [Tabular Model Scripting Language &#40;TMSL&#41; Verweis](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) für Informationen zu den was unterstützt wird  
  
## <a name="see-also"></a>Siehe auch  
 [Tabular Model Scripting Language &#40;TMSL&#41; – Referenz](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Sichern und Wiederherstellen von Analysis Services-Datenbanken](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
