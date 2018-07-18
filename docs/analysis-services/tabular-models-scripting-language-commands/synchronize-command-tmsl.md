---
title: Synchronize-Befehl (TMSL) | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4265e6fa1e2214fae53cacdb084e152005eb3647
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033273"
---
# <a name="synchronize-command-tmsl"></a>Synchronize-Befehl (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Synchronisiert eine Analysis Services-Datenbank mit einer anderen vorhandenen Datenbank.  
  
## <a name="request"></a>Anforderung  
 Die Eigenschaften, die von der JSON-Code akzeptiert synchronize-Befehl lauten wie folgt.  
  
```  
{   
   "synchronize":{   
      "database":"AdventureWorksDW_Production",  
      "source":"Provider=MSOLAP.7;Data Source=localhost;Integrated Security=SSPI;Initial Catalog=AdventureWorksDW_Dev",  
      "synchronizeSecurity":"copyAll",  
      "applyCompression":true  
   }  
}  
```  
  
 Die Eigenschaften, die von der JSON-Code akzeptiert synchronize-Befehl lauten wie folgt.  
  
||||  
|-|-|-|  
|**Eigenschaft**|**Default**|**Beschreibung**|  
|Datenbank||Der Name des Datenbankobjekts synchronisiert werden.|  
|Quelle||Die Verbindungszeichenfolge für die Verbindung mit dem Quellserver verwendet werden soll.|  
|synchronizeSecurity|skipMembership|Ein Enumerationswert, der angibt, wie sicherheitsdefinitionen wie Rollen und Berechtigungen wiederhergestellt. Gültige Werte enthält, SkipMembership, CopyAll, IgnoreSecurity.|  
|applyCompression|Wahr|Ein boolescher Wert, die bei "true", gibt an, dass die Komprimierung während der Synchronisierungsvorgang angewendet wird. andernfalls "false".|  
  
## <a name="response"></a>Antwort  
 Gibt ein leeres Ergebnis zurück, wenn der Befehl erfolgreich abgeschlossen wurde. Andernfalls wird eine XMLA-Ausnahme zurückgegeben.  
  
## <a name="usage-endpoints"></a>Nutzung (Endpunkte)  
 Dieses Befehlselement wird in einer Anweisung verwendet die [Execute-Methode &#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) Aufruf über einen XMLA-Endpunkt verfügbar gemacht werden, es gibt folgende Möglichkeiten:  
  
-   Als ein XMLA-Fenster in SQL Server Management Studio (SSMS)  
  
-   Als Eingabedatei für die **invoke-Ascmd** PowerShell-Cmdlet  
  
-   Als Eingabe für ein SSIS-Tasks oder SQL Server-Agent-Auftrag  
  
 Sie können eine vorgefertigte Skripts für diesen Befehl aus SSMS generieren, durch Klicken auf die Schaltfläche "Skript" im Dialogfeld Datenbank synchronisieren.  
  
 Die [ \[MS-SSAS-T\]: SQL Server Analysis Services tabellarisch (SQL Server-Technische Protokoll)](http://go.microsoft.com/fwlink/p/?LinkId=784855) Dokument enthält Abschnitt 3.1.5.2.2, in dem die Struktur der JSON-tabellarischen Metadaten-Befehle und die Objekte beschrieben. Derzeit werden diesem Dokument behandelt, Befehle und Funktionen, die im TMSL-Skript ist noch nicht implementiert. Lesen Sie das Thema [Tabular Model Scripting Language &#40;TMSL&#41; Verweis](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) um Informationen zu unterstützten  
  
## <a name="see-also"></a>Siehe auch  
 [Tabular Model Scripting Language &#40;TMSL&#41; – Referenz](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
