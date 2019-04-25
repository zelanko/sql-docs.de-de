---
title: Erstellen einer Verbindungszeichenfolge | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/20/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
- connection strings [ADO]
ms.assetid: 14eae122-2d1e-40c8-b88e-b7cb8dfbc93b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 455fe1c3f5a19b498730909f1c56bf98b03ae51b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472646"
---
# <a name="creating-a-connection-string"></a>Erstellen einer Verbindungszeichenfolge
Eine Verbindungszeichenfolge besteht aus einer Liste von Argument-Wert-Paaren (das heißt, Parameter), die durch Semikolons getrennt. Zum Beispiel:  
  
```syntax
"arg1=val1; arg2=val2; ... argN=valN;"  
```  
  
 Alle Parameter müssen vom ADO oder den angegebenen Anbieter erkannt werden.  
  
 ADO erkennt die folgenden fünf Argumente in einer Verbindungszeichenfolge.  
  
|Argument|Description|  
|--------------|-----------------|  
|*Anbieter*|Gibt den Namen eines Anbieters für die Verbindung verwendet.|  
|*Dateiname*|Gibt den Namen einer anbieterspezifischen-Datei (z. B. eine persistente Daten Quellobjekt), die vordefinierten Verbindungsinformationen enthält.|  
|*URL*|Gibt die Verbindungszeichenfolge als eine absolute URL identifiziert eine Ressource, z. B. eine Datei oder ein Verzeichnis an.|  
|*Remote-Anbieter*|Gibt den Namen eines Anbieters verwenden, wenn eine Client-Side-Verbindung öffnen. (Nur Remotedaten-Dienst.)|  
|*Remoteserver*|Gibt den Pfadnamen des Servers, verwenden Sie beim Öffnen einer Client-Side-Verbindung an. (Nur Remotedaten-Dienst.)|  
  
 Andere Argumente übergeben werden, an den Anbieter mit dem Namen in der *Anbieter* Argument ohne jede Verarbeitung von ADO.  
  
 Die Anwendung HelloData im [HelloData: Eine einfache ADO-Anwendung](../../../ado/guide/data/hellodata-a-simple-ado-application.md) verwendet die folgende Verbindungszeichenfolge:  
  
```vb
m_sConnStr = "Provider=SQLOLEDB;Data Source=MySqlServer;" & _  
             "Initial Catalog=Northwind;Integrated Security='SSPI';"  
```  
  
 In dieser Verbindungszeichenfolge ADO erkennt nur die `"Provider=SQLOLEDB"` -Parameter, der Microsoft OLE DB-Anbieter für SQL Server als ADO-Datenquelle angibt. Die restlichen das Argument/Wert-Paare `"Data Source=MySqlServer; Initial Catalog=Northwind;Integrated Security='SSPI';"`, an dieses Anbieters wörtlichen übergeben werden. Den Typ und die Gültigkeit des solche Parameter sind anbieterspezifisch. Informationen zu gültigen Parametern, die in der Verbindungszeichenfolge übergeben werden können, finden Sie in der einzelnen Dokumentation des Anbieters.  
  
 Gemäß der OLE DB-Anbieter für SQL Server-Dokumentation können Sie für die "Server" ersetzen die *Datenquelle* Parameter und "Database" für die *Anfangskatalog* Parameter. Daher würde die folgende Verbindungszeichenfolge identisch mit dem oben aufgeführten Ergebnissen.  
  
```vb
m_sConnStr = "Provider=SQLOLEDB;Server=MySqlServer;" & _  
             "Database=Northwind;Integrated Security='SSPI';"  
```
